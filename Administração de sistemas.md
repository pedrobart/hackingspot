# Administração de sistemas

***
### Tópico 1

- **Sistemas Operativos Servidor – Windows Server**
- **Instalação do sistema operativo servidor**
- **Otimização do sistema operativo servidor**
- **Backup e sistemas de proteção contra falhas**
- **Utilizadores – Criação e configuração de contas**
- **Gestão de recursos**
- **Ferramentas de administração**
- **Instalação e configuração de clientes de acordo com a configuração da rede e do servidor**

- **Sistemas Operativos Servidor – plataforma Open Source**
	- **GNU/Linux servidor**

- **Instalação e configuração de um sistema operativo open source**
	- **Particionamento, formatação, opções de instalação**
	- **Instalação de dispositivos e device drivers**
	- **Configurações**
	
 - **Conceitos sobre sistemas operativos**
	- **Kernel, sistemas operativos e distribuições**
	- **Software livre dentro da empresa**
	
- **Múltiplas configurações do sistema**
- **Resolução de problemas**
- **Instalação de serviços e aplicativos**
- **Levantamento das necessidades de utilização e seleção do sistema servidor mais adequado**
***
# Administração de sistemas

- **Um sistema operativo (SO) de plataforma proprietária (por diferenciação de SO de plataforma aberta) é um sistema operativo de código fechado (total ou parcial) geralmente pertencente a uma empresa de software que o produz.**

- **O exemplo mais bem sucedido ao momento é o Microsoft Windows.**

- **Um sistema operativo Servidor (por diferenciação de SO cliente) é um SO direcionado à disponibilização de serviços a dispositivos que irão utilizar/consumir estes serviços.**

- **Como exemplo de serviços disponibilizados temos a partilha e transmissão de ficheiros, serviços de mail, encriptação, certificação de utilizadores, etc.**

***
# Algumas Aplicações para SO Servidores

**SGBD's (Sistemas de Gestão de Base de Dados):**

