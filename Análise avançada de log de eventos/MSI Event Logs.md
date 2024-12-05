MSI, anteriormente chamado de Microsoft Installer, é um formato de pacote de instalação do Windows. 

É utilizado para instalar e implementar aplicações ou pacotes necessários do Windows nas máquinas dos utilizadores finais. 

MSI é um método de instalação padronizado que simplifica o processo de instalação para os utilizadores.

Instalar arquivos MSI é simples e geralmente requer pouca intervenção do utilizador. 

MSI é geralmente similar a executar um executável.

Pode ser difícil distinguir entre instaladores legítimos e arquivos MSI maliciosos. 

Os agentes de ameaças frequentemente enganam as vítimas para "atualizar" o software nas suas máquinas, disfarçando-se como atualizações de software bem conhecidas.

O MSI permite que a conta LocalSystem (NT AUTHORITY\SYSTEM) seja executada, então o acesso não autorizado ao LocalSystem pode comprometer o sistema e levar a mais comprometimento da rede. 

Como o MSI é baseado no armazenamento de estrutura COM, isso permite que os agentes de ameaças armazenem arquivos maliciosos num arquivo MSI e controlem os arquivos que são armazenados com ações personalizadas. 

Essa tecnologia dá aos agentes de ameaças várias opções de padrão de execução para infectar os computadores das vítimas.


## Análise

Analise  dos logs de aplicação nos logs do Windows para encontrar a atividade do instalador MSI.

![](../anexos/Pasted%20image%2020241205185216.png)

Vamos até ao log marcado com uma seta e clicamos em “Filtrar Log Atual”.

![](../anexos/Pasted%20image%2020241205185257.png)

Em seguida, vamos para Event Sourcess e localizamos e selecionamos a fonte 'MsiInstaller'.

![](../anexos/Pasted%20image%2020241205185339.png)

Clicamos em 'OK' e uma lista de todos os eventos relacionados à atividade do MSI será listada.


![](../anexos/Pasted%20image%2020241205185459.png)


O primeiro ID de evento que vamos verificar é o ID de evento 1040.

![](../anexos/Pasted%20image%2020241205185636.png)


O ID do evento 1040 regista sempre que um processo de instalação ou desinstalação de um MSI começa, incluindo detalhes como o caminho completo do MSI e o ID do processo.

O próximo ID de evento principal é o ID de evento 11707. Esse ID de evento, juntamente com o ID de evento 1040, informa se ocorreu uma instalação ou desinstalação.

![](../anexos/Pasted%20image%2020241205185805.png)

  
Este ID de evento indica se a instalação foi validada e o produto foi instalado com sucesso. 

Contém o nome do produto, a versão e o nome do fabricante. É útil em casos em que malware está a tentar ficar stealthy num MSI falso ou MSIs legítimos que estão a ser injetados com código malicioso, por exemplo, como parte de um Supply chain attack.

O código de status indica se foi bem-sucedido ou não. "Um status '0' significa que foi instalado sem erros.

Se quisermos verificar se o produto MSI instalado foi removido, podemos verificar o ID do evento 1034. Muitas vezes, o malware  desinstala-se após concluir a sua missão, como adicionar uma rotina de persistência, um backdoor, etc.



