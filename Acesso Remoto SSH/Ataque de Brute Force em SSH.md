O SSH é um protocolo de rede encriptado que permite a gestão remota de sistemas, sobretudo de tipo Unix. É versátil e pode encapsular outros protocolos para fornecer encriptação adicional. Normalmente, os administradores autenticam-se via comando SSH utilizando as mesmas credenciais de acesso do sistema, o que se torna problemático quando a porta 22 está exposta, especialmente na Internet. Senhas fracas em contas conhecidas facilitam o sucesso de ataques de força bruta.

Neste cenário, simula-se um ataque de força bruta ao serviço SSH, onde o invasor consegue aceder e efetuar login com sucesso. 

Serão aplicadas técnicas de deteção das tentativas de acesso e identificação do IP de origem do invasor.


**Instalação de openssh-server no ubuntu:**
![[Screenshot 2025-02-23 172121.png]]

**Após instalação, verificamos se o serviço está Ativo:**
![[Screenshot 2025-02-23 172140 1.png]]

**Executamos os seguintes comandos para iniciar o serviço:**
![[Screenshot 2025-02-23 172204.png]]

**Ativamos o serviço SSH para ligar automaticamente após a máquina fazer boot:**
![[Screenshot 2025-02-23 172217.png]]

Utilizei a ferramenta Hydra para realizar um ataque de força bruta no servidor, onde a presença de uma senha correta na lista permitiu o acesso bem-sucedido. As tentativas incorretas, geradas durante o ataque, foram registadas nos logs de autenticação, localizados em **/var/log/auth.log**. 

Em cenários reais, estes ataques podem manifestar-se de forma ruidosa (milhares de tentativas por minuto) ou furtiva (1 tentativa por minuto), sendo crucial a análise destes registos para a deteção e mitigação de intrusões.

**Ator malicioso:**
![[Screenshot 2025-02-23 173945.png]]

**Sistema vítima:**
![[Screenshot 2025-02-23 174839.png]]


**Iniciando o ataque de Brute Force:**
![[Screenshot 2025-02-23 175106.png]]

**Ataque realizado com sucesso:**
![[Screenshot 2025-02-23 175250.png]]


Utilizando o comando:
 **cat /var/log/auth.log | grep "Failed password"**

![[Pasted image 20250223175813.png]]

Foram registadas múltiplas tentativas de acesso a partir do IP **192.168.1.4**, com a maioria dos acessos falhados. Os registos de autenticação (localizados em **/var/log/auth.log**) fornecem informações forenses cruciais, nomeadamente:
- **Timestamps**
- **Nome de utilizador**
- **IP de origem**


Após as várias tentativas falhadas, o log de autenticação regista entradas que comprovam que o atacante conseguiu, de facto, autenticar-se via SSH. Isto evidencia a eficácia do ataque de força bruta. Para extrair exclusivamente as entradas que correspondem a acessos SSH remotos bem-sucedidos, pode ser utilizado o comando:
**cat /var/log/auth.log | grep "Accepted password"**

![[Pasted image 20250223180219.png]]

O ficheiro **/var/log/wtmp** regista, de forma cronológica, todos os eventos de login e logout do sistema, permitindo traçar uma linha do tempo dos acessos, incluindo sessões remotas. Este registo é de extrema importância para análises forenses e para equipas de SOC, pois fornece dados cruciais para identificar atividades suspeitas ou padrões de acesso.

Devido à sua natureza binária, o **wtmp** não pode ser visualizado diretamente com comandos como o `cat`. Para ler o seu conteúdo, utiliza-se o utilitário **utmpdump**, que converte o ficheiro para um formato legível. Um exemplo de utilização é:
**utmpdump /var/log/wtmp**

![[Pasted image 20250223180827.png]]

Este artefacto é essencial para determinar **se um invasor conseguiu sessão no sistema**, **quanto tempo permaneceu ativo** e **de onde realizou o acesso**, permitindo tomar decisões informadas para mitigação e resposta ao incidente.

