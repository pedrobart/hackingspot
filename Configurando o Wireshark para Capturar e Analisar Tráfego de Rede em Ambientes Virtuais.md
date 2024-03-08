**Neste laboratório explorei várias questões relacionadas à configuração e análise de tráfego de rede usando o [wireshark](https://www.wireshark.org/) num ambiente de laboratório virtual. Comecei com a configuração básica das máquinas virtuais no [VirtualBox](https://www.virtualbox.org/), incluindo a configuração das interfaces de rede e a definição de endereços IP  para garantir conectividade entre as máquinas. As máquinas utilizadas foram: [Kioptrix](https://www.vulnhub.com/entry/kioptrix-level-1-1,22/) , [Kali Linux](https://www.kali.org/) , [Linux Mint](https://linuxmint.com/).**

**Foi também de importância  habilitar o encaminhamento de pacotes no Kali Linux para permitir que ele atue como gateway para as outras máquinas na rede. Isso permitiu que o Kali Linux roteasse o tráfego entre as máquinas virtuais.**

**Explorei também a diferença entre tráfego HTTP e HTTPS e como filtrar e visualizar esses diferentes tipos de tráfego no [wireshark](https://www.wireshark.org/).**

**Este tipo de laboratórios é essencial para praticar e ganhar experiência para no futuro poder solucionar problemas problemas comuns que podem surgir durante a configuração e análise de tráfego de rede, como configuração de rotas, problemas de roteamento, configuração incorreta de interfaces de rede, e a importância do modo promíscuo para capturar todo o tráfego da rede.**

**Finalmente, abordei questões específicas, como a validação da existência de serviços SSH e Telnet na máquina, a instalação de serviços, a análise de fluxos de dados de conexões Telnet e SSH, e a configuração de serviços em máquinas Linux Mint.**

**Abaixo irei mostrar  passo a passo para configurar, capturar e analisar o tráfego de rede em ambientes virtuais, utilizando ferramentas como o Wireshark e outras técnicas de diagnóstico de rede.** 


**![Screenshot 2024-03-08 035141](https://github.com/pedrobart/hackingspot/assets/87336174/ab740aea-7b78-4422-8d9c-2a1e90fcb8f5)**



# **Garantir conectividade** 

**![Screenshot 2024-03-05 025641](https://github.com/pedrobart/hackingspot/assets/87336174/3026c905-8879-4dd8-8c5b-bda9c31a322f)**



**Após  confirmar com recurso ao comando [PING](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ping),  é possível confirmar conexão entre a maquina Kioptrix com o Kali linux, e capturar o tráfego com o filtro [ICMP](https://networklessons.com/cisco/ccie-routing-switching-written/icmp-internet-control-message-protocol) no wireshark.**



**Irei fazer o mesmo processo mas com a máquina Linux Mint.****

![Screenshot 2024-03-05 032439](https://github.com/pedrobart/hackingspot/assets/87336174/15051e44-007f-4b36-9e24-6b046335e355)

**Conectividade com sucesso e a captura do tráfego com recurso ao filtro ICMP no wireshark.**



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
**O FTP geralmente transmite dados em texto claro, especialmente durante a fase de autenticação e troca de comandos entre o cliente e o servidor FTP. Isso significa que os comandos e respostas FTP são enviados como texto simples, o que torna possível visualizá-los sem decodificação adicional, o quê não é recomendado pois compromete a confidencialidade, integridade dos dados,**
**tornando-os facilmente visíveis para qualquer pessoa que esteja capturando o tráfego.**


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


**Após e instalação e configuração acessei através do Kali Linux ao serviço FTP, fiz o login e utilizei o comando whoami  e mkdir hacked(que cria uma pasta com o nome hacked no ambiente de trabalho do linux mint)**

**Após e instalação e configuração acessei através do Kali Linux ao serviço FTP, fiz o login e utilizei o comando whoami  e mkdir hacked.**

**![Screenshot 2024-03-07 035452](https://github.com/pedrobart/hackingspot/assets/87336174/a9809a47-0513-4a41-9274-efe9e7c17d9b)**

**Abaixo podemos ver o conteúdo do pacote e ver em texto clear os comandos executados na shell entre as duas máquinas, mais uma vez a falta de encriptação.**

**![Screenshot 2024-03-07 035859](https://github.com/pedrobart/hackingspot/assets/87336174/ba8cedd0-ce83-45e8-908f-bb4265b329ac)****

Instalar ssh
```bash
sudo apt install openssh-server
```
