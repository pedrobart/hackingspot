O **TeamViewer** é uma aplicação de acesso remoto amplamente utilizada para manutenção e assistência técnica em computadores e outros dispositivos. Tal como o **AnyDesk**, o TeamViewer permite sessões interativas com partilha de ecrã, transferência de ficheiros, controlo total do sistema e comunicação entre utilizadores.

Embora seja uma ferramenta legítima, o seu **potencial de abuso por Threat Agents** é significativo. É frequentemente utilizada por atacantes para manter acesso persistente, transferir dados ou interagir com a máquina vítima através de GUI, tal como acontece com o AnyDesk.

## **Identificadores de Sessão**

Cada cliente TeamViewer possui um **ID único de sessão** (9 dígitos), atribuído automaticamente pela aplicação. Este ID é utilizado em conjunto com uma password (temporária ou persistente) para estabelecer ligações remotas.

- Exemplo de ID: `987 654 321`
- Passwords podem ser:
    
    - Temporárias (mudam a cada reinício)

    - Definidas manualmente (para acesso persistente)

## **Cenários Comuns de Abuso**

- **Persistência sem instalação visível**: TeamViewer pode correr em modo "unattended access" com execução silenciosa.
    
- **Transferência de ficheiros** sem deixar logs explícitos no Windows.
    
- **Execução sem ícones visíveis na bandeja do sistema**, quando usado com argumentos específicos.
    
- **Abuso de versões portáteis** (standalone `.exe`), sem necessidade de instalação.
    


## **Artefactos de Interesse no Endpoint**

### **1. Caminhos e binários comuns**

- `C:\Program Files (x86)\TeamViewer\TeamViewer.exe`
    
- `%APPDATA%\TeamViewer\`
    
- `%TEMP%`, `%Downloads%` (em casos de execução portátil)
    

### **2. Ficheiros de Log**

- `TeamViewerXX_Logfile.log` (onde XX é a versão)
    
- `Connections_incoming.txt`  
    Contém informações sobre sessões estabelecidas (ID, IP remoto, hora).
    

### **3. Registos no registo do Windows**

- `HKLM\SOFTWARE\WOW6432Node\TeamViewer`
    
- `HKCU\Software\TeamViewer`
    

Podem conter informações sobre:

- ID de cliente
    
- Última ligação
    
- Passwords guardadas (obfuscadas)
    
- Configuração de _unattended access_
    

## **Indicadores Forenses e Táticas de Hunting**

### **Entradas de Log a Monitorizar**

- `Incoming connection established`
    
- `Remote control started`
    
- `File transfer started`
    
- `Authentication successful`
    

### **Eventos anómalos a procurar**

- Execução de `TeamViewer.exe` a partir de diretórios não padrão (Downloads, TEMP).
    
- Execução sem janelas visíveis (`/S` ou `/quiet`).
    
- Comunicação de saída com domínios conhecidos da TeamViewer:
    
    - `*.teamviewer.com`
        
    - `*.tvcdn.de`
        
- Criação de tarefas agendadas, serviços ou chaves de run com referência a TeamViewer.


# **Deteção e Análise de Atividade Suspeita com TeamViewer**

## **Localização dos Ficheiros de Log**

Durante uma análise forense ou de threat hunting, os seguintes ficheiros de log devem ser recolhidos e analisados:

- `C:\Program Files\TeamViewer\TeamViewer15_Logfile.log`
    
- `C:\Users\<Username>\AppData\Roaming\TeamViewer\Connections.txt`
    
- `C:\Program Files\TeamViewer\Connections_incoming.txt`
    

---

## **1. TeamViewer15_Logfile.log**

Este ficheiro contém **informação detalhada e verbosa** sobre as sessões, incluindo:

### **Entradas-Chave para Análise**

- **Punch received**  
    Indica o IP remoto com o qual foi estabelecida a ligação.  
    → **Utilidade**: Identificar o IP externo do atacante.
    
- **Upload from**  
    Mostra o caminho completo do ficheiro que foi descarregado (download) para o sistema local.  
    → **Utilidade**: Detetar possíveis transferências de ferramentas ou payloads maliciosos.
    
- **Download from**  
    Indica o caminho completo do ficheiro que foi enviado (upload) a partir da máquina da vítima.  
    → **Utilidade**: Identificar potenciais tentativas de **exfiltração de dados**.
    

### **Nota sobre Timestamps**

- Os tempos registados neste log **não estão em UTC**.
    
- Estão no **fuso horário local configurado no sistema** da vítima, pelo que será necessário **converter para UTC** para correlacionar com outros artefactos (como os logs de conexão).
    

---

## **2. Connections.txt e Connections_incoming.txt**

Estes ficheiros registam **as sessões de acesso remoto**, seja como origem ou como destino.

### **Formato dos Logs**

- Contêm os seguintes dados:
    
    - **Timestamp (UTC)**
        
    - **ID de sessão**
        
    - **Estado da sessão** (início e fim)
        

### **Diferença entre os dois ficheiros**

- **Connections.txt**
    
    - Regista sessões **originadas a partir** do dispositivo onde o log está localizado.
        
    - No contexto da vítima, é onde devemos focar.
        
- **Connections_incoming.txt**
    
    - Regista sessões **recebidas no dispositivo** (ex: quando um atacante se liga remotamente à vítima).
        

> Ambos os ficheiros têm estrutura semelhante, mas devem ser analisados com base na direção da ligação. No nosso caso, como estamos a analisar os logs da vítima, o foco principal é o `Connections.txt`.

---

## **Correlação de Dados entre Logs**

Um dos aspetos mais importantes na análise é a **correlação de timestamps entre ficheiros de log diferentes**:

- **TeamViewer15_Logfile.log** regista o IP do atacante e os caminhos dos ficheiros, com tempo local.
    
- **Connections.txt** regista a **hora exata (em UTC)** em que a sessão foi iniciada e terminada.
    

### **Exemplo de correlação prática**

1. Encontramos no `TeamViewer15_Logfile.log` uma entrada como `Punch received: 192.168.1.123` às **15:32:10 (hora local)**.
    
2. Convertendo para UTC, corresponde a **14:32:10 UTC**.
    
3. No `Connections.txt`, vemos uma sessão com:
    
    - **Início**: 2025-06-03 14:32:11 UTC
        
    - **Fim**: 2025-06-03 14:52:40 UTC
        

→ Conclusão: o IP identificado corresponde à sessão remota registada, confirmando a ligação remota e possível uso malicioso.

---

## **Sinalização de Exfiltração**

A evidência de exfiltração pode ser identificada quando:

- O `Download from` no log refere-se a ficheiros sensíveis (ex: documentos, base de dados, passwords).
    
- O timestamp coincide com a sessão remota registada no `Connections.txt`.
    
- O log inclui entradas como `Upload from` imediatamente antes ou depois.