- [**MySQL**](https://www.mysql.com/)
- **[SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)**
- **[PostgreSQL](https://www.postgresql.org/)**
- **[Oracle](https://www.oracle.com/)**

**Servidores que possuem e manipulam informações numa base de dados.**

![[Pasted image 20240309165917.png]]

***
# Algumas Aplicações para SO Servidores

- **Servidor de Ficheiros – Servidor que armazena ficheiros de diversos utilizadores.**

- **Servidor de Impressão – Servidor responsável por controlar pedidos de impressão de ficheiros dos diversos clientes.**

![[Pasted image 20240309170050.png]]
***
# Algumas Aplicações para SO Servidores

- **Serviços Web (HTTP Servers), como o IIS (Internet Information Services), Apache.**
- **Servidores responsáveis pelo armazenamento de páginas de um determinado site, requisitados pelos clientes através de browsers.**

![[Pasted image 20240309170140.png]]
***
# Algumas Aplicações para SO Servidores

- **Servidores de e-mail, como postfix, Microsoft Exchange Server, Lotus Notes, etc.** 

- **Nem todos eles se limitam a serem meros servidores de e-mail, alguns incorporam calendários, entre outras funcionalidades.**

![[Pasted image 20240309170358.png]]

***

# Algumas Aplicações para SO Servidores

- **Servidores de Fax - Servidor para transmissão e receção automatizada de fax pela Internet, disponibilizando também a capacidade de enviar, receber e distribuir fax em todas as estações da rede.**
![[Pasted image 20240309170453.png]]

***
# Algumas Aplicações para SO Servidores

- **Servidor DNS – Servidores responsáveis pela conversão de endereços de sites em endereços IP e vice-versa.**
![[Pasted image 20240309170702.png]]

***
# Algumas Aplicações para SO Servidores

- **Servidor Proxy - Servidor que atua como uma cache, armazenando páginas da internet recém visitadas, aumentando a velocidade de carregamento destas páginas ao chamá-las novamente.**

![[Pasted image 20240309170755.png]]

***

# Algumas Aplicações para SO Servidores

- **Servidor FTP - Permite acesso de outros utilizadores a um disco rígido ou servidor. Esse tipo de servidor armazena ficheiros para dar acesso a eles pela internet.**

![[Pasted image 20240309170856.png]]

***
# Algumas Aplicações para SO Servidores

- **Servidor Webmail - servidor para criar e-mails na web.**

![[Pasted image 20240309170951.png]]
***
# Algumas Aplicações para SO Servidores

- **Servidor de Virtualização - permite a criação de máquinas virtuais (servidores isolados no mesmo equipamento) mediante compartilhamento de hardware, aumentando a eficiência energética, sem prejudicar as aplicações e sem risco de conflitos de uma consolidação real.**

![[Pasted image 20240309171911.png]]
***
# Algumas Aplicações para SO Servidores

- **Servidor de sistema operativo - permite compartilhar o sistema operativo de uma máquina com outras, interligadas na mesma rede, sem que essas precisem ter um sistema operativo instalado, nem mesmo um HD próprio.**


![[Pasted image 20240309172009.png]]

***
# Características 

- **==Gestão de múltiplas tarefas para clientes diferentes==**
- **Pode requer grandes capacidades de processamento e memória. 
- **É comum um servidor ser equipado com processadores XEON, 32Gb a 4T de memória e vários discos.**

***
# Características 


| Segurança                                                                                                                                                           | Administração                                                                                                                             | Desempenho                                                                                                                                         | Estabilidade                                           |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| **Utilização de Firewall's devidamente configuradas. Políticas de segurança “apertadas”, como por exemplo necessidade de alterar passwords com regularidade, etc.** | **Utilização de painéis de administração/gestão para as aplicações servidor a correr, muita vezes com acesso remoto por consola ou web.** | **Limitação de recursos por cliente ou aplicação. Alertas para taxas elevadas de processamento. Hardware dedicado e monitorizado constantemente.** | **Aplicações Servidor independentes umas das outras**. |
### Backups

- **Utilização de vários discos em RAID.** 
- **Gestão de sistemas de backup automáticos.**

***

# Proprietário Vs Livre

- **Engane-se quando pensa que todos os Servidores Linux são gratuitos, não confundir gratuito com livre.**

- **Um bom SO Servidor é pago, porque existem nele sistemas/aplicações que são pagas.**

- **Além disso um SO Servidor pago, incluí apoio/assistência, coisa que os gratuitos não incluem.**

- **Pago Vs Free? [Red Hat Enterprise Linux](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux) (RHEL) Vs [CentOS](https://www.centos.org/).**

- **Proprietário Vs Livre? [Windows Server](https://www.microsoft.com/en-us/windows-server) Vs [RHEL](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux).**
***

# Windows Vs Linux

**Nem tudo o que funciona em Windows funciona em Linux e vice-versa, alguns exemplos:**

- **IIS**
- **MS SQL Server**
- **Microsoft Exchange Server**

## Como Escolher? Windows Vs Linux

###### Windows
- **.NET / MS Server's**
- **Instalação do sistema e de aplicações simples**
- **Atualizações feitas pelo sistema da MS (as atualizações são validadas/certificadas).** 
###### Linux
- **Mais barato**
- **Mais moldável (muitos kernels especializados)**
- **Menos updates críticos de segurança**
- **Mais seguro…?**

***
# Windows Server 2016

**Novidades do Windows Server 2016:**

**Adição de camadas de segurança:** 
- **Aumenta a segurança e reduz os riscos através das várias camadas de proteção incorporadas.**

**Novas opções de Implementação:** 
- **Aumenta a disponibilidade e reduz a utilização de recursos com o [Nano Server](https://infob.com.br/microsoft-nano-server-o-guia-completo/).**

**Containers incorporados:** 
- **Aumenta a agilidade dos processos de desenvolvimento e gestão graças aos containers Windows Server e Hyper-V.**

**Armazenamento rentável:**
- **Cria armazenamento definido por software rentável e de elevada disponibilidade, reduzindo simultaneamente os custos.**

**Funcionamento em rede ágil:** 
- **Funcionamento em rede definido por software para automatizar com uma eficiência semelhante à da cloud.**

***
# Windows Server 2019

**Novidades do Windows Server 2019:**

**Redes virtuais criptografadas:** 
- **As redes virtuais ou SDN (Sofware Defined Network) possuem um recurso que fornece uma configuração simples, utilizando criptografia baseada no protocolo DTLS (Datagram Transport Layer Security), oferecendo proteção contra interceptações e tentativas de manipulação do tráfego de rede.**

**Máquinas Virtuais Blindadas (Shielded VMs):** 
- **As VMs Blindadas suportam também máquinas virtuais que estejam a executar sistemas operativos Linux.**

**Windows Admin Center:** 
- **Tem o objetivo de centralizar a administração de vários servidores, facilitando a administração dos ambientes de TI.
- **É possível, por exemplo ter acesso através de um browser a informações como: Visualizador de Eventos, Gerenciador de dispositivos, Gestor de Disco, Acesso Remoto, etc**

**Windows Defender ATP:** 
- **A partir desta versão o Windows Defender Advanced Protection Threat, está incorporado na instalação do Windows Server.**
- **Fornece uma camada de proteção preventiva, que tem como objetivo principal detetar ataques e exploração de vulnerabilidades ao sistema operativo, trazendo a possibilidade de detetar atividades suspeitas ao nível de memória e de kernel, fornecendo resposta automática para comportamentos suspeitos.**

**Infraestrutura Hyper-convergente:** 
- **Reforço do desempenho, confiabilidade e simplificação da implantação e da gestão de ambientes hyperconvergentes.**
***
# Windows Server 2022

**Suporte a containers e Kubernetes:** 
- **O Windows Server 2022 oferece suporte a containerss com melhorias no Docker e no Kubernetes, permitindo que os utilizadores implementem e gerenciem containers com mais facilidade.**

**Melhorias de segurança:** 
- **Como é comum nas novas versões, o Windows Server 2022 trás melhorias de segurança, incluindo recursos aprimorados de proteção de identidade, proteção contra ameaças e controles de acesso.**

**Suporte estendido para o Azure Hybrid:** 
- **O Windows Server 2022 está integrado ao Azure para oferecer suporte estendido em ambientes híbridos, permitindo que as organizações ampliem as suas operações para a nuvem com mais facilidade.**

**Serviços de armazenamento e HCI:** 
- **O Windows Server 2022 trás melhorias nos serviços de armazenamento, incluindo armazenamento de arquivos e armazenamento definido por software.** 
**Além disso, há suporte aprimorado para Infraestrutura de Hiperconvergência (HCI).**

**Desempenho aprimorado:** 
- **O Windows Server 2022 foi projetado para oferecer melhor desempenho em diversas cargas de trabalho, incluindo virtualização, armazenamento e processamento de dados.**

**Melhorias na gestão:** 
- **O sistema operacional inclui melhorias na gestão de servidores, como o Windows Admin Center, para simplificar tarefas administrativas e oferecer uma experiência de gestão mais intuitiva.**
***
# Windows Server 2022
## Instalação

**Irei mostrar passo a passo da instalação no ambiente [VirtualBox](https://www.virtualbox.org/).**

**Fazer [Download](https://www.microsoft.com/en-US/evalcenter/evaluate-windows-server-2022) do Windows Server 2022 (ficheiro .iso)**

**Anexar a ISO do DVD de instalação do Windows Server 2022 à máquina virtual.**

**Após a máquina virtual ou o servidor inicializar a partir do DVD, ele exibirá um ecrã para configurar as configurações de idioma e teclado.**



# irei continuar este projeto