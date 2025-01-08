# Teste de penetração em ambiente virtualizado + Sniffing com Wireshark

**Neste laboratório explorei várias questões relacionadas à configuração e análise de tráfego de rede usando o [wireshark](https://www.wireshark.org/) num ambiente de laboratório virtual. Comecei com a configuração básica das máquinas virtuais no [VirtualBox](https://www.virtualbox.org/), incluindo a configuração das interfaces de rede e a definição de endereços IP  para garantir conectividade entre as máquinas. As máquinas utilizadas foram: [Kioptrix](https://www.vulnhub.com/entry/kioptrix-level-1-1,22/) , [Kali Linux](https://www.kali.org/) , [Linux Mint](https://linuxmint.com/).**

**Kioptrix é uma série de máquinas virtuais vulneráveis projetadas para fins educacionais e práticos em testes de penetração, aprendizagem de segurança cibernética e prática de habilidades de hacking ético. Essas máquinas virtuais foram criadas pelo autor loneferret e estão disponíveis publicamente para download e uso.**

**Cada máquina virtual Kioptrix é projetada com várias vulnerabilidades comuns que são encontradas em ambientes reais. Os utilizadores podem explorar essas vulnerabilidades e praticar técnicas de exploração, análise de vulnerabilidades, pós-exploração e resolução de problemas de segurança.**

**A série Kioptrix é amplamente utilizada por estudantes, profissionais de segurança cibernética, pesquisadores e entusiastas de hacking ético para aprimorar as suas habilidades e entender melhor os princípios de segurança de sistemas. É importante observar que o uso do Kioptrix deve ser estritamente para fins educacionais e legais, e não para atividades maliciosas.**

**Foi também de importância  ativar o redirecionamento de pacotes no Kali Linux para permitir que ele atue como gateway para as outras máquinas na rede. Isso permitiu que o Kali Linux roteasse o tráfego entre as máquinas virtuais.**

**Explorei também a diferença entre tráfego HTTP e HTTPS e como filtrar e visualizar esses diferentes tipos de tráfego no [wireshark](https://www.wireshark.org/).**

**Este tipo de laboratórios é essencial para praticar e ganhar experiência para no futuro poder solucionar problemas comuns que podem surgir durante a configuração e análise de tráfego de rede, como configuração de rotas, problemas de roteamento, configuração incorreta de interfaces de rede, e a importância do modo promíscuo para capturar todo o tráfego da rede.**

**Finalmente, abordei questões específicas, como a validação da existência de serviços SSH e Telnet na máquina, a instalação de serviços, a análise de fluxos de dados de conexões Telnet e SSH, e a configuração de serviços numa máquina com o sistema Linux Mint.**

**Abaixo irei mostrar  passo a passo para configurar, capturar e analisar o tráfego de rede em ambientes virtuais, utilizando ferramentas como o Wireshark e outras técnicas de diagnóstico de rede.** 


**![Screenshot 2024-03-08 035141](https://github.com/pedrobart/hackingspot/assets/87336174/ab740aea-7b78-4422-8d9c-2a1e90fcb8f5)**


***
# **Garantir conectividade** 

**![Screenshot 2024-03-05 025641](https://github.com/pedrobart/hackingspot/assets/87336174/3026c905-8879-4dd8-8c5b-bda9c31a322f)**


**Após  confirmar com recurso ao comando [PING](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ping),  é possível confirmar conexão entre a maquina Kioptrix com o Kali linux, e capturar o tráfego com o filtro [ICMP](https://networklessons.com/cisco/ccie-routing-switching-written/icmp-internet-control-message-protocol) no wireshark.**


**Irei fazer o mesmo processo mas com a máquina Linux Mint.****

![Screenshot 2024-03-05 032439](https://github.com/pedrobart/hackingspot/assets/87336174/15051e44-007f-4b36-9e24-6b046335e355)

**Conectividade com sucesso e a captura do tráfego com recurso ao filtro ICMP no wireshark.**

Habilitar o Port Forwarding no kali linux
```bash
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Ataque de [ArpSpoof](https://www.imperva.com/learn/application-security/arp-spoofing/)
Executar no terminal do kali linux o seguinte comando
```bash
arpspoof -i eth0 -t IP_KALI IP_ALVO
```


**Instalar no Linux Mint o serviço FTP**
```bash
sudo apt install vsftpd
```
**Iniciar o serviço** 
```bash
sudo systemctl start vsftpd 
sudo systemctl enable vsftpd
```

**Criar um utilizador FTP**

```bash
sudo useradd -m [username]
sudo passwd [username]
```

**Caso seja necessário permitir o tráfego na firewall**
```bash
sudo ufw allow 20/tcp
sudo ufw allow 21/tcp
```
**Reiniciar a firewall** 
```bash
sudo ufw reload
```

**Na imagem a seguir, através da minha máquina Host irei conectar-me ao servidor FTP do Linux Mint criado anteriormente, com o programa [Filezilla](https://filezilla-project.org/).**
**E podemos ver o tráfego de dados FTP no wireshark através do sistema kali linux.** 
**As credenciais de login que a maquina host (192.168.1.89) utilizou para se conectar ao servidor FTP (Linux Mint - 192.168.1.99)**

**![Screenshot 2024-03-07 032846](https://github.com/pedrobart/hackingspot/assets/87336174/47ddff13-c96b-4849-8266-1f25bc35cf71)**

**No Wireshark, o tráfego FTP (File Transfer Protocol) é frequentemente visível em texto claro devido à maneira como o protocolo FTP opera.** 
**O FTP geralmente transmite dados em texto claro, especialmente durante a fase de autenticação e troca de comandos entre o cliente e o servidor FTP. Isso significa que os comandos e respostas FTP são enviados como texto simples, o que torna possível visualizá-los sem decodificação adicional, o quê não é recomendado pois compromete a confidencialidade e a integridade dos dados,**
**tornando-os facilmente visíveis para qualquer pessoa que esteja a capturar o tráfego.**


**Instalar o serviço Telnet**

```bash
sudo apt install telnetd
```
**Iniciar o serviço Telnet**
```bash
sudo systemctl status inetd
```
**Caso seja necessário permitir tráfego na firewall**
```bash
sudo ufw allow 23/tcp
```
**Reiniciar a firewall**
```bash
sudo ufw reload
```



**Após a instalação e configuração acessei através do Kali Linux ao serviço FTP, fiz o login e utilizei o comando whoami  e mkdir hacked.**

**![Screenshot 2024-03-07 035452](https://github.com/pedrobart/hackingspot/assets/87336174/a9809a47-0513-4a41-9274-efe9e7c17d9b)**

**Abaixo podemos ver o conteúdo do pacote e ver em texto clear os comandos executados na shell entre as duas máquinas, mais uma vez a falta de encriptação.**

**![Screenshot 2024-03-07 035859](https://github.com/pedrobart/hackingspot/assets/87336174/ba8cedd0-ce83-45e8-908f-bb4265b329ac)****

**Instalar ssh**
```bash
sudo apt install openssh-server
```
**Caso seja necessário permitir na firewall**
```bash
sudo ufw allow ssh
```
**Ativar o serviço ssh**
```bash
sudo service ssh status
```

**O mesmo comando que foi feito para Telnet, foi feito com SSH:**

**![Screenshot 2024-03-07 040944](https://github.com/pedrobart/hackingspot/assets/87336174/dce773aa-d3ae-46b9-a1d1-2e82c50f6ad2)**

**Como podemos ver na imagem acima, o conteúdo do pacote encontra-se encriptado e não é possível extrair qualquer dado.** 
****
**Irei entrar num website com protocolo HTTP para posteriormente mostrar a captura de tráfego:**
**![Screenshot 2024-03-07 043504](https://github.com/pedrobart/hackingspot/assets/87336174/ba7b3bcb-7d4e-4050-9688-40af9bb79fdc)**

**Ao aceder um website com o protocolo http podemos ver na imagem abaixo o tráfego HTTP no wireshark**:

**![Screenshot 2024-03-07 043544](https://github.com/pedrobart/hackingspot/assets/87336174/e9c7cc46-f5f1-45d1-a03b-c150423ecd74)**

**Ao analisar o pacote é possível ver em clear text. Veremos abaixo a diferença no protocolo HTTPS.**

**![Screenshot 2024-03-07 044112](https://github.com/pedrobart/hackingspot/assets/87336174/82b2fdb6-1306-4930-8947-366642b8a52e)**

**Da mesma forma vista anteriormente no exemplo do SSH, o pacote encontra-se encriptado e não dá  para extrair qualquer dado.**

**A importância da criptografia nos serviços de rede é fundamental para garantir a segurança, privacidade e integridade dos dados transmitidos.**

- **A criptografia protege os dados contra acesso não autorizado durante a transmissão. Ela garante que apenas os destinatários autorizados possam ler e interpretar as informações transmitidas.**
- **A criptografia ajuda a garantir que os dados não tenham sido alterados ou corrompidos durante a transmissão. 
- Ela usa algoritmos de hashing e assinaturas digitais para verificar se os dados permanecem intactos durante o trânsito.**

**A criptografia pode ser usada para autenticar as partes envolvidas na comunicação. Os certificados digitais e os protocolos de autenticação garantem que as partes sejam quem afirmam ser, reduzindo o risco de ataques de spoofing e phishing.**
**Sem criptografia, os dados transmitidos pela rede podem ser facilmente interceptados e lidos por atores maliciosos. A criptografia protege contra esse tipo de interceptação, garantindo que apenas as partes autorizadas tenham acesso aos dados.**

**É essencial implementar protocolos e tecnologias de criptografia adequados em todos os serviços de rede para garantir a segurança e a privacidade dos dados transmitidos.**
***
# Teste de penetração na maquina Kioptrix level 1

**Existe algumas maneiras de conseguir acesso root nesta máquina, vou ser rápido e objetivo.** 

**Comecei por utilizar o comando**
```bash
arp-scan -l
```
**O comando `arp-scan -l` é utilizado para listar as informações sobre dispositivos conectados à rede local por meio do protocolo [ARP](https://www.fortinet.com/br/resources/cyberglossary/what-is-arp) (Address Resolution Protocol).** 

**![Screenshot 2024-03-08 064320](https://github.com/pedrobart/hackingspot/assets/87336174/112e3f89-4010-49ae-b7c3-efd73bd4c538)**

**Agora que tenho o IP da maquina vou utilizar as seguintes ferramentas: [NMAP](https://nmap.org/), [enum4linux](https://www.kali.org/tools/enum4linux/), [smbclient](https://www.samba.org/samba/docs/current/man-html/smbclient.1.html).**


**O Nmap é uma poderosa ferramenta de código aberto usada para exploração de rede, auditoria de segurança e descoberta de dispositivos em redes de computadores. O seu nome é uma abreviação de "Network Mapper". O Nmap é amplamente utilizado por administradores de rede, profissionais de segurança cibernética, pesquisadores e hackers éticos para examinar redes, identificar hosts, serviços em execução, sistemas operacionais e detectar possíveis vulnerabilidades.**

```bash
sudo nmap -A -p- -T4 ip_alvo
```

**output:**
```python
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-03-08 06:52 WET
Nmap scan report for 192.168.1.101
Host is up (0.00055s latency).
Not shown: 65529 closed tcp ports (reset)
PORT      STATE SERVICE     VERSION
22/tcp    open  ssh         OpenSSH 2.9p2 (protocol 1.99)
|_sshv1: Server supports SSHv1
| ssh-hostkey: 
|   1024 b8:74:6c:db:fd:8b:e6:66:e9:2a:2b:df:5e:6f:64:86 (RSA1)
|   1024 8f:8e:5b:81:ed:21:ab:c1:80:e1:57:a3:3c:85:c4:71 (DSA)
|_  1024 ed:4e:a9:4a:06:14:ff:15:14:ce:da:3a:80:db:e2:81 (RSA)
80/tcp    open  http        Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)
|_http-title: Test Page for the Apache Web Server on Red Hat Linux
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
111/tcp   open  rpcbind     2 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2            111/tcp   rpcbind
|   100000  2            111/udp   rpcbind
|   100024  1          32768/tcp   status
|_  100024  1          32768/udp   status
139/tcp   open  netbios-ssn Samba smbd (workgroup: oMYGROUP)
443/tcp   open  ssl/https   Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_RC4_64_WITH_MD5
|_    SSL2_DES_192_EDE3_CBC_WITH_MD5
|_ssl-date: 2024-03-08T11:53:07+00:00; +5h00m00s from scanner time.
| ssl-cert: Subject: commonName=localhost.localdomain/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--
| Not valid before: 2009-09-26T09:32:06
|_Not valid after:  2010-09-26T09:32:06
|_http-title: 400 Bad Request
32768/tcp open  status      1 (RPC #100024)
MAC Address: 08:00:27:A2:FC:6B (Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Linux 2.4.X
OS CPE: cpe:/o:linux:linux_kernel:2.4
OS details: Linux 2.4.9 - 2.4.18 (likely embedded)
Network Distance: 1 hop

Host script results:
|_clock-skew: 4h59m59s
|_smb2-time: Protocol negotiation failed (SMB2)
|_nbstat: NetBIOS name: KIOPTRIX, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)

TRACEROUTE
HOP RTT     ADDRESS
1   0.55 ms 192.168.1.101

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 37.44 seconds
```
**Possível vetor de ataque:**
```bash
139/tcp   open  netbios-ssn Samba smbd (workgroup: oMYGROUP)
```


**Noutro Terminal:**
```bash
enum4linux -a 192.168.1.101
```

**Resultado:**
**![Screenshot 2024-03-08 070503](https://github.com/pedrobart/hackingspot/assets/87336174/ec9ba70f-5fc5-448d-b9d7-ce1696170da8)**

**Para identificar qual versão do Samba está a ser executada no Kioptrix, podemos usar um módulo específico no Framework Metasploit. O módulo auxiliary/scanner/smb/smb_version. Podemos procurá-lo no Metasploit conforme mostrado abaixo:**
**![Screenshot 2024-03-08 071124](https://github.com/pedrobart/hackingspot/assets/87336174/c5aea9f4-a453-4c86-9c06-e8c5e265e8cd)**

**Para selecionar o Modulo (modulo numero 12)**
```bash
use 12 
```
**E mostrar as opções do módulo** 
```bash
show options
```

**![Screenshot 2024-03-08 071347](https://github.com/pedrobart/hackingspot/assets/87336174/f622cb0c-a756-4afa-bd24-21902a661c6c)**

```bash
set RHOST IP_KIOPTRIX
```
**![Screenshot 2024-03-08 071410](https://github.com/pedrobart/hackingspot/assets/87336174/16b98990-a87e-4481-829c-f96a022b2b52)**

**Executar o módulo de reconhecimento da versão do Samba**
```python
run
```

**![Screenshot 2024-03-08 071418](https://github.com/pedrobart/hackingspot/assets/87336174/61dc28e5-0aab-4d86-9cf9-afd08f62b75c)**

**Agora que sabemos a versão do Samba vamos procurar por [exploits](https://www.bitdefender.com.br/consumer/support/answer/27646/)**
```python
searchsploit Samba 2.2.1a
```
**![Screenshot 2024-03-08 071505](https://github.com/pedrobart/hackingspot/assets/87336174/76f5ac77-ea08-4c8d-83bd-3be665a3bafc)**



**Vamos fazer download do exploit acima**

**![Screenshot 2024-03-08 071648](https://github.com/pedrobart/hackingspot/assets/87336174/d79a6787-42c4-4a83-9646-ea5782c377f9)**


**O exploit está na linguagem C e temos de compilar para o podemos executar**
```c
gcc -o Samba 10.c
```


**Samba é o nome que vamos dar ao ficheiro:**
**![Screenshot 2024-03-08 071735](https://github.com/pedrobart/hackingspot/assets/87336174/f8e221ce-7816-49f4-80bc-7e0f14ce383c)**


**Manual das opções do exploit:**

**![Screenshot 2024-03-08 071825](https://github.com/pedrobart/hackingspot/assets/87336174/50ebfd2f-2d21-4606-8b52-2e947d4d4d43)**



**Executar o exploit:**

**![Screenshot 2024-03-08 071859](https://github.com/pedrobart/hackingspot/assets/87336174/8354cac6-aa74-43a2-b3e1-70e657df738f)**


**O exploit funcionou, e após o comando 'whoami' temos a resposta que temos permissões 'root' e temos acesso total à máquina.** 

***
# **Fim**

**Este resumo destaca as etapas e técnicas utilizadas para explorar vulnerabilidades, analisar tráfego de rede e comprometer uma máquina num ambiente de laboratório controlado. É importante ressaltar que todas as atividades foram realizadas para fins educacionais e práticos, visando a aprendizagem e o aprimoramento das habilidades em segurança informática e testes de penetração.**






