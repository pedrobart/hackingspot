O AnyDesk é uma ferramenta legítima que permite a visualização e controlo remoto de computadores e dispositivos móveis. Por exemplo, se um colaborador de uma grande empresa tiver um problema técnico, alguém da equipa de IT pode usar o AnyDesk para “assumir o controlo” do dispositivo e diagnosticar o problema.

Dito isto, os atacantes adoram utilizar ferramentas legítimas porque isso permite-lhes:

- Integrar-se facilmente no ambiente
    
- Evitar mecanismos de defesa
    
- Tirar partido da facilidade de utilização

Portanto, quando existe uma ferramenta fácil de usar como o AnyDesk, TeamViewer, etc., e os atacantes têm a oportunidade de a utilizar numa campanha. 

Vamos começar por estabelecer uma ligação a um endpoint utilizando o AnyDesk. 
Suponhamos que o atacante já tem acesso por shell ao sistema, instala então o AnyDesk no computador e adiciona um utilizador e palavra-passe, permitindo-lhe aceder remotamente ao dispositivo a qualquer momento e a partir de qualquer lugar. 

O AnyDesk irá proporcionar ao atacante acesso completo via interface gráfica (GUI), facilitando ainda mais a sua acção.

Do lado da vítima, o atacante pode instalar o AnyDesk diretamente a partir da linha de comandos. Para esta demonstração, instalei o AnyDesk via interface gráfica para facilitar a visualização.

![](../anexos/Pasted%20image%2020250602230739.png)

Neste momento, o atacante tem acesso à interface gráfica (GUI) do servidor da vítima. 

A partir daqui, pode enviar mensagens de chat, transferir ficheiros para e a partir do servidor. Esta capacidade é extremamente poderosa, especialmente se o uso da ferramenta AnyDesk for legítimo nesse ambiente.

Por exemplo, o AnyDesk possui uma funcionalidade de navegação de ficheiros ("browse file") que permite explorar diretórios e aceder diretamente a ficheiros no sistema da vítima.

![](../anexos/Pasted%20image%2020250603220703.png)

Esta funcionalidade permite visualizar todos os ficheiros através de uma interface semelhante ao Explorador do Windows, possibilitando a ação de _drag and drop_ (arrastar e largar) para fazer upload ou download de ficheiros entre o atacante (dispositivo local) e a vítima (dispositivo remoto).

Vamos supor que os atacantes pretendem exfiltrar um ficheiro da máquina da vítima.  
Com o acesso GUI ativo via AnyDesk, o atacante pode simplesmente navegar até ao diretório desejado na máquina comprometida, localizar o ficheiro de interesse e arrastá-lo diretamente para o seu dispositivo local. Esta ação não exige privilégios especiais adicionais, uma vez que o AnyDesk já está a correr com permissões apropriadas atribuídas aquando da instalação ou configuração inicial.

Este tipo de exfiltração é discreto, rápido e, em ambientes onde o AnyDesk é utilizado de forma legítima, pode facilmente passar despercebido aos mecanismos tradicionais de deteção.


Os atacantes podem clicar no botão de download e o ficheiro selecionado será transferido para o seu dispositivo local. Da mesma forma, também é possível fazer upload de ficheiros para a máquina da vítima. Esta funcionalidade pode ser explorada por threat agents para carregar ferramentas maliciosas, como backdoors ou scripts auxiliares, com o objetivo de facilitar a execução de outras fases do ataque.

### Detecção de atividades maliciosas com AnyDesk

Como referido, a localização dos logs do AnyDesk depende da forma como a aplicação está a ser utilizada:

- Quando está instalado, os logs encontram-se em: C:\ProgramData\AnyDesk
    
- Quando executado em modo standalone (portátil), os artefactos e logs estão em: C:\Users\Username\AppData\Roaming\AnyDesk
    

Neste caso, vamos focar-nos no modo standalone, frequentemente utilizado por atacantes para evitar alterações evidentes ao sistema.

### Ficheiros de log relevantes no modo standalone

1. **service.conf**  
    Contém as configurações da instância AnyDesk, incluindo possíveis passwords definidas para acesso remoto não assistido. Pode indicar tentativa de persistência mesmo sem instalação formal.
    
2. **ad.trace**  
    Regista eventos da aplicação, como tentativas de ligação, erros, e início/fecho do programa. Pode incluir identificadores de sessão e timestamps úteis para correlação.
    
3. **connection_trace.txt**  
    Contém o histórico de sessões remotas (entrada e saída). Mostra data e hora da ligação, ID remoto utilizado e duração da sessão.
    
