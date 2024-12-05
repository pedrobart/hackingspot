
**Gestão de identidade centralizado**

O Active Directory gere contas de users e credenciais centralmente. 

Dessa forma, os users podem aceder a vários recursos na rede com uma única identidade. 
A gestão segura de identidade é garantido pela gestão centralizada de contas de utilizadores, implementação de políticas de senha e o facilitismo  de processos de autorização.

  

**Gestão Centralizada de Recursos**

O Active Directory fornece gestão centralizado de recursos na rede. Incluem contas de utilizador, grupos, pastas partilhadas, impressoras, servidores e outros dispositivos de rede. 
A gestão centralizada de recursos facilita a configuração e atualização regulares de recursos e o controlo de direitos de acesso.

  

**Segurança e Controlo de Acesso**

O Active Directory ajuda a impor políticas de segurança na rede. Graças aos mecanismos de autorização e controlo de acesso, os níveis de acesso dos utilizadores a certos recursos são controlados. 
Isso previne acesso não autorizado a dados sensíveis e aumenta a segurança dos dados.

  

**Políticas de Grupo**

Um dos recursos mais importantes do Active Directory são as Políticas de Grupo. 
As Políticas de Grupo são usadas para gerir centralmente as configurações de utilizadores e computadores. 
As políticas incluem configurações de segurança, configurações de desktop, configurações de aplicação e muito mais. 
As Políticas de Grupo fornecem consistência em toda a rede e facilitam a gestão.

  

**Continuidade e recuperação de negócios**

O Active Directory desempenha um papel importante em garantir a continuidade dos negócios das organizações. 
Em caso de perda de dados ou falhas no sistema, é possível restaurar rapidamente os sistemas usando os mecanismos de backup e restauração do Active Directory. 
Isso minimiza a perda de dados e permite que as organizações continuem operacionais sem interrupção.

  

**Conformidade e Auditoria**

 O Active Directory facilita os requisitos de conformidade fornecendo trilhas de auditoria e mecanismos de tracking.

  

**Domínio**

O domínio é usado como a unidade básica de gestão de uma rede.
Contas de utilizador, grupos, contas de computador e outros objetos estão localizados no domínio que fornece autenticação comum e controlo de acesso.

  

**Unidade Organizacional (UO)**

A Unidade Organizacional (OU) é usada para agrupar e gerir objetos dentro do domínio de uma maneira mais organizada. 
OUs são usadas para administração, controlo de acesso e aplicação de Política de Grupo.

  

**Grupos**

Grupos são usados ​​para agrupar logicamente utilizadores ou computadores. Agrupar utilizadores por recursos ou funções semelhantes facilita a gestão de direitos de acesso e permissões.

  

**Objetos**

Elementos básicos no Active Directory. Utilizadores, computadores, impressoras, grupos, OUs e outros objetos formam os blocos de construção do banco de dados no Active Directory.


## Uso de contas padrão

"Contas Padrão" são contas que são pré-criadas pelo sistema operativo ou aplicações e geralmente têm um nome de utilizador e senha exclusivos. 

Estas contas são criadas automaticamente quando o sistema é instalado ou configurado o sistema ou as aplicações. 

Por exemplo, contas de "Administrador" ou "Convidado" criadas pelo sistema operativo Windows enquadram-se nessa categoria. 
No entanto, o uso dessas contas padrão é geralmente perigoso em termos de segurança.

As contas padrão geralmente vêm com configurações básicas de segurança e podem usar senhas usadas com frequência ou políticas de segurança fracas. 
Portanto, usar essas contas pode criar um ponto que os invasores podem aceder facilmente. Os invasores podem saber as configurações de segurança fracas e os nomes das contas padrão. 

Tentativas de infiltração em sistemas e ataques podem ser realizadas visando essas contas. 
Como as contas padrão geralmente podem ser usadas em vários sistemas ou aplicações, pode ser difícil monitorizar e auditar as atividades dessas contas.
Se as contas padrão continuarem a ser usadas, essas contas podem fornecer permissões de acesso contínuas, mesmo que não sejam mais necessárias. Isso aumenta os riscos desnecessários.

Como resultado, em vez de usar contas padrão, é uma abordagem mais segura criar contas especiais e baseadas em necessidades e proteger essas contas com medidas de segurança, conforme necessário. As permissões de acesso de contas padrão devem ser revistas regularmente e as desnecessárias devem ser desativadas ou excluídas.



## Uso de Grupos Autorizados

Outros membros privilegiados do grupo, como Domain Admins e Enterprise Admins, são muito poderosos. 

