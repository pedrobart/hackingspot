**Neste laboratório explorei várias questões relacionadas à configuração e análise de tráfego de rede usando o [wireshark](https://www.wireshark.org/) num ambiente de laboratório virtual. Comecei com a configuração básica das máquinas virtuais no [VirtualBox](https://www.virtualbox.org/), incluindo a configuração das interfaces de rede e a definição de endereços IP  para garantir conectividade entre as máquinas. As máquinas utilizadas foram: [Kioptrix](https://www.vulnhub.com/entry/kioptrix-level-1-1,22/) , [Kali Linux](https://www.kali.org/) , [Linux Mint](https://linuxmint.com/).**

**Foi também de importância  habilitar o encaminhamento de pacotes no Kali Linux para permitir que ele atue como gateway para as outras máquinas na rede. Isso permitiu que o Kali Linux roteasse o tráfego entre as máquinas virtuais.**

**Explorei também a diferença entre tráfego HTTP e HTTPS e como filtrar e visualizar esses diferentes tipos de tráfego no [wireshark](https://www.wireshark.org/).**

**Este tipo de laboratórios é essencial para praticar e ganhar experiência para no futuro poder solucionar problemas problemas comuns que podem surgir durante a configuração e análise de tráfego de rede, como configuração de rotas, problemas de roteamento, configuração incorreta de interfaces de rede, e a importância do modo promíscuo para capturar todo o tráfego da rede.**

**Finalmente, abordei questões específicas, como a validação da existência de serviços SSH e Telnet na máquina, a instalação de serviços, a análise de fluxos de dados de conexões Telnet e SSH, e a configuração de serviços em máquinas Linux Mint.**

**Abaixo irei mostrar  passo a passo para configurar, capturar e analisar o tráfego de rede em ambientes virtuais, utilizando ferramentas como o Wireshark e outras técnicas de diagnóstico de rede.** 


![Screenshot 2024-03-08 035141](https://github.com/pedrobart/hackingspot/assets/87336174/ab740aea-7b78-4422-8d9c-2a1e90fcb8f5)



# Garantir conectividade 

![[Screenshot 2024-03-05 025641.png]]


Após  confirmar com recurso ao comando PING 