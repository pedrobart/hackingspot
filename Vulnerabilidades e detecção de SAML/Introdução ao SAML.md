
No cenário digital de hoje, as aplicações da web geralmente exigem mecanismos de autenticação seguros para verificar a identidade dos utilizadores e garantir o seu acesso autorizado aos recursos. Uma solução amplamente adotada para implementar autenticação segura e ativar a funcionalidade Single Sign-On (SSO) é a Security Assertion Markup Language (SAML). N

  
## O que é SAML?

Security Assertion Markup Language (SAML) é um padrão aberto baseado em XML para troca de dados de autenticação e autorização entre diferentes entidades num ambiente baseado na web. Ele fornece uma estrutura padronizada para autenticação segura, permitindo que os utilizadores acedam a vários aplicações usando um único conjunto de credenciais.

  
## Visão geral do fluxo de trabalho SAML

Num alto nível, o fluxo de trabalho SAML envolve três entidades principais: o Identity Provider (IdP), o Service Provider (SP) e o User.


#### fluxo de trabalho SAML:

**Solicitação de acesso do utilizador**

O utilizador tenta aceder a um recurso ou aplicação protegido fornecido pelo Provedor de Serviços (SP).

  
**Redirecionamento do Provedor de Serviços**

O Provedor de Serviços identifica que o utilizador não está autenticado e o redireciona para o Provedor de Identidade (IdP) para autenticação.



**Autenticação do utilizador**

- O Provedor de Identidade autentica o utilizador por vários meios, como nome de utilizador e senha, autenticação multifator ou outros mecanismos.
- Após a autenticação bem-sucedida, o IdP gera uma asserção SAML, que contém informações sobre o utilizador e o seu status de autenticação.

  

**Troca de Asserção SAML**

O IdP envia a asserção SAML para o navegador do utilizador, que então a redireciona para o Provedor de Serviços.

  

**Validação do Provedor de Serviços**

- O Provedor de Serviços verifica a integridade e a autenticidade da asserção SAML.
- Se a afirmação for válida, o utilizador  será considerado autenticado e o Provedor de Serviços concederá acesso ao recurso ou aplicação solicitada.

  
  

## Importância da segurança SAML

Dada sua ampla adoção, é crucial entender vulnerabilidades potenciais em implementações SAML para garantir autenticação segura e proteger contra ataques potenciais. Atores de ameaças podem tentar explorar vulnerabilidades em SAML para obter acesso não autorizado, manipular atributos de utilizador ou comprometer a integridade do processo de autenticação.

Para nós SOC, devemos ter uma  uma compreensão abrangente das vulnerabilidades SAML é essencial para detectar e responder proativamente a ameaças potenciais. 



## Deteção de SOC em segurança SAML

É vital estar ciente dos indicadores específicos de comprometimento (IOCs) e técnicas que podem auxiliar na deteção de vulnerabilidades SAML e ataques potenciais. 


## Monitorização de tráfego de asserção SAML

Monitorizar regularmente o tráfego de rede relacionado às asserções SAML trocadas entre o Provedor de Identidade (IdP) e o Provedor de Serviços (SP).

Procurar por padrões anormais, volume inesperado ou fluxos de mensagens SAML suspeitos que se desviem dos fluxos de trabalho normais de autenticação.

  
  

## Analisando metadados de asserção SAML

Analisar minuciosamente os metadados associados às asserções SAML, incluindo certificados de assinatura, identificadores de entidade e datas de expiração.

Sinalizar quaisquer anomalias, como certificados expirados ou adulterados, alterações inesperadas em identificadores de entidade ou metadados inconsistentes em transações SAML.

  
  

## Rastreamento de eventos de autenticação e autorização

Implementar mecanismos de registo e monitorização para capturar eventos de autenticação e autorização, incluindo transações SAML bem-sucedidas e com falha.

Monitorizar padrões de login suspeitos, múltiplas tentativas de autenticação com falha ou comportamento inesperado do utilizador que podem indicar um ataque ou comprometimento.

  


## Integração de Gestão de Informações e Eventos de Segurança (SIEM)

Integrar logs e eventos relacionados ao SAML num SIEM.

Aproveitar as regras de correlação e análises do SIEM para identificar possíveis vulnerabilidades do SAML, detetar anomalias e gerar alertas acionáveis ​​para investigação posterior.

Ao incorporar estas estratégias de deteção de SOC nas operações de segurança, podemos identificar e responder proativamente a vulnerabilidades SAML e possíveis ataques, mitigando o impacto na postura de segurança da organização.

