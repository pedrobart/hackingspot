A análise de conexão de rede pode ajudara monitorizar o tráfego de rede, identificar conexões suspeitas, rastrear o comportamento da aplicação e investigar incidentes de segurança. 

Por exemplo, se tivermos recursos de registo para registar informações de conexão de rede junto com o processo que as iniciou, podemos facilmente correlacionar e executar análise contextual para identificar atividade de rede suspeita/maliciosa somente a partir desses registos, caso um invasor tenha sido executado no sistema.

  

## Configurar Logs de Eventos de Auditoria

Para habilitar a auditoria dos logs da Plataforma de Filtragem do Windows, vamos para “Editor de Política de Grupo Local > Configuração do Computador > Configurações do Windows > Configurações de Segurança > Configuração Avançada da Política de Auditoria > Políticas de Auditoria do Sistema > Acesso a Objetos > Conexão da Plataforma de Filtragem de Auditoria”.

![](../anexos/Pasted%20image%2020241203225309.png)



![](../anexos/Pasted%20image%2020241203225326.png)

Isto agora registará a conexão de rede, incluindo o nome do processo.

## Análise

 Começaremos com o Event ID 5156 em Security Logs.
 
![](../anexos/Pasted%20image%2020241203225508.png)


Aqui podemos ver que uma conexão de saída para 13.235.67.159 na porta 4444 foi feita por um processo do PowerShell.

 O PowerShell fazer uma conexão é suspeito por si só, mas neste caso, a porta é suspeita, pois a porta 4444 é amplamente usada pelo meterpreter.

Dividindo os campos neste evento:

**Nome do aplicação** : O processo que está a fazer a conexão.
**Direção** : Saída/entrada diz se a conexão é interna ou externa.
**Endereço de origem e porta** : IP e porta do sistema local.
**Endereço e porta de destino** : o IP remoto e a porta para os quais a conexão foi feita.


Podemos usar essas informações valiosas para identificar conexões de rede maliciosas, como atividade de comando e controlo, atividade de infostealer ou tráfego de botnet. 

Devemos sempre procurar por processos estranhos/maliciosos/benignos a fazer a conexão. 

Por outro lado, também devemos procurar o endereço IP remoto em feeds de inteligência de ameaças, como o Virustotal, para encontrar a reputação do endereço IP. 

Neste exemplo, é apenas uma VPC, mas, na realidade, pode ser parte da infraestrutura de um invasor.

