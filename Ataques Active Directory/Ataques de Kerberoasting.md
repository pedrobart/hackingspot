O Kerberoasting permite que um invasor solicite um ticket de serviço para qualquer serviço com um SPN registado e então usa esse ticket para quebrar a senha do serviço. 

Se o serviço tiver um SPN registado, então, ele pode ser Kerberoastable se a sua senha não for forte, se for rastreável, bem como os privilégios da conta de serviço quebrada. O que torna esse um ataque comum é que para executar esse ataque, o invasor não precisa ser administrador. Isso pode ser feito com privilégios de apenas um user de domínio.

Muitas vezes, em ambientes reais do Active Directory, contas de serviço recebem privilégios e permissões que nem precisam.
Os administradores de sistema concedem privilégios de administrador de domínio a contas de serviço na maioria das vezes. 

É por isso que os invasores realizam esses ataques na esperança de aumentar privilégios ou até mesmo ter privilégios de administrador de domínio. 

Se um invasor obtiver privilégios de administrador de domínio, ele poderá fazer o que quiser em todo o ambiente do Active Directory, não apenas numa única máquina.


## Ataque 

Vamos supor que o invasor tenha acabado de se estabelecer na rede interna. Os invasores não sabem que tipo de contas de serviço estão presentes no ambiente. Há um Framework chamado “ **PowerSploit** ” que contém diferentes tipos de scripts do PowerShell para enumeração e exploração interna. Um dos scripts é chamado “ **Powerview.ps1** ”, que é um ótimo script para enumeração interna no ambiente do Active Directory.


O invasor primeiro importou os módulos do Powerview. 
**Comando:** “. \PowerView.ps1”

Então o invasor usou um módulo cmdlet do script e o nome do cmdlet é "Get-NetUser". 
**Comando:** Get-NetUser -SPN

O invasor forneceu uma troca de SPN que enumerará todas as contas que têm um nome principal de serviço. 99% das vezes, os SPNs são definidos apenas para contas de serviço. 

Agora o invasor sabe um nome ServiceAccount. Para esse ataque, podemos usar scripts Impacket novamente para executar o ataque e isso requer um conjunto de credenciais válidas. Vamos supor que o invasor não saiba nenhuma credencial válida e tenha obtido acesso por meio de um e-mail de phishing.

Usaremos a ferramenta rubeus, que é muito fácil de usar e despejará hashes de contas de serviço que são kerberoastable.
**Comando:** .\Rubeus.exe kerberoast
Então o invasor pode copiar esse hash e quebrá-lo offline.

## Detectar 

Agora vamos discutir como podemos detectar atividade de kerberoasting. Mais uma vez, detectar isso é difícil, pois os serviços são acedidos ​​e usados ​​em usos diários. Por exemplo, se um user aceder uma partilha de arquivo, um ticket de serviço seria solicitado por esse user do controlador de domínio para aceder o serviço. Como há milhares e milhares de eventos ocorrendo ao mesmo tempo, detetar esse ataque fica cada vez mais difícil.

![[Pasted image 20241124013828.png]]
Podemos ver um TGT a ser solicitado com um tipo de criptografia de “0x17”, assim como vimos na lição anterior de AS-REP roasting. 
O evento principal ocorre imediatamente após este evento com ID de evento “4769”. Novamente, há milhares de eventos registrados com esta ID de evento diariamente, mas procuraremos um campo que indique kerberoasting.

![[Pasted image 20241124013905.png]]

Em casos de uso legítimos deste ID de evento, o tipo de criptografia seria 0x12 ou 0x11. Mas, se virmos um tipo de criptografia "0x17", isso seria um chamado para uma investigação mais aprofundada. Para reduzir ainda mais as chances de falsos positivos, podemos filtrar solicitações de outras contas de serviço. As contas de serviço trabalham solicitando tickets de serviço dos controladores de domínio regularmente. Para reduzir ainda mais os eventos a serem analisados, podemos filtrar solicitações de nomes de conta começando com "$", pois são contas de computador ou outras contas de serviço que o Windows usa como parte de suas operações. Além disso, os invasores às vezes usam scripts ou ferramentas para executar kerberoasting em mais de uma conta de serviço ao mesmo tempo. Se virmos muitos eventos com EventID 4769 e tipo de criptografia "0x17 '' num pequeno período de tempo, isso seria um sinal de alerta confirmado.

Então, para resumir, pode-se detectar atividades de kerberoasting em logs de eventos:

1- ID do evento 4768 com tipo de criptografia “0x17”.

2- O evento acima é imediatamente seguido pelo ID do evento 4769 também com tipo de criptografia “0x17”.

3- O nome da conta que solicita o ticket de serviço é uma conta de user de domínio e não uma conta de serviço ou conta de computador (começando com $).

4- Filtrar por palavras-chave de sucesso de auditoria no evento 4769 (significa que o invasor obteve o hash).

5- Em alguns casos, muitas solicitações de tickets de serviço num curto espaço de tempo.

## Etapas de mitigação 

1- As contas de serviço devem ter senhas complexas e longas.

2- Permissões apropriadas nas contas de serviço (para que, se o invasor tiver acesso a elas, não possa causar muito dano com elas).

