A gestão de users e grupos do Windows desempenha um papel crítico em manter os sistemas Windows a operacionais de forma segura e eficiente. 

### Contas de utilizador e gestão

Uma conta de utilizador é uma identidade definida no Windows para uma pessoa ou serviço. 
Cada conta de utilizador é tipicamente associada a um nome de utilizador e senha.


**Contas de administrador**

Estas contas fornecem acesso total a todos os recursos e configurações do sistema. 
Contas de administrador também têm a capacidade de criar, modificar ou excluir outras contas de utilizador.


**Contas de utilizador padrão**

Estas contas fornecem aos utilizadores a capacidade de executar certos programas e gerir arquivos e configurações pessoais. 
No entanto, a capacidade de alterar configurações de todo o sistema é frequentemente limitada.

  

Para gestão de utilizadores no Windows Server;

Botão Iniciar -> Gestão do computador -> utilizadores e grupos locais -> utilizadores é aberta:

![](../anexos/Pasted%20image%2020241205191653.png)

Os principais utilizadores padrão que acompanham o Windows Server são os seguintes:

![](../anexos/Pasted%20image%2020241205191713.png)

Para criar um novo utilizador local, clicamos com o botão direito do mouse na tela users, selecione "New User", digitamos as informações do utilizador e clique no botão "Create".

![](../anexos/Pasted%20image%2020241205191819.png)

## Permissões e autorizações do utilizador

**Princípio do Menor Privilégio**

Dar aos utilizadores apenas a autoridade necessária, o que significa criar o menor nível de privilégios para os mesmos.

  

**Limitar contas de administrador**

Contas de administrador devem ser usadas em números limitados e somente quando necessário.

  

## Políticas de senha

**Regras de senha forte**

Deve conter pelo menos 12 caracteres, letras, números e caracteres especiais.

  

**Alteração obrigatória de senha**

Os utilizadores devem alterar suas senhas periodicamente.

  

**Autenticação de dois fatores (2FA)**

Avaliar a usabilidade do 2FA e ativar se possível. Isso cria uma camada extra de segurança caso uma senha seja comprometida.

  

**Controle de Conta de Utilizador (UAC)**

Ativar os recursos do UAC para que programas e aplicações só possam obter privilégios elevados com a aprovação do administrador.

  

**Tempos limite de sessão e bloqueios de tela**

Ativar recursos de tempo limite automático e bloqueio de tela para que os sistemas fiquem protegidos quando os utilizadores se afastarem fisicamente do teclado.

  

**Controlo e  monitorização de contas**

Ativar auditoria de contas de users e acesso. 
Rever logs regularmente para identificar atividades anormais ou suspeitas.

  

These precautions are critical to the security of Windows systems. A good user account management practice plays a crucial role in improving system security.

  

## Grupos e Gestão

Um grupo é uma coleção de um ou mais utilizadores. 
Grupos facilitam a gestão de utilizadores e recursos do sistema.

  

**Grupos locais**

Grupos definidos num computador. Grupos locais são usados ​​para gerir recursos num computador específico.

  

**Grupos de Domínio**

Grupos de domínio são usados ​​para gerir recursos em vários computadores na rede.

  

Os membros do grupo podem ter certos privilégios por meio de políticas de grupo. 
Adicionar ou remover um utilizador de um grupo é uma maneira fácil de alterar rapidamente os privilégios de um utilizador.

Botão Iniciar -> Gestão do computador -> Utilizadores e grupos locais -> Grupos:

![](../anexos/Pasted%20image%2020241205192339.png)


Os grupos locais padrão que vêm com o Windows Server são os seguintes:

![](../anexos/Pasted%20image%2020241205192431.png)

![](../anexos/Pasted%20image%2020241205192443.png)

Os grupos padrão que vêm com a função do Windows Server Active Directory são os seguintes:

![](../anexos/Pasted%20image%2020241205192506.png)

![](../anexos/Pasted%20image%2020241205192515.png)

Alguns pontos importantes a serem considerados em relação a "Grupos e Gestão" em termos de segurança do sistema Windows:

**Tipos de grupo e uso**

É importante determinar os tipos de grupos. 
O Windows oferece diferentes tipos de grupos, como local, global e universal. 
Entender qual tipo usar e quando, pode melhorar a segurança.

  

**Controlos de acesso de grupo**

Permissões de grupo: Definir as permissões de acesso a serem atribuídas a grupos de acordo com o princípio do menor privilégio. 

Por exemplo, ao conceder acesso de leitura e escrita, determinar cuidadosamente quem obtém permissões de leitura e escrita.

  

## Relação Utilizador-Grupo

**Adicionar/Remover Utilizador**

Estabelecer um processo de gestão eficaz para adicionar ou remover users de grupos conforme necessário.

  

**Relatórios de Users**

Rever as associações de grupo regularmente e verificar os membros de cada grupo e mantê-los atualizados.

  

## Controlo e monitorização de grupo

**Logs de grupo**

Rever os logs regularmente para verificar alterações de grupo, solicitações de acesso e outros eventos.

  

**Revisão regular**

As permissões e associações de grupo devem ser revistas em intervalos regulares.

  

## Backup e recuperação de grupo

**Backups de grupo**

Fazer backup regularmente das configurações, especialmente para grupos importantes e críticos.

  

Embora estes tópicos sejam importantes para a segurança do grupo e dos seus membros, são críticos para a segurança geral do sistema. 







