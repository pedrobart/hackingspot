O AS-REP Roasting despeja os hashes Kerberos de contas de users que têm a pré-autenticação Kerberos desabilitada.

O único requisito para o AS-REP roast um user é que o user deve ter a pré-autenticação desabilitada. 

A pré-autenticação é a primeira etapa na autenticação Kerberos e é projetada para evitar ataques de adivinhar de senha por força bruta. 

Durante a pré-autenticação, o hash do user será usado para criptografar um registo de data e hora que o controlador de domínio tentará descriptografar para validar que o hash correto está sendo usado e não está a  repetir uma solicitação anterior. 

Após validar o registo de data e hora, o KDC emitirá um TGT para o user. 

Se a pré-autenticação estiver desabilitada, pode-se solicitar quaisquer dados de autenticação para qualquer user e o KDC retornará um TGT criptografado que pode ser quebrado offline porque o KDC salta a etapa de validação de que o user é realmente quem ele diz ser.

É exatamente assim que os invasores usam indevidamente o recurso de pré-autenticação, pois é assim que o Active Directory funciona e é projetado. 

Isso também dificulta a deteção desse ataque, pois ele mistura-se com eventos e atividades legítimos que ocorrem em ambientes do Active Directory. 

No entanto, existem algumas propriedades que se destaca um evento legítimo de um malicioso. 

Então, para resumir, é assim que este ataque ocorre:

1- O invasor faz uma enumeração em contas de users do Active Directory que não exigem pré-autenticação.

2- O invasor solicita o Kerberos Ticket-Granting Ticket (TGT).

3- O Controlador de Domínio do AD responde com o TGT sem exigir a senha da conta como pré-autenticação.

4- O invasor usa uma ferramenta para extrair os hashes de um pacote capturado.

## Ataque 

Da perspectiva de um invasor, o invasor precisaria apenas de um nome de um user de domínio válido e deveria saber o endereço IP do controlador de domínio. 

Os invasores podem criar uma lista de nomes de users e usar um conjunto impacket de scripts python. 

O Impacket é uma coleção de classes Python para trabalhar com protocolos de rede. 

Ele foi feito para propósitos legítimos e é amplamente usado por administradores de sistema, redteamers e adversários. 

Vamos supor que o invasor não saiba nenhum nome de conta válido no domínio. Os invasores podem usar uma ferramenta como “kerbrute” que enumera nomes de users válidos.
**Comando:** ./kerbrute_linux_amd64 userenum -d teste.org --dc 192.168.1.5 users.txt

E  iria ser feito um output com users válidos. Contudo não sabemos se algum desses users tem a pré-autenticação desabilitada ou não. Quando usamos o script "GetNPUsers.py" do impacket e fornecemos a ele uma lista de usuários válidos, ele recuperará o hash do user se ele tiver a pré-autenticação desabilitada.
**Comando:** python3 /usr/share/doc/python3-impacket/examples/GetNPUsers.py teste.org/ -dc-ip 192.168.1.5 -user users.txt -no-pass

Fornecemos o caminho do script python, depois o nome de domínio que é "teste.org'', depois o endereço IP do controlador de domínio que é "192.168.1.5", depois a lista de nomes de users válidos e, em seguida, um switch "-no-pass" que indica que não temos nenhuma credencial válida até o momento. Digamos que se um invasor já tiver um conjunto válido de credenciais de um user de domínio e quiser executar o movimento lateral, ele pode usar essas credenciais e também executar o AS-REP roasting para obter o hash do user e, em seguida, quebrá-lo.

**Comando:** python3 /usr/share/doc/python3-impacket/examples/GetNPUsers.py teste.org/ -dc-ip 192.168.1.5 -user users.txt -no-pass -format john
  
E aqui veriamos os users com a hash exposta, o que significa que a pré-autenticação foi desabilitada para esses users. No final, especificamos um sinalizador de formato para “john”, que torna esse hash quebrável pela ferramenta “John the Ripper”, que é uma ferramenta de quebra de senha.
**Comando:** john --wordlist=pass.txt hash.txt
E veriamos a senha em cleartext.

