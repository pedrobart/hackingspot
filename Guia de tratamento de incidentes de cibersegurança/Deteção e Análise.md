A Detecção e Análise é a etapa em que o incidente de segurança  é detetado e investigado em profundidade.


#### Deteção

Todo incidente de segurança  começa com a deteção.
Os eventos de segurança  podem ser transmitidos por meio de diferentes canais. Por exemplo, pode ser através de uma regra SIEM acionada, de um alerta acionado pelos produtos de segurança  da equipa a informr que o sistema está lento ou de uma notificação enviada por meio  contato da nossa organização.

#### Verificação

As coisas seriam ainda mais fáceis se cada deteção fosse um incidente de segurança cibernética, mas não é sempre assim. Primeiro a deteção deve ser verificada e avaliada se é realmente um incidente de segurança ou um falso positivo.

Um analista SOC resolve centenas de alertas (deteções) SIEM na sua rotina diária de trabalho. 

Como analista de resposta a incidentes, devemos primeiro confirmar a precisão da deteção recebida e se se trata de um incidente de segurança. Por exemplo, temos uma deteção da equipa a indicar algumas anormalidades na extensão dos arquivos no servidor. 
Pressupor que isso é causado diretamente por ransomware e pelos processos de resposta a incidentes e isolar o servidor, poderá causar alguma interrupção desnecessária do serviço. Devemos primeiro verificar a deteção de entrada. Portanto, a primeira coisa que precisamos fazer é verificar se o arquivo realmente possui uma extensão anormal. 
Lembrar de que a deteção correta nem sempre prova que se trata de um incidente de segurança. Mesmo que a extensão do arquivo seja anormal, alguém com acesso ao servidor pode ter feito isso por engano. O que precisamos fazer é investigar o motivo pelo qual a extensão do arquivo é uma extensão anormal (por exemplo, investigar os logs do Sysmon(Se tiver implementado) para poder entender quem modificou o arquivo e qual processo ele usou para fazer isso). Depois de concluir a investigação, descobrimos que alguém pode ter feito isso por engano.

Neste exemplo, antes de iniciar os processos de resposta a incidentes, é extremamente importante confirmar a precisão da deteção identificada e se é realmente é um incidente de segurança ou não.

Se realmente for  um incidente de segurança devemos começar a coletar e registar as evidências. 

Exemplo de reporting:
- O status atual do incidente (novo, em andamento, em investigação, resolvido, etc.) 
- Um resumo do incidente
- Indicadores relacionados ao incidente
- Outros incidentes relacionados a este incidente
- Ações tomadas por todos pelos outros colaboradores da equipa neste incidente
- Avaliações de impacto relacionadas ao incidente
- Informações de contato de outras partes envolvidas (por exemplo, proprietários do sistema, administradores do sistema)
- Uma lista de evidências coletadas durante a investigação do incidente
- Próximas etapas a serem executadas (por exemplo, reconstruir o host, atualizar uma aplicação).

Como as informações de resposta a incidentes contêm dados críticos, é necessário mantê-las sempre atualizadas e limitar o número de utilizadores que podem aceder a essas informações.

***
#### Prioridade

Vamos estar expostos a mais de um incidente de segurança a ao mesmo tempo. A abordagem de resposta aos incidentes de cibersegurança numa base de “primeiro a chegar, primeiro a servir” não é correta. Devemos priorizar os incidentes do ponto de vista da gravidade, criticidade, área de impacto, danos potenciais, etc. e começar a lidar com esses incidentes de acordo com essa prioridade.

#### Impacto Funcional do Incidente
![[Untitled.png|600]]
***
#### Análise
A etapa de análise é onde as atividades do invasor são analisadas. Nesta etapa, todos os detalhes devem ser analisados ​​desde o primeiro passo de acesso do invasor até as suas atividades mais recentes nos sistemas.

#### Analisando a causa raiz
Ao responder a incidentes de cibersegurança, a nossa prioridade deve ser detetar o método de acesso do atacante e impedir esse acesso.

Vamos pensar num cenário em que um invasor obtém acesso ao sistema explorando uma vulnerabilidade que detectou. Tentar excluir o software malicioso utilizado pelo invasor dos servidores antes de encontrar o método de acesso inicial do invasor, o invasor explorará a vulnerabilidade novamente e acederá ao servidor novamente para instalar o malware. Por esta razão, em primeiro lugar, a causa raiz deve ser detectada e remediada.

Depois que a causa raiz for detetada, devemos executar a etapa de Contenção, Erradicação e Recuperação para evitar que o invasor comprometa os sistemas novamente durante os esforços de resposta a incidentes. Após esta etapa, as demais atividades do invasor deverão ser analisadas voltando à etapa de Análise.

#### Analisando Outras Atividades
Durante a resposta ao incidente, após eliminar a possibilidade do invasor aceder novamente os sistemas através do método de acesso inicial, outras atividades também deverão ser analisadas.

As etapas de deteção e análise e contenção, erradicação e recuperação estão num ciclo contínuo dentro de si. 
Os dispositivos e utilizadores comprometidos devem ser isolados da rede rapidamente.

