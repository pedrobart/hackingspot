Resumi aqui uma compreensão aprofundada de malware e ransomware, os seus tipos, objetivos e propriedades. Também forneci uma visão geral da relação entre vulnerabilidades e explorações e explorar o conceito de ransomware e os seus vários tipos.

Após a conclusão, será possível:

- Identificar os objetivos e propriedades de diferentes tipos de malware
- Descrever malware avançado e o seu papel em ataques coordenados
- Descrever os conceitos de vulnerabilidades e explorações e o seu papel nos ataques informáticos
- Identificar os tipos de ransomware e as etapas para um ataque de ransomware bem-sucedido

### Malware e Ransomware

Malware (abreviação de “software malicioso”) é um arquivo ou código que normalmente:

 - Assume o controlo; 
 - Coleta informações; 
 - Danifica um endpoint infectado.

#### Definições e Objetivos

Malware é um termo inclusivo para todos os tipos de software malicioso.

##### Malware

- O malware geralmente tem um ou mais dos seguintes objetivos: 
- Fornecer controlo remoto para um invasor usar uma máquina infectada;
- Enviar spam da máquina infectada para alvos desavisados;
- Investigar a rede local do utilizador infectado e roubar dados confidenciais.

##### Malware avançado/moderno

Malware avançado ou moderno geralmente refere-se a malware novo ou desconhecido. 
Esses tipos de malware são altamente sofisticados e frequentemente têm alvos especializados. Malware avançado normalmente pode contornar  facilmente defesas tradicionais.

### Tipos de malware

O malware é variado em **tipo** e **capacidades**. Vamos rever vários tipos de malware.

**Logic Bombs**

Uma Logic Bomb é um malware que é acionado por uma condição específica, como uma data específica ou uma conta de utilizador específica sendo desativada.

#### Spyware e Adware

Spyware e adware são tipos de malware que coletam informações como:

- Comportamento de navegação na Internet; 
- Credenciais de login e informações de conta financeira, num endpoint infectado. 
- Spyware frequentemente altera as configurações do navegador e de outros softwares e reduz a velocidade do computador e da Internet num endpoint infectado. 
- Adware é um spyware que exibe anúncios num endpoint infectado, geralmente como banners pop-up.

#### Rootkits

Um rootkit é um malware que fornece acesso privilegiado (nível de root) a um computador. Os rootkits são instalados na BIOS de uma máquina, o que significa que as ferramentas de segurança de nível de sistema operacional **não** conseguem detectá-los.

#### Bootkits

Um bootkit é um malware que é uma variante do modo kernel de um rootkit, muito usado para atacar computadores protegidos por criptografia de disco completo.

#### Backdoors

Um backdoor é um malware que permite que um invasor ignore a autenticação para obter acesso a um sistema comprometido.

#### Anti-AV

Anti-AV é um malware que desabilita o software antivírus instalado legitimamente no endpoint comprometido, impedindo assim a detecção e remoção automática de outros malwares.

#### Ransomware

Ransomware é um malware que bloqueia um computador ou dispositivo (Locker ransomware) ou criptografa dados (Crypto ransomware) num endpoint infectado com uma chave de criptografia que somente o invasor conhece, tornando os dados inutilizáveis ​​até que a vítima pague um resgate (geralmente com criptomoeda, como Bitcoin).

#### Trojan Horse

Um cavalo de Troia é um malware disfarçado como um programa inofensivo, mas que na verdade dá ao invasor controlo total e privilégios elevados de um endpoint quando instalado. 

Ao contrário de outros tipos de malware, os cavalos de Troia geralmente não são auto-replicantes.

#### Vírus

Um vírus é um malware que se autorreplica, mas precisa primeiro infectar um programa host e ser executado por um utilizador ou processo.

#### Worms

Um worm é um malware que normalmente tem como alvo uma rede de computadores replicando-se para se espalhar rapidamente. Diferente dos vírus, os worms não precisam infectar outros programas e não precisam ser executados por um utilizador ou processo.

### Malware avançado ou moderno

O malware moderno é furtivo e evasivo. Ele desempenha um papel central num ataque coordenado contra um alvo.

Malware avançado ou moderno alavanca redes para ganhar poder e resiliência. 
Malware moderno pode ser atualizado — assim como qualquer outra aplicação de software — para que um invasor possa mudar de curso e cavar mais fundo na rede ou fazer mudanças e promulgar contramedidas.

Essa é uma mudança fundamental em comparação aos tipos anteriores de malware, que geralmente eram agentes independentes que simplesmente se infectavam e se replicavam.

#### Tipos de malware avançado ou moderno

