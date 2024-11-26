Ntds.dit (NT Directory Services DataBase) é o arquivo de banco de dados no Active Directory (AD) que contém todas as informações sobre o banco de dados do AD, incluindo a configuração dos domínios do AD, users, grupos, políticas de segurança, hashes de senha e outros objetos. Ele é armazenado em cada controlador de domínio (DC) na floresta do AD e é usado para autenticar users e gerir o acesso a recursos. 

O arquivo Ntds.dit é usado pelo Active Directory Domain Services (AD DS) para armazenar e gerir os dados do diretório, e é essencial para o funcionamento adequado do AD. O banco de dados é um componente essencial do AD e deve ser feito backup regularmente para garantir que ele possa ser recuperado em caso de desastre ou falha.

Por padrão, o arquivo Ntds.dit estará localizado em “%SystemRoot%\NTDS\Ntds.dit” de um controlador de domínio.

Se o invasor obtiver esse banco de dados, ele poderá recuperar senhas em texto simples (fazer isso exigiria o hive do registro SYSTEM também) e, em teoria, ele teria o domínio inteiro. 
Ele pode então obter acesso remoto a qualquer máquina no domínio, incluindo controladores de domínio, e com privilégios totais.
Existem muitas ferramentas que podem ser usadas para despejar esse banco de dados, incluindo um utilitário interno do Windows chamado "ntdsutil". Esse utilitário é usado pelo Windows para fazer backup do arquivo de banco de dados Ntds.dit regularmente e também pode ser usado via linha de comando. Os invasores usam esse utilitário para se misturar ao ambiente, pois esse utilitário é usado normalmente no próprio controlador de domínio para fins de backup.

**Comando:** ntdsutil "ac i ntds" "ifm" "criar C:\Users\Administrador\Área de Trabalho\NTDS_BACKUP completo" qq

- **ac i ntds:** Esta é a opção para ativar a instância do serviço NTDS que está a ser executada na máquina local.

- **ifm** : Esta é a opção para iniciar o submenu Gestão de Instância NTDS, que fornece acesso a comandos para operações de backup e restauração.

- **criar C:\Users\Administrador\Desktop\NTDS_BACKUP completo:** Este é o comando para criar um backup completo do banco de dados Ntds.dit. O backup será salvo no local especificado C:\Users\Administrador\Desktop\NTDS_BACKUP.

1º - **q** : Esta é a opção para sair do utilitário ntdsutil.

2º - **q** : Esta é a opção para sair do submenu Gestão de Instância NTDS.

## Detetar 

Agora vamos focar na parte de detecção e nos tipos de eventos que são gerados devido à atividade acima. Precisaríamos ver os logs de eventos da aplicação. Vamos para os logs do aplicação e depois em Filter current log.
Em seguida, vamos para a opção de fontes de eventos. E selecionamos a fonte “ESENT”.

Como mencionado anteriormente, ntdsutil é usado como uma rotina comum em ambientes de diretório ativo, então devemos olhar para alguns IDs de Evento e focar no PATH do banco de dados. Os invasores tentam enganar e evadir nomeando o caminho dos arquivos como backup, backup crítico, etc.

O primeiro ID de evento que devemos procurar é o ID de evento 325.
Este ID de evento é gerado quando um novo banco de dados é criado. Na maioria dos casos, este ID de evento sozinho pode nos ajudar a determinar a atividade de dump do Ntds.dit, mas apenas para evitar qualquer possíveis falsos positivos, também podemos procurar outro evento que esteja associado a ele.

Vamos ver o ID do evento 327 que é gerado quando um mecanismo de banco de dados desanexa um banco de dados; no nosso caso, a cópia despejada do ntds é desanexada.

Outro ID de evento crucial, que pode realmente adicionar mais contexto à nossa análise, é o ID de evento 216. Esse ID de evento não contém o caminho de localização do nosso banco de dados despejado, mas é gerado sempre que o ntds é gravado no disco em vez do seu local padrão.

“%Systemroot\NTDS\ntds.dit”. Se esse evento for gerado próximo ao horário dos eventos acima que discutimos, isso pode esclarecer nossas dúvidas e pode ser um caso confirmado de dumping de Ntds.dit.

Então para resumir:

1- Selecionar os IDs de evento 325, 327 e 216 nos logs de eventos de aplicação e selecionar a origem do evento como “ESENT”.

2- Procurar por caminhos anormais (qualquer coisa diferente de C:\Windows\NTDS\) nos IDs de evento 325 e 327.

3- O tempo do evento ID 216 seria em torno dos eventos 325 e 327.

4- Se houver muitos eventos mesmo após filtrar usando os IDs de eventos, podemos usar a opção “Find” no EventViewer e procurar pela palavra-chave “ntds”. Isso realmente ajudaria e reduziria a quantidade de eventos a serem analisados.
## Etapas de mitigação 

Não há mitigações diretas contra isto, pois o processo deste ataque é uma operação normal do servidor Windows. No entanto, algumas coisas podem ser feitas para reduzir o risco:

1- Restringir privilégios administrativos em todo o ambiente.

2- Auditst rotineiramente o acesso administrativo e os logins nos controladores de domínio, pois esse ataque só pode ser executado em controladores de domínio.