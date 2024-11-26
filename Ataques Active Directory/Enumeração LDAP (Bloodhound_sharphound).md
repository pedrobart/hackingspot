LDAP (Lightweight Directory Access Protocol) é um protocolo para aceder e manter serviços de informações de diretório distribuídos numa rede de Protocolo de Internet (IP). 
O LDAP é uma parte importante do Active Directory, pois fornece o protocolo subjacente para aceder e manter as informações armazenadas no diretório. Com o LDAP, o Active Directory pode ser consultado e atualizado de forma padronizada, permitindo que várias aplicações e serviços interajam com o diretório. 
O LDAP é usado pelo Active Directory para autenticar users, impor políticas de segurança e gerir o acesso a recursos. Por exemplo, quando um user faz login num domínio do Windows, o Active Directory usa o LDAP para verificar as credenciais do user e determinar se ele tem as permissões necessárias para aceder aos recursos solicitados.

O uso do LDAP no Active Directory também torna possível a integração com outros sistemas e aplicações que suportam o protocolo LDAP. Isso permite que as organizações alavanquem os seus investimentos no Active Directory e fornece um local único e centralizado para gerir informações de users e recursos.

perigo:
Permite que o invasor enumere e reúna muitas informações sobre o domínio e obtenha o layout do terreno. Eles podem obter nomes de contas de users de domínio, nomes de computadores e muitas outras informações. Na verdade, essa é uma das primeiras coisas que os invasores realizam para criar um plano sobre como penetrar ainda mais na rede.

  

## Ataque 

Há uma ferramenta chamada “ **bloodhound** ” que enumera o LDAP no diretório ativo e então cria um gráfico visual completo, fornecendo a estrutura lógica de todo o domínio, o que torna mais fácil para o invasor planear ainda mais o seu ataque para comprometer o Controlador de Domínio/Administradores de Domínio o mais rápido possível. O Bloodhound tem um coletor chamado “ **sharphound** ” que, quando executado num computador num diretório ativo, ele consultará o LDAP e coletará muitas informações e então criará um arquivo zip delas. Então esse arquivo zip é ingerido no banco de dados Neo4j, que então cria um gráfico completo. 

![[Pasted image 20241124170842.png]]

## Deteção 

LDAP é um requisito funcional do Active Directory, portanto, há milhares de interações com isso no Active Directory. Os invasores aproveitam isso, pois podem fazer enumerações à vista de todos, pois não há uma maneira direta de saber se a solicitação LDAP pertence a um ator malicioso ou se é uma solicitação legítima. É por isso que a auditoria no acesso a objetos é desabilitada por padrão no Active Directory. Se cada objeto (cada conta, cada serviço, cada computador e muitos mais) começar a ser registado sempre que consultado via LDAP, isso causaria problemas significativos de desempenho no domínio e as operações seriam interrompidas. É por isso que não é ideal registrar cada objeto sempre que o LDAP for consultado sobre eles. Se um user fizer login num computador, 5 a 6 logs de auditoria seriam registados apenas para esse evento. E como o ambiente corporativo tem milhares de users, isso não é o ideal e não é recomendado.

Insirir objetos CANARY. Uma solução viável para o problema acima é criar contas de users, nomes de computador, grupos etc. no Active Directory que não sejam usados ​​por ninguém e, em vez disso, apenas desempenhem o papel de contas/computadores/grupos fictícios. Faça com que pareçam contas legítimas, computadores etc. e se misturem bem ao ambiente. Ninguém seria capaz de dizer a diferença entre uma conta fictícia e uma legítima. Em seguida, habilitar a auditoria nesses objetos fictícios e sempre que um invasor usar ferramentas automatizadas como o bloodhound, esses objetos fictícios também seriam consultados do LDAP, fazendo com que o evento fosse registado sem problemas de desempenho. Deve haver centenas de objetos CANARY para ter uma melhor chance de deteção em ambientes grandes.

Um administrador de sistema pode consultar o LDAP sobre qualquer coisa relacionada ao domínio, como nomes de computador, permissões, contas de users, etc., a partir da linha de comando. Da mesma forma, um invasor pode fazer isso a partir da linha de comando também, usando o mesmo comando. Portanto, não há como dizer a diferença entre uma solicitação legítima e uma maliciosa, a menos que o invasor use ferramentas automatizadas como o bloodhound. Se os invasores começassem a consultar o LDAP sobre todas as informações em que estão interessados ​​via linha de comando, isso levaria muitas horas e o processo não seria tão eficiente. Eles nem conseguiriam entender todas essas respostas LDAP quando combinadas. O Bloodhound faz tudo isso e dá um mapa em menos de 5 minutos.

O ID do evento associado à enumeração LDAP é 4662. Se detetarmos muitos eventos num período muito curto de tempo da mesma conta de user, isso é uma indicação de enumeração LDAP. Vamos ver o primeiro evento gerado quando executamos o sharphound.

Para resumir:
1- Filtrar pelo ID do evento 4662.
2- Se muitos eventos ocorrerem num período muito curto, pode ser uma forte indicação de que uma enumeração LDAP ocorreu.

## Etapas de mitigação

1-Evitar enumeração de sessões sem privilégios.