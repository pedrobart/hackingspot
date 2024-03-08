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

Conectividade com sucesso e a captura do tráfego com recurso ao filtro ICMP no wireshark.



