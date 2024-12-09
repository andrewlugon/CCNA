Enable - entra no modo priv

Disable - sair do modo priv

configure terminal - configuração global

exit ou ctrl z- sair do modo

line - modo de subconfiguração de linha, use o comando **line** seguido pelo tipo e número da linha 
de gerenciamento que deseja acessar

interface - configuração de interface

hostname - alterar nome

no hostname - retornar nome padrão

enable secret - proteger o acesso EXEC priv

line vty 0 15 - entrar no modo VTY

password - config senha

login - ativar o acesso VTY

service password-encryption - criptografar todas as senhas de texto simples

show running-config - verificar as senhas estão criptografadas

banner motd # mensagem do dia #

startup-config - Este é o arquivo de configuração salvo armazenado na NVRAM. Ele contém todos os comandos que serão usados pelo dispositivo na inicialização ou reinicialização. O flash não perde seu conteúdo quando o dispositivo está desligado.

running-config - Isto é armazenado na memória de acesso aleatório (RAM). Ele reflete a configuração atual. A modificação de uma configuração ativa afeta o funcionamento de um dispositivo Cisco imediatamente. A RAM é uma memória volátil. Ela perde todo o seu conteúdo quando o dispositivo é desligado ou reiniciado.

show running-config - do modo EXEC privilegiado é usado para visualizar a configuração em execução

show startup-config - visualizar o arquivo de configuração de inicialização

copy running-config startup-config - salvar as alterações feitas na configuração em execução no arquivo de configuração de inicialização EXEC privilegiado

copy running-config running-config - salva config RAM

reload  - restaurar o startup-config (A desvantagem de usar o comando reload para remover uma configuração em execução não salva é o breve período de tempo em que o dispositivo ficará offline, causando o tempo de inatividade da rede.)

 erase startup-config - A configuração de inicialização é removida