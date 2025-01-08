
# REDES E COMUNICAÇÃO DE DADOS


### Tópico 

- **Conceitos sobre redes informáticas**
- **Interligação de computadores**
- **Classificação de Redes de Computadores**
- **Comutação de circuitos**
- **Comutação de pacotes**
- **Topologia**
- **Modelo OSI**
- **Conceitos**
	 - **Camadas**
	 - **Protocolos**
- **Dispositivos de interligação de redes**

***

# Dados

- **Entidades adotadas para representar qualquer tipo de informação**
- **Ex.: Voz, vídeo, texto, imagem, gráficos, etc**
***
# Codificação 

- **Representação da informação através de sinais ou símbolos**
- **Processo de converter informações digitais num formato específico para transmissão através de um meio de comunicação, como cabos de rede, fibra óptica ou ondas de rádio.** 
- **A codificação é fundamental para garantir a precisão e a integridade dos dados durante a transmissão, minimizando erros e permitindo a recuperação precisa das informações no destino**
***
# Comunicação 

- **Troca de informação entre equipamentos**
- **Requer um conjunto diversificado de funções e a cooperação entre diferentes tipos de sistemas**
***
# Transmissão de dados

- **Envio de sinais digitais ou analógicos sobre um suporte físico (meio) de transmissão**
- **Sistema de transmissão não reconhece qualquer estrutura associada aos dados**
- **Meio de transmissão pode ser constituído por um conjunto de canais distintos**
***

# Modelo de um sistema de comunicação 


| FONTE                  | EMISSOR                                                                 | MEIO DE TRANSMISSÃO                       | RECETOR                     | DESTINO          |
| ---------------------- | ----------------------------------------------------------------------- | ----------------------------------------- | --------------------------- | ---------------- |
| Gera os dados a enviar | Converte os dados em sinais adequados ao meio de transmissão e envia-os | Transporta os dados sob a forma de sinais | Converte os sinais em dados | Utiliza os dados |
***

# Funções de um sistema de comunicação 

 - **Utilização eficiente do sistema de transmissão**
 - **Geração de sinais a transmitir; sincronização**
 - **Gestão da comunicação; gestão da rede**
 - **Controlo de fluxo; deteção e correção de erros**
 - **Endereçamento e encaminhamento**
 - **Recuperação de anomalias**
 - **Representação da informação (formatação dos dados)**
 - **Segurança**
 ***
# Interligação  de computadores

## Ligação direta

 - **Forma mais simples**
 - **Tipicamente para ligar dois computadores**
 - **Limitada a um número reduzido de computadores**
 - **Só é exequível para curtas distâncias**
 - **Custo cresce com o número de ligações e de forma exponencial**

