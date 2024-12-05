A segurança do serviço Domain Name System (DNS) é extremamente importante para a segurança geral de uma rede. 

Ele facilita a comunicação de utilizadores e sistemas na rede. 

No entanto, este serviço importante também pode ser alvo de invasores, então a segurança desse serviço é extremamente importante.

O DNS traduz esses nomes em endereços IP correspondentes quando uma URL é inserida num navegador da web, ou quando uma App se conecta a um serviço da web ou deseja resolver um domínio. 

No entanto, se o serviço DNS não for seguro, os invasores podem manipular consultas DNS e redirecionar os utilizadores para sites falsos ou maliciosos. 

Esse tipo de ataque é frequentemente chamado de envenenamento de DNS ou falsificação de DNS e pode ser usado para roubar informações pessoais ou informações confidenciais dos users (senha, cartão de crédito, etc.). 

Além disso, um ataque DDoS (Distributed Denial of Service) no serviço DNS pode causar um colapso completo de uma rede ou serviço da web.

A segurança do serviço DNS garante que a troca de informações na rede permaneça segura e privada. 

Isso não apenas protege as informações pessoais dos users, mas também protege as informações e serviços confidenciais das empresas de invasores. Portanto, a segurança do serviço DNS é vital para a segurança geral de uma rede.

O Windows DNS Server é um serviço DNS fornecido pela Microsoft e é normalmente usado por redes baseadas em Windows. 
Este serviço é amplamente preferido, especialmente em ambientes Windows, pois é fortemente integrado ao serviço Windows Active Directory. 
No entanto, a segurança do Windows DNS Server é um problema crítico devido ao fato de que invasores podem ter como alvo este serviço e comprometer a rede.

Isso destaca que a segurança do Windows DNS Server é parte integrante da segurança geral de uma rede. 

Portanto, estas estratégias e práticas de proteção de serviço devem ser compreendidas e implementadas. 

A avaliação e a melhoria contínua da segurança do Windows DNS Server são necessárias para proteger contra ataques de DNS, garantir o routing adequado do tráfego de rede e manter a segurança geral da rede. 
  

## Restrição de transferência de zona DNS

Transferência de Zona DNS é o processo de copiar todos os registos DNS do servidor DNS primário (master) para os servidores DNS secundários (slave ou backup). 
Este processo é frequentemente usado para backup de DNS e balanceamento de carga.

Os dados DNS são geralmente organizados numa estrutura chamada "zona", que contém todos os registos de um namespace DNS específico (domínio). 
Uma transferência de zona DNS copia todos os dados de uma zona de um servidor para outro. Geralmente acontece quando alterações são feitas no servidor primário e essas alterações precisam de ser enviadas para todos os servidores de backup.



##### As transferências de zona podem ser de dois tipos:

**Transferência de Zona Completa (AXFR)**

Copia todas as informações de uma zona do servidor DNS primário para o servidor DNS de backup. As transferências geralmente ocorrem quando uma zona é criada pela primeira vez ou quando o servidor de backup sofre um reboot.

  
**Transferência de Zona Incremental (IXFR)**

Copia as alterações numa zona do servidor DNS primário para o servidor DNS de backup. Quando uma zona muda, o servidor de backup recebe apenas as alterações, aumentando a eficiência e reduzindo o tráfego de rede.

As transferências de zona geralmente ocorrem automaticamente, mas um administrador de rede pode acioná-las manualmente. A segurança das transferências de zona é importante porque, se um invasor obtiver acesso a uma transferência de zona, ele poderá aprender sobre todos os registos no servidor DNS. Por esse motivo, devemos restringir as transferências de zona para permitir apenas servidores de backup confiáveis.



Para abrir a consola de Gestão de DNS procuramos por "Gestão de Servidores", selecionar o menu "Ferramentas" e clicar em "DNS". Na janela que se abre, clicamos com o botão direito do mouse na zona relevante e clicamos em "Propriedades".

![](../anexos/Pasted%20image%2020241205205512.png)



Na janela que se abre, mudamos para o separador “Zone Transfers” e selecionamos a opção “Allow zone transfers:” e selecionamos a opção “Only to the following servers” para permitir apenas certos endereços IP. Escrevemos a lista de endereços IP a serem permitidos dizendo “Edit”. (Como visto na imagem o endereço IP 172.16.8.1 tem permissão para fazer transferência de zona.)

![](../anexos/Pasted%20image%2020241205205633.png)


Vamos tentar a transferência de Zona DNS pelo servidor com Endereço IP 172.16.8.136

![](../anexos/Pasted%20image%2020241205205719.png)

Quando uma tentativa de transferência de zona é feita de um sistema que não tem permissão de transferência de zona, o resultado será uma mensagem "Falha na transferência", conforme abaixo:

![](../anexos/Pasted%20image%2020241205205825.png)

## Segurança DNS

DNSSEC ou Domain Name System Security Extensions é um conjunto de padrões da Internet  usado para verificar a integridade e autenticidade de consultas e respostas DNS. Simplificando, DNSSEC ajuda a verificar se os resultados de uma consulta DNS não foram manipulados ou alterados.

O DNSSEC realmente determina se uma resposta DNS é genuína e foi modificada. Basicamente assina digitalmente as respostas DNS e com essa assinatura digital na resposta a cada consulta DNS.

Para definir o DNSSEC:

Abrir a consola de gestão de DNS, procuramos por  "Gestão de Servidores", depois selecionamos o menu "Ferramentas" e clicamos na opção "DNS". Clicamos com o botão direito do mouse na zona que aplicaremos e clicamos em “DNSSEC” -> “Assinar a Zona”.

![](../anexos/Pasted%20image%2020241205210103.png)

Uma assinatura especial etc. se não for usada, selecionamos a opção “Usar configurações padrão para assinar a zona” e clicamos no botão “Avançar”.

![](../anexos/Pasted%20image%2020241205210132.png)

As configurações de DNSSec definidas como padrão são mostradas brevemente. Podemos concluir a configuração de DNSSec clicando em “Next” e depois em “Finish”.

O DNSSEC tem prós e contras. Por exemplo, o DNSSEC pode ser complexo de implementar e gerir e usar mais recursos do sistema. Portanto, uma implementação do DNSSEC deve ser cuidadosamente planeada e gerida.

## Auditoria do Servidor DNS

Auditar a atividade do servidor DNS pode ajudar a identificar uma série de ameaças e ataques. Estas atividades estão localizadas: Microsoft -> Windows -> DNSServer\Audit no Windows Eventlog. 

![](../anexos/Pasted%20image%2020241205210306.png)

As atividades do servidor DNS devem ser monitorizadas constantemente, o que evitará o “ **sequestro de DNS** ”  detetando-os precocemente. O sequestro de DNS é um tipo de ataque feito direcionando consultas DNS para diferentes servidores DNS e alterando a resposta conforme desejado. Isso pode ser feito alterando os registos DNS no servidor DNS.