4. **trace.txt**  
    Log geral com mensagens técnicas e informação de debugging. Pode revelar comportamentos suspeitos da aplicação.
    
5. **user.conf**  
    Guarda preferências do utilizador e possíveis dados de sessão.
    

### Indicadores de uso malicioso

- Presença do ficheiro `service.conf` com password configurada para acesso remoto.
    
- Múltiplas ligações remotas fora do horário normal, registadas em `connection_trace.txt`.
    
- Execução do binário AnyDesk a partir de pastas como `%AppData%`, `%Temp%` ou outros diretórios não padrão.
    
- Entradas em `ad.trace` a indicar falhas de autenticação ou ligações repetidas de endereços externos.
    

### Recolha forense e hunting

Durante uma análise ou investigação de incidentes, nós analistas devemos:

- Verificar a existência do diretório `%AppData%\AnyDesk`
    
- Extrair e analisar os ficheiros de log mencionados
    
- Correlacionar os dados com outros artefactos do sistema, como logs de eventos do Windows, logs do XDR/EDR, e comportamento de rede
    
- Avaliar se houve exfiltração de dados ou transferência de ferramentas maliciosas


![](../anexos/Pasted%20image%2020250603221628.png)


O ficheiro `ad.trace`, localizado no diretório `%AppData%\Roaming\AnyDesk`, contém registos detalhados das operações do AnyDesk. Este ficheiro é especialmente útil para identificar atividades suspeitas em cenários onde o AnyDesk foi executado como binário standalone, sem instalação persistente.


## **Pontos-Chave a Monitorizar no `ad.trace`**

###  **Identificação de Sessões Remotas**

- **Palavra-chave**: `Logged in from`; `Incoming session request`.
    
- **Descrição**: Indica que foi estabelecida uma ligação remota ao dispositivo.
    
- **Dados relevantes**: Endereço IP da origem, carimbo de data/hora (UTC).
    
- **Objetivo da análise**: Identificar possíveis ligações externas não autorizadas.


![](../anexos/Pasted%20image%2020250603222424.png)
- **Alias do AnyDesk**
    
    - O campo "bart" corresponde a um **nome personalizado (alias)** definido na aplicação AnyDesk.
        
    - Os utilizadores (ou atacantes) podem configurar o seu AnyDesk com um alias (ex: `bart@ad`) em vez de usar o ID numérico ou endereço IP.
        
- **Abstração da infraestrutura**
    
    - AnyDesk abstrai as ligações através da sua infraestrutura de servidores relay, NAT traversal, ou ligações diretas P2P.
        
    - Mesmo em ligações diretas (como neste caso: `"Connection flags: direct paid"`), o software prioriza mostrar o **nome amigável** em vez do IP.
        
- **IP não visível no `ad.trace`**
    
    - O log `ad.trace` normalmente **não regista diretamente o IP remoto**, a não ser em mensagens de erro de ligação, logs de debug mais detalhados, ou quando combinado com outros ficheiros (`connection_trace.txt` ou ferramentas externas como EDR/NDR/Sysmon).
        
- **Anonimização ou ocultação por design**
    
    - Esta decisão de design visa facilitar a identificação para utilizadores legítimos, mas **dificulta o trabalho forense**, especialmente quando o atacante usa um nome genérico como “bart”.

---
# **Transferência de Ficheiros sem Nome Registado no AnyDesk – Análise Forense**


O ficheiro `ad.trace` do AnyDesk pode registar operações de transferência de ficheiros (upload ou download), mas frequentemente **não inclui o nome do ficheiro** transferido — apenas o caminho do diretório e o estado da transferência (ex: sucesso ou falha). Esta limitação dificulta a identificação direta dos ficheiros manipulados.


## **Desafios Comuns**