Eles podem aceder todo o domínio, todos os sistemas, todos os dados, computadores, laptops e recursos semelhantes.

É recomendado que contas de utilizador comuns não estejam nesses grupos autorizados, a única exceção deve ser a conta de administrador de domínio padrão. 
O que os invasores procuram é aceder contas pertencem a administradores de domínio.

A Microsoft recomenda que seja adicionado temporariamente a conta ao grupo Domain Admins quando o acesso Domain Admin for necessário. Após a conclusão do processo, a conta deve ser removida do grupo Domain Admins.


## Usar várias contas (utilizador normal e conta de administrador)

Um dos pilares da segurança de computadores é distinguir entre uma conta de utilizador regular usada para tarefas do dia a dia e uma conta de administrador separada usada para tarefas administrativas. Esta abordagem envolve configuração personalizada e medidas de segurança para ambas as contas para atender às suas necessidades.

  

**Por que devemos usar várias contas?**

**Separação de Privilégios**

Uma conta de utilizador regular tem permissões limitadas, enquanto a conta de administrador tem privilégios mais altos. Isso impede que tarefas do dia a dia interfiram em tarefas administrativas.

  

**Limitar Ataques**

Se asw tarefas diárias e operações administrativas forem realizadas com a mesma conta, malware ou invasores também poderão aceder privilégios de administrador ao assumir o controlo de uma conta de utilizador comum.

  

**Segurança de Dados e Sistemas**

Usar contas diferentes para funções diferentes e usar a conta de administrador somente quando necessário e num computador privado aumenta a segurança dos dados e do sistema.

  

## Como usar?

**Conta de utilizador regular**

Uma conta de utilizador normal é usada para atividades de rotina, como tarefas diárias, navegar na internet e verificação de e-mail. Esta conta tem permissões limitadas, reduzindo assim os riscos potenciais.

  

**Conta de administrador**

Esta é uma conta de administrador usada apenas para operações especiais, como tarefas administrativas, configuração do sistema e instalação de software. Esta conta tem altos privilégios e é importante mantê-la segura.

  

## Criar uma Política de Auditoria

As configurações de política de auditoria são uma medida de segurança importante usada para monitorizar, controlar e registar eventos numa rede. 
Estas políticas são usadas para aumentar a segurança de uma organização e detetar atividades indesejadas. 
Ativar políticas de auditoria por meio da Política de Grupo é uma etapa crítica na deteção de vulnerabilidades e na defesa contra ataques informáticos.

Devemos certificar de que as configurações da Política de Auditoria mencionadas abaixo estejam definidas na política de grupo e aplicadas a todos os computadores e servidores.

Para configurações de política de auditoria;

A secção “Configuração do computador -> Políticas -> Configurações do Windows -> Configurações de segurança -> Configuração avançada da política de auditoria”:


**Login da conta**

Certificar que a 'Audit Credential Validation' esteja definida como 'Sucesso e falha'

  

**Gerenciamento de contas**

A auditoria 'Application Group Management' está definida como 'Sucesso e falha'

A auditoria 'Computer Account Management' está definida como 'Sucesso e falha'

A auditoria 'Other Account Management Events' está definida como 'Sucesso e falha'

Auditoria 'Security Group Management' está definida como 'Sucesso e Falha'

A auditoria 'User Account Management' está definida como 'Sucesso e falha'

  

**Tracking detalhado**

Auditoria 'PNP Activity' está definida como 'Sucesso'

Auditoria 'Process Creation' está definida como 'Sucesso'

  

**Logon/Logoff**

Auditoria 'Account Lockout' está definida como 'Sucesso e falha'

Auditoria 'Group Membership' está definida como 'Sucesso'

Auditoria 'Logoff' está definida como 'Sucesso'

Auditoria 'Logon' está definida como 'Sucesso e Falha'

A auditoria de 'Other Logon/Logoff Events' está definida como 'Sucesso e falha'

Auditoria 'Special Logon' está definida como 'Sucesso'

  

**Acesso a Objetos**

A auditoria 'Removable Storage' está definida como 'Sucesso e falha'

  

**Mudança de política**

A auditoria 'Audit Policy Change' está definida como 'Sucesso e falha'

Auditoria  'Authentication Policy Change' está definida como 'Sucesso'

Auditoria 'Sensitive Privilege Use' está definida como 'Sucesso'

  

**Uso de privilégios**

A auditoria 'Sensitive Privilege Use' está definida como 'Sucesso e falha'

  

