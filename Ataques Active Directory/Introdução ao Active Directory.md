
O Active Directory é um serviço de diretório desenvolvido pela Microsoft para redes de domínio Windows. É um banco de dados centralizado que armazena informações sobre recursos numa rede, como utilizadores, computadores e aplicações, e fornece uma estrutura hierárquica para organizar e gerir esses recursos.

O AD é usado para gerir e controlar o acesso a recursos de rede, como arquivos, impressoras e outros recursos partilhados. Ele fornece um mecanismo centralizado de autenticação e autorização, permitindo que os utilizadores acedam a recursos na rede usando um único conjunto de credenciais. O AD também fornece um único ponto de gestão para os administradores de rede, permitindo que controlem facilmente o acesso aos recursos de rede.

AD é um componente importante de muitas redes corporativas e é amplamente utilizado em organizações de todos os tamanhos. Ele integra-se com outras tecnologias da Microsoft, como o Exchange e o SharePoint, para fornecer uma solução abrangente para gerir a autenticação, autorização e acesso do user a recursos na rede. Além disso, ele suporta o uso de Objetos de Política de Grupo (GPOs) para impor políticas de segurança e conformidade, bem como fornecer uma infraestrutura para distribuição de software e gestão de patches.

O núcleo principal do Active Directory é o Kerberos. É um protocolo usado para autenticação, processo de autorização para ambientes de grande escala. C
  
  
## O que é o Kerberos?

Kerberos é o serviço de autenticação padrão para os domínios Microsoft Windows. Pretende-se ser mais "seguro" do que o NTLM usando a autorização de bilhete de terceiros, bem como criptografia mais forte. Mesmo que o NTLM tenha muito mais vetores de ataque para escolher, ele ainda tem um punhado de vulnerabilidades subjacentes, assim como o Kerberos, o que ainda o torna um alvo para agentes de ameaças. Ele funciona na UDP Port 88.

  
  

**Terminologias comuns:**

Centro de Distribuição de Chaves (KDC): 
O Centro de Distribuição Chave é um serviço para emissão de TGTs e tickets de serviço que consistem no Serviço de Autenticação e no Serviço de Concessão de Bilhetes.

- Ticket Granting Ticket (TGT):  é um ticket de autenticação usado para solicitar tickets de serviço do TGS para recursos específicos do domínio.

- Serviço de Autenticação (AS): O Serviço de Autenticação emite TGTs para ser usado pelo TGS no domínio para solicitar acesso a outras máquinas e tickets de serviço.

- Serviço de Subvenção de Bilhetes (TGS): No Active Directory é responsável por conceder Bilhetes de Serviço (STs) a clientes que já tenham obtido um Bilhete (TGT) do Servidor de Autenticação (AS).

Nome Principal de Serviço (SPN): Um Nome Principal de Serviço é um identificador dado a uma instância de serviço para associar uma instância de serviço a uma conta de serviço de domínio. O Windows exige que os serviços tenham uma conta de serviço de domínio e é por isso que um serviço precisa de um conjunto de SPN.

Vamos imaginar um diretório ativo que o user precisa aceder a uma partilha o de arquivos. O user simplesmente abre a partilha e insire as suas credenciais, se tiver permissões para aceder  à partilha. 

No backend, todo o fluxo de autenticação funciona:
  
1- O cliente solicita autenticação do KDC. Esta solicitação de autenticação seria em texto simples.

2- O KDC envia um TGT e uma chave de sessão se o cliente existir no banco de dados. Se o cliente não estiver no banco de dados, a autenticação falhará.

3- O cliente solicita o bilhete de serviço do arquivo junto com o TGT enviado anteriormente pelo KDC.

4- O KDC envia o ticket criptografado com a chave de sessão. O cliente pode usar a chave de sessão enviada anteriormente pelo KDC para descriptografar o ticket de serviço.

5- O cliente solicita o servidor Fileshare para acesso usando o ticket de serviço.

6- O servidor Fileshare autentica o cliente. Ele envia um ticket que concederá acesso à partilha de arquivos.
  

O bilhete de serviço tem um tempo de expiração específico. Pode ser usado o mesmo ticket de sessão para acessar os serviços até que ele expire. A vida útil padrão de um bilhete Kerberos é de 600 minutos.