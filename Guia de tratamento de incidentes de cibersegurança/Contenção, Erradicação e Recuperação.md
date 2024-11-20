
A etapa de Contenção, Erradicação e Recuperação inclui isolamento, limpeza dos indicadores/métodos de persistência utilizados no ataque e restauração dos sistemas.

#### Contenção

A etapa de contenção é onde o invasor fica isolado para que não possa causar mais danos. Dado que atrasar a etapa de contenção é arriscado, esta deve ser realizada assim que o evento for detetado e confirmado como um incidente de cibersegurança.

Os métodos de contenção podem mudar dependendo do tipo de incidente de segurança. Alguns métodos de contenção que podem ser aplicados são:

- Colocar o dispositivo num segmento de rede isolado,
- Parar os serviços afetados,
- Desligar o dispositivo,
- Desconectar o dispositivo da rede,
- Desativar a conta do utilizador na rede da organização.

Os produtos EDR atuais vêm com recurso de contenção. Com esse recurso, o dispositivo no qual o agente está instalado fica separado da rede e comunica apenas com o servidor central do EDR. Desta forma, ao realizar análises ao vivo no dispositivo, o isolamento do dispositivo também é garantido.

Devemos criar uma estratégia de contenção completa durante a fase de preparação.

Como não é possível isolar servidores críticos diretamente da rede, é altamente recomendável preparar um procedimento de contenção separado para aplicações/servidores críticos.

***
#### Erradicação

A etapa de erradicação inclui atividades como limpar o software malicioso deixado pelo invasor, desativar os utilizadores comprometidos e excluir os utilizadores criados pelo invasor.

O ponto mais importante que não deve ser esquecido nesta etapa é que os indicadores pertencentes ao ataque são registrados como prova antes de serem apagados. Por exemplo, antes de excluir do servidor um software malicioso usado no ataque, é necessário fazer uma screenshot da pasta onde o malware está localizado, para salvar as informações de hash do malware e registar uma cópia do malware num ambiente isolado.

As atividades a serem realizadas na etapa de erradicação podem ser listadas como;
- Limpar os arquivos enviados pelo invasor,
- Desativar/excluir utilizadores comprometidos,
- Excluindo utilizadores criados pelo invasor,
- Mitigar as vulnerabilidades identificadas,
- Encerramento de processos em execução ativa.

***
## Recuperação

A fase de recuperação inclui a restauração dos servidores/dispositivos/serviços afetados ao seu estado operacional anterior e a confirmação do seu funcionamento adequado.

A fase de recuperação varia de organização para organização. 

Estratégias que podem ser aplicadas na fase de recuperação podem ser listadas como;

- Retornar ao backup pré-comprometimento
- Reconstruir sistemas do zero
- Substituir arquivos comprometidos por versões limpas
- Instalar patches
- Alterar senhas
- Reforçar a segurança do perímetro da rede
***