**Sistema**

Auditoria 'IPsec Driver' está definida como 'Sucesso e Falha'

Auditoria 'Other System Events' está definido como 'Sucesso e Falha'

Auditoria 'Security State Change' está definida como 'Sucesso'

A auditoria 'Security System Extension' está definida como 'Sucesso e Falha'

Auditoria 'System Integrity' está definida como 'Sucesso e Falha'


Atividades suspeitas geralmente começam em sistemas de utilizadores finais. Devemos monitorizar todos os sistemas constantemente para conseguir detetar os incidentes de segurança imediatamente.


## Gestão de conta de administrador local

O Windows Local Administrator Password Solution (Windows LAPS) é um método que permite a gestão regular e automática de senhas de contas de administrador local em estações de trabalho e servidores. 
Esta solução fornece um nível mais alto de segurança contra ataques informáticos atualizando constantemente as senhas de contas de administrador local.

  

## Por que devemos usar o Windows LAPS?

**Simplificar a gestão de senhas**

O Windows LAPS permite uma gestão central de senhas para todas as contas de administrador locais. 
Isso substitui atualizações manuais de senhas.

  

**Melhorar a segurança da senha**

Mudanças automáticas de senha e políticas complexas de senha aumentam a segurança da senha. Reduz o risco de usar senhas antigas ou fracas por muito tempo.

  

**Prevenção de ataques**

Senhas fortes e alteradas regularmente para contas de administradores locais reduzem o risco de invasores  assumirem o controlo dessas contas.

  

## Benefícios e Boas Práticas

**Rotação automática de senhas**

Alteração automática regular de senhas de administradores locais.

  

**Políticas de senhas fortes**

Uso de senhas fortes com requisitos de senha complexos e limitações de comprimento.

  

**Registros históricos de senhas**

Armazenar registos de senhas antigas e impedir o uso de senhas antigas.

  

**Registros de senha**

Registro de alterações e atualizações de senha.

  

Resumindo o  Windows LAPS é uma etapa de segurança importante que garante a gestão segura e automática de contas de administrador local. Graças à rotação de senhas, atualizações automáticas e políticas de senhas fortes, ele aumenta a resistência a ataques informáticos, simplificaa gestão e reduz a carga de trabalho.

  
  

## Criar uma política de senha

Criar uma política de senha no Active Directory é uma etapa importante para minimizar vulnerabilidades de segurança e aumentar a segurança da conta. Uma política de senha contém regras e restrições que determinam como as senhas dos utilizadores são criadas, quão complexas elas devem ser e por quanto tempo elas devem ser alteradas.

  

## Por que devemos criar uma política de senhas?

**Exigir senhas fortes**

A política de senha permite que os utilizadores usem senhas fortes e difíceis de adivinhar. Isso torna as contas mais resistentes a ataques.

  

**Aumentar a complexidade**

A política de senha impõe o uso de senhas complexas que contêm diferentes elementos, como letras minúsculas, letras maiúsculas, números e símbolos.

  

**Mudança de senha regular**

A política pode exigir que as senhas sejam alteradas periodicamente. Isso evita o uso de senhas antigas ou fracas.


**Etapas de criação da política de senha do Active Directory**

- Abrir as Ferramentas de Administração do Active Directory e selecionar Gestão de Política de Grupo.
- Para gerir senhas, aceder a Políticas de senha.
- Criar uma nova política de senha e dar um nome à mesma.
- Especificar o nível de complexidade que queremos na política de senha. Por exemplo, o uso de letras maiúsculas, letras minúsculas, números e símbolos.
- Especificar o período de tempo em que a senha será válida. A senha será então desativada e o utilizador precisará de ajuda do administrador para ativá-la novamente. Isso garante que a senha seja alterada regularmente.
- Especificaro número mínimo de vezes que os utilizador devem lembrar das suas senhas anteriores. Isso evita que senhas antigas sejam reutilizadas.
- Definir limites de tempo ou bloqueio de contas como resultado de tentativas de inserir senhas incorretas.
![](../anexos/Pasted%20image%2020241205202618.png)


## Criar uma política de bloqueio

A política de bloqueio é uma medida de segurança importante que bloqueia contas e impede o acesso por um determinado período de tempo como resultado de um número especificado de tentativas incorretas de senha.

Esta política é usada para proteger contra ataques e ameaças à segurança da conta. 

  

**Proteção contra ataques de brute force**