Este ataque também pode ser realizado por outras ferramentas como “Rubeus” e pode ser executado diretamente de uma máquina comprometida. O ataque é preciso que os invasores precisam apenas de acesso à rede interna, eles nem precisam realizar o ataque de uma máquina comprometida ou necessariamente exigir um conjunto de credenciais.

## Detecção 

Sempre que um user faz logon num domínio ou executa qualquer tipo de autenticação, como aceder um serviço, etc., um evento é registado nos logs de eventos de segurança do Windows com a ID de evento 4768. 
Esse evento é registrado sempre que um ticket de autenticação Kerberos(TGT) é solicitado do KDC, que é o controlador de domínio.

Por exemplo, um user válido logado na sua estação de trabalho, um ID de evento de 4768 é registado junto com alguns outros eventos também. 

Isso torna muito difícil detetar e caçar ataques de AS-REP roasting porque esses tickets são solicitados para operações diárias e são a essência do mecanismo de autenticação Kerberos. 

No entanto, quando ocorre uma operação legítima (como um logon de user na sua estação de trabalho), o ticket tem um tipo de criptografia de “0x12”, o que indica que ele é criptografado usando AES-256. 

Evento legítimo:
**Observação:** todos os eventos do Kerberos são registados no controlador de domínio para todos os users e computadores no ambiente do Active Directory.
![[Pasted image 20241124010047.png]]

O screenshot acima mostra que o tipo de criptografia do ticket é “0x12” e o tipo de pré-autenticação é 2. 
Qualquer coisa diferente de 0 tipo de pré-autenticação significa que o user tem a pré-autenticação habilitada. 

E o ataque que foi mencionado acima:
![[Pasted image 20241124010247.png]]
Aqui, vemos que o tipo de criptografia é “0x17”. Isso significa que o ticket é criptografado usando o algoritmo de criptografia RC4. 

Este é um dos principais indicadores de que esse ataque ocorreu, no entanto, ainda deixa espaço para dúvidas, pois alguns serviços mais antigos no Active Directory ainda exigem tickets criptografados RC4. 

Mas o tipo de pré-autenticação é 0, o que significa que está desabilitado para o user e atende aos requisitos do ataque de roasting AS-REP. 

Isso pode reduzir muito nossos eventos e deve ser definitivamente analisado.

  
  

Um analista SOC vê centenas de alertas.
Então, para reduzir muito o ruído e procurar apenas por indicações de ataque de roasting AS-REP, os analistas devem usar consultas apenas para procurar o ID do Evento 4768 com o tipo de criptografia de ticket de “0x17” e tipo de pré-autenticação “0”. 

Esses eventos devem ser definitivamente mais analisados ​​e investigados.
Então, para procurar por indícios do AS-REP, o analista deve procurar:

1- ID do evento 4768 no controlador de domínio

2- Tipo de criptografia de ticket “0x17”

3- Tipo de pré-autenticação "0"

## Etapas de mitigação 

1- Encontrar qualquer conta no ambiente que tenham desabilitado a pré-autenticação. Isso pode ser feito executando o seguinte comando do controlador de domínio.

**Comando:** ' get-aduser -f * -pr DoesNotRequirePreAuth | onde {$_.DoesNotRequirePreAuth -eq $TRUE} '

2- Aplicar política de senhas complexas e longas no domínio. Isso tornaria difícil ou impossível para o invasor quebrar a senha de um user válido.



![[Pasted image 20241124011551.png]]
![[Pasted image 20241124011604.png]]

TGT requested na conta jonsnow e com pre-auth type:2 o que é um evento legitimo.


![[Pasted image 20241124011701.png]]

![[Pasted image 20241124011712.png]]
Nestes eventos vemos a conta robstark com pre-auth type:0 que não é um evento legitimo e encaixa no ataque de roasting AS-REP.