###### Características técnicas dos malwares mais avançados: 

**Ofuscação:**
- Malware avançado frequentemente usa técnicas comuns de ofuscação para esconder certas strings binárias que são caracteristicamente usadas em malware e, portanto, facilmente detectadas por assinaturas antimalware. 
- Malware avançado também pode usar essas técnicas para esconder um programa de malware inteiro.

**Polimorfismo:**
- Alguns malwares avançados têm secções inteiras de código que não servem para nada além de alterar a assinatura do malware, produzindo assim um número infinito de hashes de assinatura exclusivos. 
- Técnicas como polimorfismo e metamorfismo são usadas para evitar a detecção por ferramentas e softwares antimalware tradicionais baseados em assinatura. 

Por exemplo, uma alteração de apenas **um único caractere** ou **bit** do arquivo ou código-fonte altera completamente a assinatura de hash do malware.

**Distribuído:**
- O malware avançado aproveita ao máximo a resiliência incorporada à própria internet. 
- O malware avançado pode ter vários servidores de controle distribuídos por todo o mundo com várias opções de fallback. 
- O malware avançado também pode aproveitar outros endpoints infectados como canais de comunicação, fornecendo assim um número quase infinito de caminhos de comunicação para se adaptar a condições de mudança ou atualizar o código conforme necessário.

**MultiFuncional:**

Atualizações de servidores C2 também podem mudar completamente a funcionalidade de malware avançado. 

 - Essa capacidade multifuncional permite que um invasor use endpoints estrategicamente para Realizar tarefas específicas como: 
 - Roubar números de cartão de crédito; 
 - Enviar spam contendo outras cargas de malware (como spyware)
 - Instalar ransomware com o propósito de extorsão.


***

### Ransomware, vulnerabilidades  e explorações

### Tipos de Ransomware

Embora o ransomware criptográfico seja o tipo mais comum e bem-sucedido de ransomware, ele não é o único. É importante lembrar que o ransomware não é uma única família de malware, mas sim um modelo de negócio criminoso no qual o malware é usado para manter algo de valor em troca de resgate.

#### Introdução avançada ao ransomware

Embora comprometer ativos de valor para resgate não seja um conceito novo, o ransomware tornou-se um negócio criminoso multibilionário visando indivíduos e organizações. Devido às suas baixas barreiras de entrada e eficácia na geração de receita, ele rapidamente deslocou outros modelos de negócios de crimes cibernéticos e tornou-se a maior ameaça enfrentada pelas organizações hoje em dia. Também é importante observar que, embora os agentes de ameaças geralmente descriptografem os seus dados após o resgate ser pago (o modelo de negócios do ransomware depende de uma expectativa razoável de que pagar um resgate restaurará o acesso aos seus dados), não há garantias de que esse será o caso. Além disso, muitos agentes de ameaças agora estão a exfiltrar uma cópia dos dados das suas vítimas antes de criptografá-los e, em seguida, **vendem os dados na dark web após o resgate ser pago**.

#### Ataques de ransomware em organizações

Embora o malware implementado na geração atual de ataques de ransomware criptográfico não seja especialmente sofisticado, ele provou ser muito eficaz não apenas em gerar receita para os operadores criminosos, mas também em impedir que as organizações impactadas continuem as suas operações normais. Novas notícias a cada semana demonstram que organizações grandes e pequenas são vulneráveis ​​a essas ameaças, atraindo novos invasores para entrar na onda e começar a lançar as suas próprias campanhas de ransomware.

#### Cinco etapas de execução do atacante

Se o invasor falhar em qualquer uma dessas etapas, o esquema **não** terá sucesso. 
Embora o conceito de ransomware exista há décadas, a tecnologia e as técnicas, como criptografia e descriptografia confiáveis, necessárias para concluir todas essas cinco etapas em larga escala não estavam disponíveis até alguns anos atrás. 

##### Etapa 1: Comprometa e controle um sistema ou dispositivo

**Os ataques de ransomware geralmente começam com engenharia social para enganar os utilizadores a abrir um anexo ou ver um link malicioso no seu navegador da web.** 

Isso permite que os invasores instalem malware num sistema e assumam o controlo. No entanto, outra tática cada vez mais comum é que os invasores obtenham acesso à rede, realizem reconhecimento na rede para identificar alvos em potencial e estabelecer Comando e Controlo (C2), instalar outros malwares e criar contas de backdoor para persistência e, potencialmente, exfiltrar dados.

##### Etapa 2: Impedir o acesso ao sistema

Os invasores identificarão e criptografarão certos tipos de arquivos ou negarão acesso a todo o sistema.

##### Etapa 3: Notificar a vítima