Ataques de brute force são tentativas de invasores de assumir contas tentando combinações de senhas diferentes de forma rápida e contínua. 
A política de bloqueio protege contra esses ataques, garantindo que as contas sejam bloqueadas após um certo número de tentativas incorretas de senha.

  

**Proteção contra ataques Pass-the-Hash**

Ataques pass-the-hash são ataques em que os invasores ganham acesso não autorizado a contas obtendo hashes de senha. 
A política de bloqueio reduz o impacto de tais ataques porque os invasores enfrentam obstáculos mais difíceis quando há um número limitado de tentativas.

  

**Aumentar a segurança da conta**

A política de bloqueio aumenta a segurança da conta porque, se os proprietários da conta esquecerem as suas senhas, a possibilidade de terceiros sequestrarem as contas fazendo inúmeras tentativas de senha é reduzida.

  

**Conscientização da conta**

Se for notado que as contas estão constantemente "locked" ou bloqueadas, isso aumenta a conscientização de que isso pode ser um sinal de um potencial ataque. Dessa forma, as ameaças à segurança podem ser detectadas num estágio inicial.

  

**Retardar os atacantes:**

A política de bloqueio desacelera as tentativas dos invasores de assumir rapidamente o controlo das contas. 
Ter as contas bloqueadas após um certo número de tentativas usando as medidas adequadas é uma maneira eficaz de evitar que invasores tomem facilmente o controlo dos sistemas.

![](../anexos/Pasted%20image%2020241205203125.png)

## Estação de trabalho de administração segura 

Secure Admin Workstation, é um sistema de computador especializado usado apenas para executar tarefas administrativas com contas privilegiadas. 
Essa abordagem é uma maneira eficaz de aumentar a segurança e minimizar ameaças. 

O SAW garante que as operações do administrador sejam protegidas e é um passo importante para maximizar a segurança.

  

## A importância de uma estação de trabalho de administração segura

O uso do Secure Admin Station é de grande importância pelos seguintes motivos:

**Ambiente Isolado para Operações Privilegiadas**

O SAW fornece um ambiente isolado onde contas privilegiadas serão usadas somente para executar tarefas administrativas. Isso garante que transações e sistemas sejam protegidos mesmo se invasores assumirem o controlo das contas.

  

**Controlo de acesso**

O SAW pode ser protegido, pois é usado apenas para operações administrativas. Isso dificulta que malware ou invasores acedam o sistema durante operações comuns do utilizador.

  

**Reduzir ameaças**

Usar o SAW reduz o risco de baixar malware, ser infectado com ransomware ou links maliciosos.

  

## Recursos da estação de trabalho do administrador seguro

A Estação de Administração Segura deve ter os seguintes recursos:

  

**Ambiente Isolado**

O SAW deve ser isolado das operações normais do utilizador e do tráfego de rede.

  

**Sem acesso à Internet**

O SAW não deve ser usado para tarefas como verificar e-mails ou navegar na web. O acesso à Internet deve ser bloqueado.

  

**Autenticação Forte**

O acesso ao SAW só deve ser possível com contas privilegiadas, e essas contas devem ser protegidas com senhas fortes ou autenticação multifator.

  

**Somente os aplicações necessárias devem ser instaladas**

Somente aplicações necessárias para operações administrativas devem ser instaladas no SAW. Softwares e aplicações desnecessárias devem ser removidas.

  

**Manter atualizado**

O sistema operativo e as aplicações no SAW devem ser atualizados regularmente. Atualizações de segurança e patches devem ser aplicados regularmente.

  

## Vantagens da estação de trabalho de administração segura

**Melhor Segurança**

O SAW aumenta a segurança  realizando operações privilegiadas num ambiente isolado.

  

**Risco de ameaça reduzido**

O risco de software malicioso ou ataques atingirem sistemas da organização é reduzido.

  

**Controlo de Operações do Administrador**

O SAW permite que controlar de forma central as operações do administrador, o que é vantajoso em termos de autorização e monitorização de acesso.


**Resposta rápida**

Como apenas operações administrativas são realizadas no SAW, qualquer incidente de segurança pode ser detetado e respondido rapidamente.

  
O uso de SAW oferece uma maneira eficaz de aumentar a segurança e reduzir riscos. Realizar transações privilegiadas num ambiente isolado ajuda a criar uma defesa mais forte contra ataques. 

As organizações devem considerar o uso de estação executiva segura como uma medida de segurança séria.

  

## Suporte ao sistema operativo