- **Caminho parcial apenas**: é habitual aparecer apenas o diretório base, como `C:\Users\victim\Desktop\`, sem menção ao ficheiro.

- **Ausência de metadados**: o log não inclui hash, tamanho ou extensão do ficheiro.

- **Dependência do contexto temporal**: exige correlação com outros artefactos com base no timestamp do log.

## **Artefactos do Windows Relevantes**

Para determinar que ficheiro foi realmente transferido, é necessário correlacionar a entrada do `ad.trace` com outros artefactos forenses do sistema de ficheiros:

### 1. **MFT (Master File Table)**

- Regista operações em ficheiros e diretórios, com timestamps de criação, modificação e acesso.
    
- Permite identificar ficheiros criados ou modificados no diretório referenciado no log, no intervalo temporal correspondente.
    

### 2. **USN Journal**

- Monitoriza alterações a nível de volume NTFS.
    
- Útil para identificar ficheiros criados, renomeados ou apagados.
    
- Permite reconstruir a atividade no diretório onde ocorreu a transferência.
    

### 3. **Prefetch**

- Se o ficheiro transferido foi executado logo após o download (por exemplo, com `explorer.exe`, `notepad.exe`), o nome pode surgir em ficheiros Prefetch.
    
- Pode reforçar a suspeita de execução de um binário malicioso transferido.
    

### 4. **Shellbags, Jump Lists, RecentFiles**

- Artefactos de interação com ficheiros via interface gráfica.
    
- Úteis para identificar navegação no diretório, aberturas recentes e caminhos usados.
    

## **Procedimento de Análise**

1. Identificar o **timestamp** da entrada de transferência no `ad.trace` (exemplo: 2025-06-03 21:21:58).
    
2. Isolar o **diretório** onde a transferência ocorreu (ex: Desktop, Downloads).
    
3. Correlacionar com a **MFT** e **USNJournal**, procurando ficheiros com timestamps coincidentes (+/- 30 segundos).
    
4. Listar ficheiros criados ou modificados nesse período e nesse diretório.
    
5. Analisar os ficheiros encontrados: nome, extensão, conteúdo e metadados.
    
6. Avaliar se algum ficheiro tem características compatíveis com exfiltração ou uso malicioso.
    

## **Exemplo de Entrada no Log e Interpretação**

- O log indica:  
    *Transferência iniciada no diretório C:\Users\victim\Desktop*  
    _Transferência concluída com sucesso_
    
- A partir daí, analisa-se a MFT e o USNJournal para esse diretório e intervalo de tempo.
    
- Caso se detete, por exemplo, a criação de um ficheiro `passwords.xlsx` ou `mimikatz.exe` nesse mesmo segundo, podemos inferir com elevado grau de certeza que foi o ficheiro transferido.

### **Timestamps de Atividades**

- **Descrição**: Cada entrada no ficheiro inclui carimbo de data e hora no formato UTC.
    
- **Objetivo da análise**: Correlacionar eventos com outros logs do sistema, como XDR, Sysmon ou Windows Event Logs.
    

---

### **Transferência de Ficheiros - Preparação**

- **Palavra-chave**: `app.prepare_task`; `app.local_file_transfer`
    
- **Descrição**: Indica que uma tarefa está a ser preparada, normalmente relacionada com a transferência de ficheiros (download a partir da máquina da vítima).
    
- **Objetivo da análise**: Detetar possíveis tentativas de **exfiltração de dados**.
    

![](../anexos/Pasted%20image%2020250603223915.png)
**Interpretação**: Indica o início efetivo do processo de download de um ficheiro a partir do sistema remoto (vítima) para o sistema local (atacante).

- **Timestamp**: 2025-06-03 21:36:55.279
- **Entrada**:
    - `app.local_file_transfer - Download started (0)`

- **Timestamp**: 2025-06-03 21:36:55.289
- **Entrada**:
    - `app.local_file_transfer - Download finished.`

Confirma que o ficheiro foi transferido com sucesso. No entanto, **não é registado o nome do ficheiro nem o caminho completo** nesta entrada.

---

### **Transferência de Ficheiros - Execução**

- **Palavra-chave**: `app.local_file_transfer`
    
- **Descrição**: Indica se a transferência de ficheiros foi concluída com sucesso.
    
- **Dados relevantes**: Caminho dos ficheiros envolvidos, estado da operação.
    
- **Objetivo da análise**: Confirmar movimentações de ficheiros suspeitos entre a máquina da vítima e o sistema do atacante.
    

---

###  **Uso da Área de Transferência (Clipboard)**

- **Palavra-chave**: `Clipboard`
    
- **Descrição**: Indica que o utilizador interagiu com a área de transferência do sistema.
    
- **Objetivo da análise**: Sinalizar possível **movimentação de dados sensíveis** (ex: passwords, comandos, texto confidencial).
    
- **Nota adicional**: Deve complementar-se com a análise de artefactos de clipboard no sistema, quando possível.
    

---

## **Recomendações de Investigação**

- Extrair e preservar o ficheiro `ad.trace` para análise.
    
- Correlacionar os eventos com os logs do sistema (eventos do Windows, EDR, firewall, etc.).
    
- Validar a legitimidade de qualquer endereço IP encontrado nas ligações remotas.
    
- Identificar horários e padrões de atividade fora do normal ou fora do horário laboral.
    
- Procurar evidência de exfiltração ou introdução de ferramentas maliciosas.
