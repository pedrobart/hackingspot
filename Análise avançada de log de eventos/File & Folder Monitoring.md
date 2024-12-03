Em qualquer organização que use servidores de arquivos para armazenar e partilhar dados, a auditoria é importante para garantir a segurança dos dados. 

A monitorização adequada de todos os servidores de arquivo no domínio pode ajudar a detetar eventos indesejados ou potencialmente prejudiciais, incluindo acessos a arquivos e eventos de leitura em arquivos que contêm dados confidenciais.

Esses eventos podem garantir mecanismos de defesa adequados para evitar eventos maliciosos, como exfiltração de dados confidenciais.

  

## Configurando a auditoria de arquivos/pastas

Para auditar estes eventos, vamos para Computer Configuration > Windows Settings > Security Settings > Local Policies > Audit Policy > Audit Object Access. Ativar eventos de sucesso e falha.

![](../anexos/Pasted%20image%2020241203200625.png)


Agora podemos ir até qualquer pasta ou arquivo que queremos monitorizar e configurá-lo para ser monitorizado.

![](../anexos/Pasted%20image%2020241203200739.png)

Vamos para “Propriedades” da pasta e selecionamos a aba “Segurança”. Depois vamos para a aba “Avançado”.

![](../anexos/Pasted%20image%2020241203200827.png)

Agora vamos até a aba “Auditoria” e clicamos em “Adicionar”.

![](../anexos/Pasted%20image%2020241203200857.png)

  
Esta ação abre a interface de “Auditoria”, aqui clicamos em “Selecionar um principal” e aqui podemos selecionar qualquer user ou grupo específico cujas atividades queremos monitorizar.

![](../anexos/Pasted%20image%2020241203200955.png)

Queremos monitorizar qualquer atividade de qualquer pessoa, então inserimos “Todos” como nome do objeto.

![](../anexos/Pasted%20image%2020241203201029.png)


Ao clicar em OK, veremos o seguinte:

![](../anexos/Pasted%20image%2020241203201058.png)

Aqui, selecionamos o menu suspenso “Tipo” e definimos  como “Tudo”, o que auditará todas as atividades, tanto as bem-sucedidas quanto as malsucedidas.

No menu suspenso "Aplica-se a", podemos selecionar o "scope" da nossa monitorização.
Aqui, queremos monitorizar a pasta, todas as subpastas nela e todos os arquivos também, então deixamos essa opção selecionada por padrão.

![](../anexos/Pasted%20image%2020241203201253.png)

Em "Permissões básicas", selecionamos "Controlo total". Depois clicamos em OK.

## Análise

Agora vamos monitorizar essa atividade. 

No momento, precisamos focar nos IDs de Evento 4656 e 4663. 

Há um arquivo no nosso diretório teste e agora vamos acede-lo.

Começaremos por analisar o ID do evento 4656. Esse ID do evento é registado quando o objeto é solicitado.

![](../anexos/Pasted%20image%2020241203214513.png)

Temos as informações da conta do user, ou seja, qual conta de user acedeu o objeto alvo que criou o evento. 
A parte "Object" mostra o "Object Name" (o que está sendo acedido e a  fazer com que o log seja gravado). 
Neste exemplo, o objeto é um arquivo chamado 'ficheiro.txt' na pasta 'data sensivel'.

Por fim, temos process information, que mostra o processo que está a ser acedido e o objeto em questão. Neste exemplo, é "explorer.exe" porque abrimos o local do arquivo por meio do "explorer.exe".

O outro ID de evento, ID de evento 4663, é gerado quando o acesso ao objeto de destino é bem-sucedido ou falhado. 

Por outras palavras, a presença do ID de evento 4656 por si só não indica que o acesso ocorreu, mas se virmos evidências de 4663 como um sucesso de auditoria, isso significa que ele realmente foi bem-sucedido.

![](../anexos/Pasted%20image%2020241203214733.png)

Aqui podemos ver as mesmas informações de antes, a única diferença é que este evento confirma que o acesso foi realmente bem-sucedido.

Também podemos confirmar que o ID do evento 4663 significa que o objeto foi acedido ou falhou ao olhar as palavras-chave. Se disser 'auditoria bem-sucedida', significa que o objeto foi acedido, se disser 'auditoria falhou', significa que o objeto teve o acesso negado.

Observando mais de perto o processo de acesso ao objeto, vemos outro exemplo nos eventos de acompanhamento em que o mesmo acesso ao arquivo foi solicitado, mas pelo processo do bloco de notas e não pelo explorer.exe.

![](../anexos/Pasted%20image%2020241203215031.png)

Esta telemetria é útil em casos em que o processo que acede aos arquivos é suspeito, como cmd, PowerShell, e pode indicar o uso de scripts, etc.

