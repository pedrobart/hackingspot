A segurança do serviço Dynamic Host Configuration Protocol (DHCP) é extremamente importante para a segurança geral de uma rede. 
Estes serviço facilita a comunicação de utilziadores e sistemas na rede. 
No entanto, este serviço importante também pode ser alvo de invasores.

O DHCP garante que os dispositivos conectados à rede recebam endereços IP automaticamente. Isso facilita a gestão de grandes redes sem que os administradores de rede definam manualmente os endereços IP para cada dispositivo. No entanto, se o serviço DHCP não for seguro, um invasor pode adicionar o seu próprio servidor DHCP à rede e, assim, fornecer informações enganosas de configuração de rede aos dispositivos que se conectam à rede. Isso permite que os invasores redirecionem o tráfego para os seus sistemas e roubem informações potencialmente confidenciais.

A segurança deste serviço garante que a troca de informações na rede permaneça segura e privada. Isso não apenas protege as informações pessoais dos utilizadores, mas também protege as informações e serviços confidenciais das empresas de invasores maliciosos. Portanto, a segurança do serviço DHCP é vital para a segurança geral de uma rede.

O DHCP, um dos elementos indispensáveis ​​das redes, impede que os administradores de rede atribuam manualmente endereços IP a cada dispositivo, atribuindo automaticamente endereços IP aos dispositivos na rede. No entanto, a segurança desse importante serviço é frequentemente negligenciada. A segurança do servidor DHCP do Windows é crítica para a segurança geral da rede. Para evitar ameaças potenciais, como acesso não intencional à rede, ataques de negação de serviço (DoS) ou vazamentos de dados, é essencial proteger o servidor DHCP do Windows.

Devido à maneira como o DHCP funciona, há várias vulnerabilidades de segurança. Por exemplo, o serviço DHCP geralmente atribuirá um endereço IP a qualquer dispositivo na rede. Isso significa que um dispositivo não autorizado pode se conectar à rede e executar atividades potencialmente prejudiciais. Além disso, ataques baseados em DHCP podem derrubar o serviço DHCP ou falsificar o tráfego de rede. Finalmente, a confidencialidade e a integridade dos dados DHCP devem ser protegidas contra a possibilidade de alteração maliciosa das informações de endereço IP.


## Filtragem MAC

A filtragem MAC pode ser implementada por meio de endereços Media Access Control (MAC) usando DHCP no Windows Server. É usada para controlar se dispositivos com um endereço MAC específico recebem um endereço IP ou não.

A filtragem de endereço MAC é usada quando queremos que apenas certos dispositivos na  rede obtenham um endereço IP, ou quando queremos impedir que certos dispositivos obtenham um endereço IP.  Com isto melhoramos a segurança da rede porque permite que apenas certos dispositivos acedam à rede.



Após abrir o "Server Manager", selecionamos "DHCP" no menu "Tools". Na janela DHCP Management que se abre, na seção "IPv4" -> "Filter", clicamos com o botão direito do mouse na seção "Allow" ou "Deny" e selecionamos "New Filter".

A opção "Permitir" no tipo de filtro só fornece endereços IP para determinados endereços MAC, enquanto a opção "Negar" impede que determinados endereços MAC obtenham endereços IP.

![](../anexos/Pasted%20image%2020241205212922.png)

Na janela "New Filter", insirimos o endereço MAC que queremos filtrar no campo "MAC Address" e clicamos no botão "Add". Dessa forma, a filtragem de endereço MAC é ativada.

![](../anexos/Pasted%20image%2020241205213008.png)

A filtragem MAC pode ser uma maneira eficaz de aumentar a segurança da rede, mas não é uma medida de segurança suficiente por si só porque os endereços MAC podem ser facilmente falsificados. É por isso que ela deve ser usada frequentemente em conjunto com outras medidas de segurança.

## Bloqueio de DHCP não autorizado

Rogue DHCP é quando um servidor DHCP não autorizado e inesperado começa a servir numa rede, geralmente para propósitos maliciosos. Um servidor Rogue DHCP pode fornecer aos clientes informações enganosas de configuração de rede, o que pode redirecionar o tráfego de rede para destinos indesejados ou até mesmo redirecionar utilizadores para sites maliciosos.

Para detetar o servidor DHCP não autorizado no Windows Server, é usado o mecanismo de autorização do servidor DHCP que a Microsoft projetou para monitorizar automaticamente os servidores DHCP e detetar servidores não autorizados.

A autorização do servidor DHCP verifica se um servidor DHCP está registado e autorizado no Active Directory. Se um servidor DHCP não estiver autorizado, o serviço DHCP será interrompido automaticamente e esse servidor não poderá distribuir endereços IP.

Para usar a autorização do servidor DHCP, o servidor DHCP deve estar num domínio do Active Directory. Para autorizar o servidor DHCP, abrimos a consola DHCP, clicamos com o botão direito do rato no servidor DHCP e clicamos em "Autorizar"
![](../anexos/Pasted%20image%2020241205213216.png)

Se detetarmos um servidor DHCP não autorizado em execução na  rede, desautoriza-mos ou removemos imediatamente.

Por padrão, podemos ver os logs DHCP no diretório "C:\Windows\system32\dhcp" e segui-los de lá. Para deteção de Rogue DHCP, logs críticos com id 50 e acima devem ser especialmente monitorizados.

Os significados de alguns IDs de eventos DHCP são os seguintes. Mais de 50 IDs de eventos são importantes para deteção de servidores invasores:

![](../anexos/Pasted%20image%2020241205213356.png)
![](../anexos/Pasted%20image%2020241205213406.png)