![](https://i.imgur.com/IGPJFr8.png)


## Recurso a Nós de interligação / Comutadores
 
 - **Solução para interligação de um número elevado de computadores**
 
 - **Disponíveis várias topologias:**
    - **Ex.: malha, estrela, barramento, anel, etc.**
 
 - **Vários tipos de comutação disponíveis**
 - **Comutação de circuitos**
 - **Comutação de pacotes**
 ***
# Rede de Computadores

- **Uma rede de computadores é um conjunto de dispositivos eletrónicos interligados que são capazes de trocar dados entre si.** 

- **Esses dispositivos podem incluir computadores, servidores, dispositivos de armazenamento, dispositivos de rede (como routers, switches e hubs) e dispositivos periféricos.**

- **As redes de computadores permitem que os dispositivos compartilhem recursos, como ficheiros, impressoras e ligações à internet. Facilitam a comunicação e colaboração entre utilizadores, além de possibilitar o acesso a informações e serviços em locais remotos**

![](https://i.imgur.com/rw3qEXp.png)

## Uma Rede de Computadores é constituída por:

#### Elementos de H/W

 - **Computadores.** 
 - **Periféricos: impressoras, scanners, fax, discos**
 - **Meios de transmissão: fios de cobre, fibras ópticas,**
 - **Dispositivos de interligação: repetidores, hub’s**

#### Elementos de S/W

 - **SO específico ou c/ funcionalidades de trabalho em rede.**
 - **Drivers de placas de rede.**
 - **Protocolos de Comunicação.**
 - **Utilitários/programas de aplicação para trabalho em rede.**

#### Vantagens

 - **Partilha de recursos físicos da rede.**
 - **Partilha de programas e ficheiros.**
 - **Intercâmbio de informação: e-mail interno, intranet**

#### Melhor organização no trabalho, o que facilita a:

 - **Definição de diferentes níveis de acesso à informação.**
 - **Supervisão e controlo do trabalho.**
 - **Constituição de grupos de trabalho.**
 - **Calendarização de tarefas.**
 - **…**

#### Desvantagens
 
 - **Velocidade de propagação de vírus;**
 - **Possibilidade de intrusão não autorizada;**
 - **O sistema poderá tornar-se mais complexo de gerir.**

***
# Classificação de redes de Computadores

### Distribuição Geográfica

#### PAN - PERSONAL AREA NETWORK

- **Redes que utilizam tecnologias de comunicação sem fios para interligar computadores, periféricos e equipamentos de voz numa pequena área.**

![](https://i.imgur.com/3QNqeOk.png)

***
### LAN - LOCAL AREA NETWORK

 - **Normalmente limitada a um edifício ou edifícios próximos;**
 - **Em termos de distância máxima não ultrapassa algumas centenas de metros;**
 - **As velocidades de transmissão variam entre os 10,100 e os 1000 Mbps;**
 - **As tecnologias Ethernet e Wireless são comuns neste tipo de redes.**

![](https://i.imgur.com/6q5N905.png)

***
## CAMPUS – Campus Network

 - **Rede informática que interliga vários edifícios de uma organização, concentrados numa determinada área.**
 - **Cada edifício pode conter uma ou mais redes locais (LAN’s).**

***

## MAN – Metropolitan Area Network

 - **Normalmente limitada a uma cidade. As entidades que possuam vários edifícios espalhados por uma grande cidade, recorrem a redes que se enquadram nesta definição**

![](https://i.imgur.com/Ll4yINH.png)

***

## WAN – Wide Area Network

 - **Este tipo de rede interliga regiões, países e continentes.**
 - **A Internet é um exemplo deste tipo de rede.**

![](https://i.imgur.com/HUqa4NU.png)

***

## SAN - Storage Area Network

 - **Redes que se destinam à interligação de computadores e dispositivos de armazenamento.**
 - **Inseridas numa área – sala ou centro de informática.**
 - **Utilizam tecnologias de transmissão de dados de elevado débito.**

![](https://i.imgur.com/5WAzY0D.png)

***

# Comutação de Circuitos

 - **A comutação de circuitos é um método de estabelecer uma ligação de comunicação entre dois pontos numa rede de telecomunicações.**
 
 - **Ex.: rede telefónica**
	 - **Os recursos são reservados antecipadamente para a duração da chamada**
	 - **Chamada tem 3 fases: Estabelecimento, transferência de informação e**
	- **terminação**
 
 - **No estabelecimento da chamada:**
 - **Define-se o percurso da informação**
 - **Reservam-se os recursos necessários (nós de comutação e canais de comunicação)
 - **Reservas estáticas de recursos.**
 - **Uma vez estabelecida a ligação, os dados são transmitidos entre os dois pontos através do caminho dedicado.**
 - **Após a conclusão da chamada, o caminho físico é libertado e os recursos são**
- **devolvidos para uso por outras chamadas.**

# Comutação de Pacotes

 - **Informação é enviada em blocos individuais de dados (pacotes);**
 - **Pacotes competem entre si para usufruírem dinamicamente dos recursos partilhados pela rede**
 - **Como cada pacote é independente dos restantes, necessita de informação de endereçamento, i.e., identificação do recetor da informação**
 - **Cada pacote é processado individualmente em cada nó da rede, enviados de nó para nó, até ao destino;**
 - **Ordem da emissão de pacotes pode não coincidir com a ordem de receção;**
 - **Utilização de caminhos alternativos.**

### Rede pode dispor de mecanismos para:

 - **Manter a ordenação de pacotes nó a nó;**
 - **Reordenação de pacotes na receção**
 - **Deteção de erros**
 - **Recuperação de erros.**
***
# Topologia


- **Uma topologia é essencialmente um mapa da rede.** 
- **A topologia física da rede descreve o layout dos cabos e postos de trabalho e a localização de todos os componentes da rede.**
- **Um meio físico partilhado designa-se por segmento Ethernet, e os dispositivos a ele ligados são os nós (computadores, impressoras e outros equipamentos).**

![](https://i.imgur.com/nz30QFc.png)
***
### Topologia em Barramento (Bus)

 - **O meio físico forma um barramento linear interligando cada um dos pontos de acesso aos sistemas de cablagem.**
 - **Comunicação feita por Broadcast**
 - **Facilidade de instalação**
 - **Menores quantidades de cabo**
 - **Em desuso devido aos problemas relacionados com as falhas**
 - **Dificuldade em mudar ou mover os nós**

![](https://i.imgur.com/XAFRAD6.png)

***
## Topologia em estrela


 - **Um computador poderá estar ligado a um “nó central” de onde saem as ligações para os outros computadores.**
 - **Se um dispositivo falhar só este é afetado**
 - **Facilidade de modificação do sistema**
 - **Desvantagem: dependente do nó central**

![](https://i.imgur.com/Sa0mqOj.png)

***

## Topologia em anel (ring)

 - **Neste caso o meio físico assume a forma de um anel, interligando cada um dos pontos de acesso;**
 - **Os dados circulam de um posto para o outro**
 - **Nº de colisões reduzido o que implica um maior aproveitamento do meio de comunicação**
 - **Desvantagem na localização das falhas. Uma falha de um nó provoca a falha da rede.**

![](https://i.imgur.com/Fv5Rp2G.png)

***

## Wireless

 - **Ad-HOC**
 - **Multiponto onde a comunicação entre os vários equipamentos é assegurada por um equipamento central AcessPoint**

![](https://i.imgur.com/ToLVSxX.png)

***

# Outras classificações

#### Classificação de RC pelos meios de transmissão

 - **Utilização de fios de cobre.**
 - **Utilização de fibras ópticas.**
 - **Transmissão sem fios: rádio, microondas, infravermelhos, WI-FI…**

#### Classificação de RC pelo débito de dados

 - **Baixo, médio, alto e muito alto.**
 - **64 Kbps, 384 Kbps, 1 Mbps, 10 Mbps, 54 Mbps, 100 Mbps, 1 Gbps…**

***

# Modelo ou Arquitetura de Comunicação

 - **A comunicação entre sistemas só é possível no contexto de um conjunto de regras que definem as interações entre estes.**

 - **O conjunto de regras designa-se de modelo ou arquitetura de comunicação.**
 
 - **Uma arquitetura de comunicação define a estrutura e comportamento da parte de um sistema real que é visível para outros sistemas ligados em rede, enquanto envolvidos na transferência e processamento de conjuntos de informação.**
 
 - **Um Modelo pode ser proprietário ou aberto.**


***

# Modelo OSI - Open Systems Interconnection

- **Modelo teórico de normas que deve permitir a interligação de sistemas abertos, independentemente do seu fabricante.**

### **Sendo um sistema aberto apresenta como vantagens:**

- **O desenvolvimento de aplicações e equipamentos é facilitado;**
- **Diversidade de aplicações;**
- **Independência do fabricante;**
- **Integração de vários componentes e/ou equipamentos de diferentes fabricantes, num mesmo sistema, comunicando facilmente.**

### Mas os sistemas abertos também têm desvantagens:

 - **Necessidade de compatibilidade;**
 - **Necessidade do estabelecimento de testes de conformidade.**
 ***
 

 - **Tornou-se num modelo de referência, rico em conceitos aplicáveis à generalidade das arquiteturas de comunicação atuais.**
 
 - **Influenciou e foi influenciado por várias tecnologias que foram surgindo.**

 - **Decompõe o processo de comunicação num conjunto vertical de sete camadas (ou níveis).**

 - **Cada nível do modelo OSI define um conjunto de funcionalidades intimamente relacionadas e necessárias à comunicação com outro sistema.**
 
 - **Confia ao nível imediatamente inferior a execução de funcionalidades mais básicas.**
 
 - **Cada nível disponibiliza um conjunto de serviços ao nível que lhe é imediatamente superior.**
***
# As Camadas do Modelo OSI

 - **Suporte de aplicações**
 - **Representação de dados**
 - **Regras de comunicação**
 - **Controlo de transporte de dados**
 - **Gestão de endereçamento de dados**
 - **Controlo de transmissão**
 - **Ligação física, cabos…**

![](https://i.imgur.com/k06TRvV.png)

***

# Modelo OSI - Camadas

### Cada camada:

 - **Agrega um conjunto relacionado de funções.**
 
 - **Visa a minimização das interações com as camadas adjacentes.**
 
 - **Apenas interage com camadas adjacentes.**

 - **São os protocolos que permitem que entidades de uma mesma camada N, num sistema, comuniquem com a mesma camada N num sistema remoto.**
 
 - **Unidades de dados de uma dada camada são encapsuladas dentro de unidades de dados da camada inferior.**

***

# Modelo OSI – Camadas e Protocolos

![](https://i.imgur.com/I32IvO0.png)

***

# Modelo OSI – Camadas e Protocolos - Encapsulamento

![](https://i.imgur.com/bFvmtJb.png)

***

# Modelo OSI – Camadas e Protocolos

![](https://i.imgur.com/1GHZrxV.png)

***

# Modelo OSI – Resumo sobre cada camada



## Aplicação 

- **representa o software a que as aplicações recorrem para aceder aos recursos da rede.**
---
## Apresentação 

- **espécie de tradutor - converte diferentes tipos de representação de dados, efetua encriptação e também compressão de mensagens**
---
## Sessão 

- **é o elo de ligação entre as aplicações que estão a comunicar através da rede. Trata da segurança de dados, transferência de dados, conexão dos computadores, logouts…**
---
## Transporte

- **assegura a comunicação fiável extremo a extremo;** 
- **garante independência quanto ao tipo e qualidade da rede utilizada, recorrendo a mecanismos de deteção e recuperação de erros e a controlo de fluxo e sequência.**
---
## Rede

- **garante a interligação entre sistemas terminais, independentemente do número e tipo de redes atravessadas;**
	 - **A funcionalidade principal é o encaminhamento (routing) da nformação entre as várias redes;**
	 - **Estabelece a relação entre endereços lógicos e físicos.**
---
## Ligação de dados

- **está próxima da placa de rede que está um nível mais abaixo, pelo que esta camada controla o adaptador de rede; 

- **estabelece a comunicação com outra máquina, controla o fluxo de frames, deteta a ocupação do meio, verifica se os frames lhe são destinados.**
 
 - **Lê a informação da camada física e atribui-lhe uma estrutura lógica (origem/destino).**
 
 - **É nesta camada que a informação é convertida em porções de informação designada por pacotes.**
---
## Físico 

- **é a interface com o meio físico de comunicação;**

**Define a representação lógica da informação; os bits (0 ou 1) são transformados em sinais físicos (ex.: tensões ou correntes elétricas, ondas eletromagnéticas, sinais ópticos) a enviar para o meio físico; define tipos de conetores, tipos de cabos, etc.**

 **Ligações Físicas – Bus, star, ring e mesh…**
 **Componentes físicos - Placas de rede, Repetidores, Hubs…**

---
# Encapsulamento

 ![](https://i.imgur.com/iu3wEfO.png)

***

# O Modelo OSI e o TCP/IP

### O TCP/IP e  os seus protocolos
 
 - **O TCP/IP, embora esteja associado ao modelo OSI, utiliza apenas quatro camadas.**

![](https://i.imgur.com/wt9oIpx.png)



| Camada de ligação                                               | Camada de internet                         | Camada de transporte                                                           | Camada de aplicação                                |
| --------------------------------------------------------------- | ------------------------------------------ | ------------------------------------------------------------------------------ | -------------------------------------------------- |
| onde é definido como a informação vai ser transportada na rede. | é adicionada informação do IP aos pacotes. | onde a informação é enviada e recebida através de protocolos como o TCP e UDP. | utiliza protocolos como o HTTP e FTP entre outros. |
![](https://i.imgur.com/E63Nn4C.png)

***
# Dispositivos de Interligação de Redes

### Dispositivos ativos

 - **Os principais dispositivos ativos usados em redes são:**
 - **Repeater (Repetidor)**
 - **Hub (Concentrador)**
 - **Bridge (Ponte)**
 - **Switch (Comutador)**
 - **Router (Encaminhador)**
***
### Repeater - repetidor

- **O Repetidor permite colmatar um problema que surge em todas as comunicações, esse problema é a distância entre os pontos a ligar;**

- **Todas as tecnologias de comunicacao identificam distâncias máximas para cada segmento de rede;** 

- **Quando ultrapassado esse limite o previsível é que haja perda ou alteração de informação;**

- **Os Repetidores tem como funao filtrar o ruído e promover a regeneração do sinal recebido, propagando-o com um reforço de energia;**

- **Trabalham no nivel 1 do modelo de camadas OSI, ou seja, apenas trabalham no nível físico;**

- **Tem como carateristicas a bidirecionalidade e o facto de não analisarem a informação que neles transita de um segmento para o outro.**

![](https://i.imgur.com/CkeKIiD.png)

***
### Hub – Concentrador

- **Dispositivos muito utilizados na construção de redes locais, principalmente desde o surgimento da cablagem estruturada;**

- **Permitem a ligaao de varios postos de trabalho a um meio comum; toda a informação recebida por uma porta é replicada para as restantes; a topologia usual é a de estrela;**

- **Têm um número de pontos de ligação (4,8,12,24 portas, ou mais), mas todas do mesmo tipo (normalmente RJ45);**

- **Com a ligacao de varios Hubs em cascata cria-se uma topologia em árvore.**

- **Para que seja possível a utilização de uma topologia em arvore é necessário que os Hubs estejam dotados de portas especificas para o efeito (portas de uplink)**

![](https://i.imgur.com/XPheOms.png)


- **As capacidades dos Hubs foram evoluindo:**
	- **Passivos - não regeneram o sinal.**
	- **Ativos - regeneram o sinal.**
	- **Inteligentes ( ... ) - possuem capacidade de diagnóstico.**

- **Com o surgimento de mais equipamentos para as redes locais Ethernet, começaram a colocar-se outros problemas:**

- **Muito tráfego >> muitas colisões >> muita lentidão ....**
- **Como interligar diferentes segmentos de rede ....**


***

### Bridge – Ponte

- **Possibilitam interligacao de redes locais de tipos diferentes**
- **Ex .: Ethernet e fibra óptica.**

- **Diferem dos repetidores, porque trabalham na 2a camada do modelo OSI, permitindo a interligação de redes de diferentes tipos.**

- **Suportam a filtragem de tráfego por endereço MAC .**

- **Constroem uma tabela (forwarding data-base) com base nos endereços MAC, identificando em que porta é que estes estão ligados.**

![](https://i.imgur.com/IZWTR7f.png)

***
### Switch – Comutador

- **Muito utilizados na criação de redes LAN.**

![U2Oh9xh.png](https://i.imgur.com/U2Oh9xh.png)



- **Dispõem de um numero de portas de ligação RJ45 (normalmente 12, 24 ou 48 portas) ...**

- **Muito semelhante aos Hubs quanto ao aspeto e topologia.**

- **Muito diferente dos Hubs, quanto ao seu funcionamento interno.**

- **Constroem uma tabela (de enderecos MAC) onde identificam quais os dispositivos ligados a cada porta, canalizando o tráfego de rede dirigido para um dispositivo apenas para a porta onde esse dispositivo está ligado.**

![](https://i.imgur.com/LgpHF0n.png)


- **Em redes Ethernet, esta segmentaao do tráfego, traduz-se numa enorme redução de colisões, levando a um aumento da largura de banda efetiva, podendo mesmo eliminar as colisões caso a rede esteja em full-duplex.**

- **Operam no nível 2 do modelo OSI.**

***

### Router – Encaminhador

- **Permitem essencialmente a interligação entre redes de tipos diferentes.**

- **São normalmente utilizados para a interligação entre redes locais sobre uma ligação WAN.**

- **Trabalham ao nivel da camada 3 (rede) do modelo OSI.**

- **Responsabilidade de encaminhar pacotes sobre uma ou mais ligações (LAN ou WAN) por forma a garantir que o pacote chega ao destino.**

- **Suporte para ligações de rede com tecnologias e protocolos diferentes, recorrendo a diferentes interfaces de rede no próprio router.**

- **Mais caros e complexos que os switches.**

- **Dependentes dos Protocolos.**

![](https://i.imgur.com/qAEYJQP.png)


***

### SWITCHES ROUTERS

- **Inteligência de um router com a performance de um switch.**

- **Usado no lugar do router para controlar o tráfego.**

- **Otimizado com tráfego IP.**


![](https://i.imgur.com/3JTwor5.png)

***

### GATEWAY

- **Uma gateway corresponde a uma combinação de hardware e software que liga diferentes ambientes de rede.** 

- **É o dispositivo de rede mais complexo, já que executa traduções em múltiplos níveis do modelo OSI.**

![](https://i.imgur.com/h5jcb5X.png)


***

## Continuação do conteúdo  em breve

