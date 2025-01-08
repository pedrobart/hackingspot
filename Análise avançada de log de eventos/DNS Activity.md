O DNS é uma parte crítica das comunicações de rede e às vezes é considerado a lista telefônica da Internet. 

Antes de estabelecer conexões por meio de protocolos como HTTP(S), SMTP, etc., a maioria dos softwares de rede, incluindo malware, depende do DNS para resolver domínios para endereços IP. 

Portanto, os logs de DNS contêm registos de DNS mais abrangentes, não apenas tráfego HTTP(S), mas também registros de domínios acedidos ​​por endpoints no ambiente, tornando o DNS uma fonte de log altamente benéfica para os defensores.

Além disso, o DNS é acessível em todos os ambientes empresariais, destacando a dependência da rede no DNS. 

Embora alguns dos segmentos de rede mais restritos neguem tráfego HTTP(S), os endpoints ainda podem resolver domínios, fornecendo uma conexão direta ou indireta com a Internet. 

Este utilitário torna o DNS um protocolo tentador para indivíduos mal-intencionados para tunelamento de comunicações para comando e controle (C2), infiltração de dados e exfiltração de dados - conhecido como tunelamento de DNS. 

O registo de DNS é crítico para identificar esse tipo de atividade maliciosa, enfatizando ainda mais o seu valor como uma fonte de registo essencial para todos os threat hunters e pessoal autorizado.

## Ativar o registo de DNS

Para registrar consultas DNS, podemos habilitar 'DNS Client Events' no Event Viewer. 

Abrir o Event Viewer e ir para 'Applications and Services Logs > Microsoft > Windows > DNS Client Events/Operational', clicar com o botão direito e selecionar 'Enable Log'. 

No exemplo abaixo, podemos ver  "Disable log" porque o log já está ativado. Se estiver desativado, veriamos a opção Enable Log no mesmo local.


![](../anexos/Pasted%20image%2020241203194313.png)

## Análise

O primeiro ID de evento em que estamos interessados ​​é o ID de evento 3006. Vamos filtrar pelo event ID:

![](../anexos/Pasted%20image%2020241203194424.png)



![](../anexos/Pasted%20image%2020241203194454.png)



![](../anexos/Pasted%20image%2020241203194805.png)Aqui podemos ver que uma consulta DNS foi feita para o domínio "sharepoint.com".

O próximo ID de evento que analisaremos é o ID de evento 3010. Primeiro, filtramos por este ID de evento:

![](../anexos/Pasted%20image%2020241203195132.png)



Aqui podemos ver que esse ID de evento indica que o SERVIDOR DNS 192.168.1.18 (serviço de servidor DNS da minha rede interna) enviou uma consulta ao servidor de nomes "yandex.com". 

Podemos usar este ID de evento para validar ainda mais que uma consulta foi realmente enviada ao servidor de destino.

O último ID de evento em que estamos interessados ​​é o ID de evento 3011:

![](../anexos/Pasted%20image%2020241203195310.png)

Este resultado indica que uma resposta foi recebida do servidor de domínio 'yandex.com'.

Podemos usar estes IDs de eventos para encontrar o domínio suspeito/malicioso próximo ao momento da atividade maliciosa. 

Suponhamos  que encontramos evidências de um stager C2 por meio de outros artefatos, podemos procurar estes IDs de eventos próximo ao momento de outros indicadores de ataque para encontrar possíveis domínios maliciosos.