Com cada novo lançamento do sistema operacional Windows, a Microsoft introduz recursos e melhorias de segurança integrados. Mais importante, atualizações de segurança. Os sistemas operativos que chegaram ao fim da vida útil, cujas atualizações de segurança não são mais fornecidas pelos fabricantes, são um dos maiores riscos à segurança.

Usar apenas a versão mais recente do sistema operativo aumentará a segurança geral.

Por exemplo, Novos Recursos de Segurança no Windows Server 2022:

- Servidor de núcleo seguro
- Raiz de confiança do hardware
- Proteção de firmware
- Boot seguro UEFI
- Segurança baseada em virtualização


## Gestão de Contas de Serviço

No ambiente do Active Directory (AD), contas de serviço são contas usadas para garantir o funcionamento adequado de sistemas, aplicações e serviços. 

No entanto, essas contas são sensíveis à segurança e podem causar riscos de segurança  se não forem geridas adequadamente. Estas contas geralmente podem ter altos privilégios e levar a fraquezas de segurança, como uso prolongado de senhas ou direitos de acesso.

Como as contas de serviço devem ser geridas de uma perspectiva de segurança:

- Uma conta separada deve ser usada para cada serviço ou aplicação. Isso garante isolamento e protege a segurança de outras contas quando uma conta é afetada. Usar uma conta de serviço partilhada aumenta o risco de segurança.

- Dar às contas de serviço apenas os privilégios mínimos de que precisam impede que invasores tirem vantagem dos seus direitos de acesso. Cada conta de serviço deve ter acesso apenas aos recursos e funções que requer.

- As senhas para contas de serviço devem ser alteradas regularmente e obedecer a políticas de senhas fortes. As senhas não devem permanecer sempre as mesmas. Ferramentas de automação e contas de serviço geridas podem ser usadas para gestão de senhas.

- Contas de serviço devem receber acesso somente aos sistemas e recursos de que precisam. O acesso à rede não deve ser expandido desnecessariamente. Tráfego de rede desnecessário deve ser bloqueado.

- As atividades das contas de serviço devem ser monitorizadas e auditadas regularmente. Atividades anormais devem ser detetadas e respondidas rapidamente. Registos de acesso devem ser revistos ​​regularmente.

- Sistemas e aplicações contendo contas de serviço devem ser mantidos atualizados e corrigidos. Atualizações regulares devem ser feitas para evitar vulnerabilidades de segurança.

  

A gestão de contas de serviço destaca-se como um elemento-chave da segurança do Active Directory. Quando geridas adequadamente, as contas de serviço podem aumentar a segurança do sistema e fornecer uma defesa mais eficaz contra ataques.

  

## Alterações importantes de utilizadores e grupos

Na segurança do Active Directory, o tracking eficaz de alterações importantes de utilizadores e grupos é essencial para garantir a segurança da rede e a integridade dos dados. A monitorização  dessas alterações é necessário para detetar tentativas de acesso não autorizado, evitar violações de segurança e atender aos requisitos de conformidade.

Os logs de eventos dos servidores do Active Directory são usados ​​para auditar essas alterações.
Transações como criação de conta, exclusão, alterações de senha e associações a grupos são registadas nesses logs. 


Eventos básicos que precisam ser seguidos em relação a utilizadores e grupo:

![](../anexos/Pasted%20image%2020241205204325.png)

![](../anexos/Pasted%20image%2020241205204340.png)


Atividades de grupos:

![](../anexos/Pasted%20image%2020241205204415.png)

![](../anexos/Pasted%20image%2020241205204425.png)


## Controlo de Associação de Grupo de Administração Local

Um utilizador com direitos de administrador local tem acesso total a todo o sistema operativo Windows e pode fazer download e instalar software que pode incluir software malicioso, ativar/desativar contas, desativar recursos de segurança do sistema, aceder informações do utilizador e roubar credenciais ou dados, o que pode levar a vários problemas de segurança.

Um utilizador padrão não deve estar no grupo de administradores locais.

**O relatório de vulnerabilidades de segurança da Microsoft afirma:**

“De todas as vulnerabilidades do Windows descobertas em 2018, 169 delas foram consideradas 'críticas'. Remover direitos de administrador poderia ter mitigado 85% dessas vulnerabilidades críticas”.

![](../anexos/Pasted%20image%2020241205204607.png)

Ao remover utilizadores do grupo de administradores locais, reduzimos bastante os riscos de invasores obterem acesso ao computador e rede.

**É recomendado usar a política de grupo para controlar o grupo de administração local.** 

Se remover-mos essas permissões do computador local sem controlo central, esses direitos poderão ser adicionados novamente.




