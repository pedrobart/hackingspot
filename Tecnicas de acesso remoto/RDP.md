O **Remote Desktop Protocol (RDP)** é um protocolo proprietário desenvolvido pela Microsoft que permite a um utilizador estabelecer uma sessão gráfica remota com outro computador através de uma ligação de rede. É uma funcionalidade nativa dos sistemas Windows e não requer licenciamento adicional, o que contribui para a sua ampla adoção.

O uso de RDP aumentou significativamente após a pandemia de COVID-19 devido à massificação do **trabalho remoto**, sendo hoje comum tanto em ambientes corporativos como pessoais.

---

## **RDP e Ameaças**

Apesar de ser uma funcionalidade legítima, o RDP é **frequentemente explorado por threat agents** para obter acesso inicial a sistemas corporativos. Porquê?

- É uma funcionalidade **nativa** do Windows.
    
- Pode ser utilizada **sem necessidade de software adicional**.
    
- O acesso pode ser feito **apenas com credenciais válidas**.
    
- Os atacantes podem obter essas credenciais de **leaks na dark web** ou através de brute force/credential stuffing.
    

Uma vez dentro, os atacantes usam o acesso RDP para movimentação lateral, exfiltração de dados, ou instalação de malware, resultando em prejuízos significativos para as organizações.

---

## **Evidência Forense: Sessões RDP**

Quando uma sessão RDP é estabelecida, são deixados diversos vestígios em logs do Windows que podem ser utilizados para deteção, correlação e análise forense.

---

## **1. Logon RDP Bem-Sucedido – Security Log (Event ID 4624)**

- **Fonte**: `Security.evtx`
    
- **Event ID**: `4624`
    
- **Logon Type**: `10` (RemoteInteractive)
    

### **Campos Relevantes**:

- `Subject.UserName`, `TargetUserName`
    
- `Logon Type = 10` → Indica sessão RDP
    
- `Logon Process = User32`
    
- `Authentication Package = Negotiate` ou `Kerberos/NTLM`
    

> Nota: O Security Log contém muito ruído. Filtrar especificamente por `Logon Type 10` ajuda a isolar sessões RDP.

---

## **2. TerminalServices-RemoteConnectionManager Logs**

- **Caminho**:  
    `Applications and Services Logs > Microsoft > Windows > TerminalServices-RemoteConnectionManager > Operational`
    

Estes logs oferecem uma **visão mais clara e direta** das ligações RDP, sem o ruído dos Security Logs.

### **Eventos Relevantes**:

- **Event ID 1149** – _Remote Desktop Services: User authentication succeeded_  
    → Ocorre quando o utilizador é autenticado com sucesso para uma sessão RDP.
![](../anexos/Pasted%20image%2020250603235752.png)

- **Event ID 4624 (Security log)** – Sessão efetivamente iniciada após a autenticação.
    
![](../anexos/Pasted%20image%2020250604000346.png)


Ao analisar o evento **ID 261**, é comum observar múltiplas ocorrências num curto espaço de tempo. Este comportamento é, geralmente, indicativo de **tentativas de brute force**.

Se imediatamente após uma sequência desses eventos for registado um **evento ID 1149**, que indica autenticação RDP bem-sucedida,existe uma **forte probabilidade** de que tenha ocorrido uma tentativa de força bruta com sucesso.

Contudo, é importante destacar o **"provavelmente"**: o evento **ID 261 por si só não representa necessariamente uma tentativa falhada de autenticação**. Pode também estar associado a outras fases do processo de ligação, como negociações de sessão ou tentativas legítimas sem erro.

![](../anexos/Pasted%20image%2020250604000943.png)
## **3. TerminalServices-LocalSessionManager Logs**

- **Caminho**:  
    `Applications and Services Logs > Microsoft > Windows > TerminalServices-LocalSessionManager > Operational`
    

### **Eventos Relevantes**:

- **Event ID 21** – _Remote Desktop Services: Session logon succeeded_
    
- **Event ID 24** – _Remote Desktop Services: Session has been disconnected_
    
- **Event ID 25** – _Remote Desktop Services: Session reconnection succeeded_
    

> Estes eventos ajudam a traçar o **ciclo de vida completo da sessão** (ligação, desconexão, reconexão).

---

## **Quando o Uso de RDP Pode Ser Considerado Malicioso**

Nem todo uso de RDP é malicioso, mas determinados indicadores devem ser considerados **red flags**:

### **Indicadores de Acesso RDP Suspeito**

- Sessões RDP estabelecidas **fora do horário laboral**.
    
- Utilização de **contas de serviço ou administrativas**.
    
- Sessões a partir de **endereços IP não pertencentes à infraestrutura da organização**.
    
- Padrões de **logon falhado seguido de sucesso** (tentativa de brute force).
    
- Sessões associadas a **movimentação lateral**, criação de serviços, ou execução de binários suspeitos.
    
- Sessões RDP para **hosts que não requerem suporte remoto regularmente**.
    
- Sessões iniciadas por contas recentemente criadas ou modificadas.