Embora pareça óbvio, atacantes e vítimas geralmente falam línguas diferentes e têm níveis variados de capacidades técnicas. Os atacantes devem alertar a vítima sobre o comprometimento, declarar o valor do resgate exigido e explicar as etapas para recuperar o acesso.

##### Etapa 4: aceitar pagamento de resgate

Para receber pagamentos e fugir da polícia, os invasores utilizam criptomoedas como Bitcoin para a transação.

##### Etapa 5: Retorne o acesso total

Os invasores devem retornar o acesso ao(s) dispositivo(s). A falha em restaurar os sistemas comprometidos destrói a eficácia do esquema, pois ninguém estaria disposto a pagar um resgate se não acreditasse que seus objetos de valor seriam devolvidos.

***

### Vulnerabilidades e explorações

Vulnerabilidades e explorações podem ser aproveitadas para forçar o software a agir de maneiras que não foram planeadas, como coletar informações sobre as defesas de segurança atuais.

#### Vulnerabilidade

Vulnerabilidades são rotineiramente descobertas em software a uma taxa alarmante. Vulnerabilidades podem existir em software quando o software é inicialmente desenvolvido e lançado, ou vulnerabilidades podem ser criadas inadvertidamente, ou até mesmo reintroduzidas, quando atualizações de versão subsequentes ou patches de segurança são instalados.

#### Explorar

Um exploit é um tipo de malware que tira vantagem de uma vulnerabilidade num endpoint instalado ou software de servidor, como um navegador da web, Adobe Flash, Java ou Microsoft Office. Um invasor cria um exploit que tem como alvo uma vulnerabilidade de software, fazendo com que o software execute funções ou código em nome do invasor.

#### Corrigindo vulnerabilidades

Os patches de segurança são desenvolvidos pelos fornecedores de software o mais rápido possível após uma vulnerabilidade ser descoberta no seu software.

##### 1. Descoberta

Um invasor pode descobrir uma vulnerabilidade e começar a explorá-la antes que o fornecedor do software esteja ciente dela ou tenha a oportunidade de desenvolver um patch.

##### 2. Desenvolvimento do Patch

O atraso entre a descoberta de uma vulnerabilidade e o desenvolvimento e lançamento de um patch é conhecido como ameaça de zero day (ou exploração).

##### 3. Teste e implemente o patch

Podem passar meses ou anos antes que uma vulnerabilidade seja anunciada publicamente. Depois que um patch de segurança se torna disponível, inevitavelmente é necessário tempo para que as organizações testem e implantem adequadamente o patch em todos os sistemas afetados. Durante esse tempo, um sistema executando o software vulnerável corre o risco de ser explorado por um invasor.

#### Como os exploits são executados

Exploits podem ser incorporados em arquivos de dados aparentemente inócuos (como documentos do Microsoft Word, arquivos PDF e páginas da web) ou podem ter como alvo serviços de rede vulneráveis. 
Exploits são particularmente perigosos porque geralmente são empacotados em arquivos legítimos que não acionam software antimalware (ou antivírus) e, portanto, não são facilmente detectados. 

###### 1. Criação
A criação de um arquivo de dados de exploração é um processo de duas etapas. A primeira etapa é incorporar um pequeno pedaço de código malicioso dentro do arquivo de dados. No entanto, o invasor ainda precisa enganar a aplicação para executar o código malicioso. Assim, a segunda parte da exploração normalmente envolve técnicas de corrupção de memória que permitem que o código do invasor seja inserido no fluxo de execução do software vulnerável.

###### 2. Ação
Após o arquivo de dados de exploração ser criado, uma aplicação legítima, como um visualizador de documentos ou navegador da web, executará ações em nome do invasor, como estabelecer comunicação e fornecer a capacidade de carregar malware adicional para o endpoint de destino. Como a aplicação que está a ser explorada é uma aplicação legítima, o antivírus tradicional baseado em assinatura e o software de lista de permissões praticamente não têm defesa contra esses ataques.

###### 3. Técnicas
Embora existam milhares de exploits, todos eles dependem de um pequeno conjunto de técnicas principais. Alguns ataques podem envolver mais etapas, e alguns podem envolver menos, mas normalmente três a cinco técnicas principais devem ser usadas para explorar uma aplicação. Independentemente do ataque ou de sua complexidade, para que o ataque seja bem-sucedido, o invasor deve executar uma série dessas técnicas principais de exploit em sequência.

###### 4. Heap spray
Heap spray é uma técnica usada para facilitar a execução de código arbitrário injetando uma certa sequência de bytes na memória de um processo de destino.


***
#### Cronograma de eliminação de uma vulnerabilidade

Vulnerabilidades podem ser exploradas desde o momento em que o software é implementado até que ele seja corrigido. 

##### 1. Software implementado
Para os sistemas locais, a única maneira de eliminar vulnerabilidades é aplicar patches eficazes nos sistemas e softwares.
##### 2. Vulnerabilidade descoberta
Os patches de segurança são desenvolvidos pelos fornecedores de software o mais rápido possível após uma vulnerabilidade ser descoberta no seu software.
##### 3. As explorações começam
O processo de descoberta e aplicação de patches continuará. 
78% dos exploits aproveitam vulnerabilidades com menos de dois anos, o que implica que desenvolver e aplicar patches é um processo longo.
##### 4. Anúncio público de vulnerabilidade
Um invasor pode descobrir uma vulnerabilidade e começar a explorá-la antes que o fornecedor do software esteja ciente dela ou tenha a oportunidade de desenvolver um patch.
##### 5. Patch lançado
Esse atraso entre a descoberta de uma vulnerabilidade e o desenvolvimento e lançamento de um patch é conhecido como ameaça de zero day (ou exploração).
##### 6. Patch implementado
Meses ou anos podem passar antes que uma vulnerabilidade seja anunciada publicamente. Depois que um patch de segurança se torna disponível, inevitavelmente é necessário tempo para que as organizações testem e implementem adequadamente o patch em todos os sistemas afetados.
##### 7. Protegido pelo Patch do Fornecedor
Durante esse período, um sistema que executa o software vulnerável corre o risco de ser explorado por um invasor.

***
### Como descriptografar ransomwares e como impedir?

Atualmente, as autoridades e empresas especializadas em segurança informática empregam uma combinação de técnicas e estratégias para lidar com ransomwares, incluindo a descriptografia e a prevenção. 

### 1. Recuperação de Chaves de Descriptografia:
   - **Infiltração e Apreensão de Servidores**: Em alguns casos, as autoridades conseguem rastrear e apreender os servidores controlados por grupos de ransomware. Esses servidores frequentemente armazenam as chaves de descriptografia, que podem ser usadas para libertar os arquivos sequestrados/criptografados.
   - **Colaboração Internacional**: A cooperação entre agências de diferentes países pode resultar na captura dos responsáveis pelo ataque, que às vezes cooperam para evitar punições severas, entregando as chaves de descriptografia.

### 2. Desenvolvimento de Descriptografadores:
   - **Análise de Código Malicioso**: Pesquisadores de segurança informática analisam o código dos ransomwares para identificar possíveis falhas na implementação da criptografia. Essas falhas podem permitir a criação de ferramentas de descriptografia específicas para certos tipos de ransomware.
   - **Plataformas de Descriptografação**: Organizações como a *No More Ransom* oferecem ferramentas gratuitas para descriptografar arquivos sequestrados por certas variantes de ransomware.

### 3. Prevenção e Mitigação:
   - **Backups Regulares**: Manter backups atualizados e armazenados em locais seguros é uma das formas mais eficazes de mitigar os efeitos de um ataque de ransomware, permitindo a restauração dos dados sem pagar o resgate.
   - **Educação e Preparação **: Educação de funcionários sobre práticas seguras de navegação e conscientização sobre phishing ajuda a prevenir a infecção inicial por ransomware.
   - **Segmentação de Rede**: Isolar diferentes partes da rede pode limitar a propagação do ransomware caso uma máquina seja infectada.

### 4. Inteligência e Colaboração:
   - **Partilha de Inteligência**: As autoridades e empresas de cibersegurança partilham informações sobre novos tipos de ransomware e técnicas de mitigação. Essa colaboração global aumenta a capacidade de resposta a novos ataques.
   - **Monitoramento Contínuo**: Ferramentas avançadas de monitoramento e detecção de ameaças são utilizadas para identificar e bloquear tentativas de infecção por ransomware em tempo real.

### 5. Ataques a Infraestrutura do Ransomware:
   - **Neutralização de Botnets**: Grupos de ransomware frequentemente utilizam redes de bots para distribuir o malware. As autoridades trabalham para identificar e desmantelar essas redes.
   - **Destruição de Carteiras de Criptomoedas**: Em alguns casos, as autoridades têm conseguido rastrear e congelar carteiras de criptomoedas usadas para receber os pagamentos de resgate, cortando o financiamento dos grupos criminosos.

Essas estratégias combinadas têm ajudado a reduzir a eficácia dos ataques de ransomware, embora o desafio seja constante, dado que os ciber-criminosos  estão sempre a desenvolver novas técnicas para evitar a detecção e maximizar os lucros.