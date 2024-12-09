A camada de rede, ou Camada OSI 3, fornece serviços para permitir que dispositivos finais troquem dados entre redes. Como mostrado na figura, IP versão 4 (IPv4) e IP versão 6 (IPv6) são os principais protocolos de comunicação de camada de rede. Outros protocolos de camada de rede incluem protocolos de roteamento, como OSPF (Open Shortest Path First) e protocolos de mensagens, como ICMP (Internet Control Message Protocol).

Para realizar comunicações de ponta a ponta através dos limites da rede, os protocolos de camada de rede executam quatro operações básicas:

- **Endereçamento de dispositivos finais** - Os dispositivos finais devem ser configurados com um endereço IP exclusivo para identificação na rede.
- **Encapsulamento** - A camada de rede encapsula a unidade de dados de protocolo (PDU) da camada de transporte em um pacote. O processo de encapsulamento adiciona informações de cabeçalho IP, como os endereços IP dos hosts origem (emissor) e destino (receptor). O processo de encapsulamento é executado pela origem do pacote IP.
- **Roteamento** - A camada de rede fornece serviços para direcionar os pacotes para um host de destino em outra rede. Para trafegar para outras redes, o pacote deve ser processado por um roteador. A função do roteador é escolher o melhor caminho e direcionar os pacotes para o host de destino em um processo conhecido como roteamento. Um pacote pode atravessar muitos roteadores antes de chegar ao host de destino. Cada roteador que um pacote atravessa para chegar ao host de destino é chamado de salto.
- **Desencapsulamento** - Quando o pacote chega na camada de rede do host de destino, o host verifica o cabeçalho IP do pacote. Se o endereço IP de destino no cabeçalho corresponder ao seu próprio endereço IP, o cabeçalho IP será removido do pacote. Depois que o pacote é desencapsulado pela camada de rede, a PDU resultante da Camada 4 é transferida para o serviço apropriado na camada de transporte. O processo de desencapsulamento é executado pelo host de destino do pacote IP.

### Encapsulamento IP

O IP encapsula o segmento da camada de transporte (a camada logo acima da camada de rede) ou outros dados adicionando um cabeçalho IP. O cabeçalho IP é usado para entregar o pacote ao host de destino.

### Características do IP

O IP foi desenvolvido como um protocolo com baixa sobrecarga. Ele fornece apenas as funções necessárias para enviar um pacote de uma origem a um destino por um sistema interconectado de redes. O protocolo não foi projetado para rastrear e gerenciar o fluxo de pacotes. Essas funções, se exigido, são realizadas por outros protocolos em outras camadas, principalmente TCP na Camada 4.

Estas são as características básicas da IP:

- **Sem conexão** - Não há conexão com o destino estabelecido antes do envio de pacotes de dados.
- **Melhor esforço** - o IP é inerentemente não confiável, porque a entrega de pacotes não é garantida.
- **Independente da mídia** - A operação é independente do meio (ou seja, cobre, fibra ótica ou sem fio) que carrega os dados.

O IP não tem conexão, o que significa que nenhuma conexão ponta a ponta dedicada é criada pelo IP antes que os dados sejam enviados. A comunicação sem conexão é conceitualmente semelhante a enviar uma carta a alguém sem notificar o destinatário com antecedência.

O IP também não requer campos adicionais no cabeçalho para manter uma conexão estabelecida. Esse processo reduz bastante a sobrecarga do IP. No entanto, sem conexão de ponta a ponta pré-estabelecida, os remetentes não sabem se os dispositivos de destino estão presentes e funcionais ao enviar pacotes, nem sabem se o destino recebe o pacote ou se o dispositivo de destino pode acessar e ler o pacote.
O protocolo IP não garante que o pacote enviado seja, de fato, recebido.

Não confiável significa que o IP não tem a capacidade de gerenciar e recuperar pacotes não entregues ou corrompidos. Isso ocorre porque, embora os pacotes IP sejam enviados com informações sobre o local da entrega, eles não contêm informações que podem ser processadas para informar ao remetente se a entrega foi bem-sucedida. Os pacotes podem chegar ao destino corrompidos, fora de sequência ou simplesmente não chegar. O IP não tem capacidade de retransmitir os pacotes em caso de erros.
Se os pacotes forem entregues fora de ordem ou estiver faltando algum pacote, as aplicações que usam os dados, ou serviços de camada superior, deverão resolver esses problemas. Isso permite que o IP funcione de forma bem eficiente. No conjunto de protocolos TCP / IP, a confiabilidade é o papel do protocolo TCP na camada de transporte.
O IP opera independentemente da mídia que transporta os dados nas camadas inferiores da pilha de protocolos.

A camada de enlace de dados OSI é responsável por pegar um pacote IP e prepará-lo para transmissão pelo meio de comunicação. Isso significa que a entrega de pacotes IP não se limita a nenhum meio específico.

Há, no entanto, uma característica muito importante dos meios físicos que a camada de rede considera: o tamanho máximo da PDU que cada meio consegue transportar. Essa característica é chamada de unidade máxima de transmissão (maximum transmission unit - MTU). Parte das comunicações de controle entre a camada de enlace de dados e a camada de rede é a definição de um tamanho máximo para o pacote. A camada de enlace de dados passa o valor da MTU para a camada de rede. A camada de rede então determina o tamanho que os pacotes podem ter.

Em alguns casos, um dispositivo intermediário, geralmente um roteador, deve dividir um pacote IPv4 ao encaminhá-lo de um meio para outro com uma MTU menor. Esse processo é chamado fragmentação do pacote ou fragmentação. A fragmentação causa latência. Os pacotes IPv6 não podem ser fragmentados pelo roteador.

# Pacote IPv4

### Cabeçalho do Pacote IPv4

O IPv4 é um dos principais protocolos de comunicação de camada de rede. O cabeçalho do pacote IPv4 é usado para garantir que esse pacote seja entregue para sua próxima parada no caminho para seu dispositivo final de destino.

O cabeçalho de um pacote IPv4 consiste em campos com informações importantes sobre o pacote. Esses campos contêm números binários que são examinados pelo processo da Camada 3.

Campos significativos no cabeçalho IPv4 incluem o seguinte:

- **Versão** - Contém um valor binário de 4 bits definido como 0100 que identifica isso como um pacote IPv4.
- **Serviços diferenciados ou DiffServ (DS)** - Anteriormente chamado de campo tipo de serviço (ToS), o campo DS é um campo de 8 bits usado para determinar a prioridade de cada pacote. Os seis bits mais significativos do campo DiffServ são os bits do ponto de código de serviços diferenciados (DSCP) e os dois últimos são os bits de notificação de congestionamento explícita (ECN).
- **Tempo de vida (TTL)** - TTL contém um valor binário de 8 bits usado para limitar a vida útil de um pacote. O dispositivo de origem do pacote IPv4 define o valor TTL inicial. É diminuído em um cada vez que o pacote é processado por um roteador. Se o campo TTL for decrementado até zero, o roteador descartará o pacote e enviará uma mensagem ICMP de tempo excedido para o endereço IP de origem. Como o roteador decrementa o TTL de cada pacote, o roteador também deve recalcular a soma de verificação do cabeçalho.
- **Protocolo** - Este campo é usado para identificar o próximo nível de protocolo. O valor binário de 8 bits indica o tipo de carga de dados que o pacote está carregando, o que permite que a camada de rede transfira os dados para o protocolo apropriado das camadas superiores. Valores comuns incluem ICMP (1), TCP (6) e UDP (17). Checksum de * **cabeçalho -** Isso é usado para detectar corrupção no cabeçalho IPv4.
- **Endereço IPv4 de origem** - Contém um valor binário de 32 bits que representa o endereço IPv4 de origem do pacote. O endereço de origem IPv 4 é sempre um endereço unicast.
- **Endereço IPv4 de destino** - Contém um valor binário de 32 bits que representa o endereço IPv4 de destino do pacote. O endereço IPv4 destino é um endereço unicast, multicast, ou broadcast.

# Pacote IPv6

Ao longo dos anos, protocolos e processos adicionais foram desenvolvidos para enfrentar novos desafios. No entanto, mesmo com alterações, ele ainda enfrenta três grandes problemas:

- **Esgotamento do endereço IPv4** - O IPv4 tem um número limitado de endereços públicos exclusivos disponíveis. Embora haja aproximadamente 4 bilhões de endereços IPv4, o número crescente de novos dispositivos habilitados para IP, conexões sempre ativas e o potencial de crescimento de regiões menos desenvolvidas têm aumentado a necessidade de mais endereços.
- **Falta de conectividade ponto a ponto** - Network Address Translation (NAT) é uma tecnologia comumente implementada em redes IPv4. A NAT é uma forma de vários dispositivos compartilharem um único endereço IPv4 público. No entanto, como o endereço IPv4 público é compartilhado, o endereço IPv4 de um host de rede interna fica oculto. Isso pode ser problemático para tecnologias que exigem conectividade de ponta a ponta.
- **Maior complexidade da rede** - Embora o NAT tenha ampliado a vida útil do IPv4, ele só se destinava a ser um mecanismo de transição para o IPv6. O NAT em suas várias implementações cria complexidade adicional na rede, criando latência e dificultando a solução de problemas.

### Visão geral do IPv6

No início da década de 90, a Internet Engineering Task Force (IETF) tinha uma preocupação crescente a respeito dos problemas com o IPv4 e começou a procurar um substituto. Isso levou ao desenvolvimento do IP versão 6 (IPv6). O IPv6 supera as limitações do IPv4 e possui recursos que atendem às demandas atuais e previsíveis de rede.

As melhorias que o IPv6 fornece incluem o seguinte:

- **Espaço de endereço aumentado** - os endereços IPv6 são baseados no endereçamento hierárquico de 128 bits, em oposição ao IPv4 com 32 bits.
- **Manipulação aprimorada de pacotes** - O cabeçalho IPv6 foi simplificado com menos campos.
- **Elimina a necessidade de NAT** - com um número tão grande de endereços IPv6 públicos, o NAT entre um endereço IPv4 privado e um IPv4 público não é necessário. Isso evita alguns dos problemas induzidos por NAT enfrentados por aplicativos que exigem conectividade de ponta a ponta.

O espaço de 32 bits de um endereço IPv4 fornece aproximadamente 4.294.967.296 endereços exclusivos. O espaço de endereço IPv6 fornece 340.282.366.920.938.463.463.374.607.431.768.211.456, ou 340 undecilhões de endereços. Isto é aproximadamente equivalente a cada grão de areia na Terra.

### Campos do cabeçalho de pacote IPv4 no cabeçalho de pacote IPv6

Uma das principais melhorias de design do IPv6 em relação ao IPv4 é o cabeçalho IPv6 simplificado.

Por exemplo, o cabeçalho IPv4 consiste em um cabeçalho de comprimento variável de 20 octetos (até 60 bytes se o campo Opções for usado) e 12 campos de cabeçalho básicos, sem incluir o campo Opções e o campo Preenchimento.

Para o IPv6, alguns campos permaneceram os mesmos, alguns campos mudaram de nome e posição e alguns campos do IPv4 não são mais necessários, conforme destacado na figura.

![[Pasted image 20241117190804.png]]

Por outro lado, o cabeçalho simplificado do IPv6 mostrado na figura a seguir consiste em um cabeçalho de comprimento fixo de 40 octetos (em grande parte devido ao comprimento dos endereços IPv6 de origem e de destino).

O cabeçalho simplificado IPv6 permite um processamento mais eficiente de cabeçalhos IPv6.
![[Pasted image 20241117190909.png]]

### Cabeçalho do Pacote IPv6

- **Versão** - Este campo contém um valor binário de 4 bits definido como 0110 que identifica isso como um pacote IP versão 6.
- **Classe de tráfego** - Este campo de 8 bits é equivalente ao campo DSv (Serviços diferenciados de IPv4).
- **Etiqueta de fluxo** - Este campo de 20 bits sugere que todos os pacotes com a mesma etiqueta de fluxo recebam o mesmo tipo de manipulação pelos roteadores.
- **Comprimento da carga útil** - Este campo de 16 bits indica o comprimento da parte dos dados ou da carga útil do pacote IPv6. Isso não inclui o comprimento do cabeçalho IPv6, que é um cabeçalho fixo de 40 bytes.
- **Próximo cabeçalho** - Este campo de 8 bits é equivalente ao campo Protocolo IPv4. Ele exibe o tipo de carga de dados que o pacote está carregando, permitindo que a camada de rede transfira os dados para o protocolo apropriado das camadas superiores.
- **Limite de salto** - Este campo de 8 bits substitui o campo TTL IPv4. Esse valor é subtraído de um por cada roteador que encaminha o pacote. Quando o contador atinge 0, o pacote é descartado e uma mensagem de ICMPv6 com tempo excedido é encaminhada para o host de envio. Isso indica que o pacote não atingiu seu destino porque o limite de salto foi excedido. Ao contrário do IPv4, o IPv6 não inclui uma soma de verificação do cabeçalho IPv6, porque esta função é executada nas camadas inferior e superior. Isso significa que a soma de verificação não precisa ser recalculada por cada roteador quando diminui o campo Limite de Saltos, o que também melhora o desempenho da rede.
- **Endereço IPv6 de origem** - Este campo de 128 bits identifica o endereço IPv6 do host de envio.
- **Endereço IPv6 de destino** - Este campo de 128 bits identifica o endereço IPv6 do host de recebimento.

Um pacote IPv6 pode conter também cabeçalhos de extensão (EH), que fornecem informações de camada de rede. Opcionais, os cabeçalhos de extensão ficam posicionados entre o cabeçalho IPv6 e a carga. Eles são usados para fragmentação, segurança, suporte à mobilidade e muito mais.

Ao contrário de IPv4, os roteadores não fragmentam os pacotes IPv6 roteados.Um pacote IPv6 pode conter também cabeçalhos de extensão (EH), que fornecem informações de camada de rede. Opcionais, os cabeçalhos de extensão ficam posicionados entre o cabeçalho IPv6 e a carga. Eles são usados para fragmentação, segurança, suporte à mobilidade e muito mais.

Ao contrário de IPv4, os roteadores não fragmentam os pacotes IPv6 roteados.

# Como um Host Roteia

Com IPv4 e IPv6, os pacotes são sempre criados no host de origem. O host de origem deve ser capaz de direcionar o pacote para o host de destino. Para fazer isso, os dispositivos finais do host criam sua própria tabela de roteamento. Este tópico discute como os dispositivos finais usam tabelas de roteamento.

Outra função da camada de rede é direcionar pacotes entre hosts. Um host pode enviar um pacote para o seguinte:

- **Itself** - Um host pode fazer ping em si mesmo enviando um pacote para um endereço IPv4 especial de 127.0.0.1 ou um endereço IPv6 ::1, que é referido como a interface de loopback. O ping na interface de loopback testa a pilha de protocolos do TCP/IP no host.
- **Host local** - Este é um host de destino que está na mesma rede local que o host de envio. Os hosts de origem e destino compartilham o mesmo endereço de rede.
- **Host remoto** - Este é um host de destino em uma rede remota. Os hosts de origem e destino não compartilham o mesmo endereço de rede.

O método de determinação varia de acordo com a versão IP:

- **Em IPv4** - O dispositivo de origem usa sua própria máscara de sub-rede juntamente com seu próprio endereço IPv4 e o endereço IPv4 de destino para fazer essa determinação.
- **Em IPv6** - O roteador local anuncia o endereço de rede local (prefixo) para todos os dispositivos na rede.

Em uma rede doméstica ou comercial, você pode ter vários dispositivos com e sem fio interconectados usando um dispositivo intermediário, como um switch LAN ou um ponto de acesso sem fio (WAP). Este dispositivo intermediário fornece interconexões entre hosts locais na rede local. Os hosts locais podem interagir entre si e compartilhar informações sem a necessidade de dispositivos adicionais. Se um host estiver enviando um pacote para um dispositivo configurado com a mesma rede IP que o dispositivo host, o pacote será simplesmente encaminhado para fora da interface do host, através do dispositivo intermediário e diretamente ao dispositivo de destino.

Obviamente, na maioria das situações, queremos que nossos dispositivos possam se conectar além do segmento de rede local, como em outras residências, empresas e na Internet. Os dispositivos que estão além do segmento de rede local são conhecidos como hosts remotos. Quando um dispositivo de origem envia um pacote a um dispositivo de destino remoto, é necessária a ajuda de roteadores e do roteamento. O roteamento é o processo de identificação do melhor caminho até um destino. O roteador conectado ao segmento de rede local é conhecido como gateway padrão (default gateway).

### Gateway Padrão

O gateway padrão é o dispositivo de rede (ou seja, roteador ou switch da Camada 3) que pode rotear o tráfego para outras redes. Comparando a rede com uma sala, o gateway padrão é a porta. Se você quiser ir para outra sala (rede), vai precisar encontrar essa porta.

Em uma rede, um gateway padrão geralmente é um roteador com esses recursos:

- Ele possui um endereço IP local no mesmo intervalo de endereços que outros hosts na rede local.
- Ele pode aceitar dados na rede local e encaminhar dados para fora da rede local.
- Ele direciona o tráfego para outras redes.

Um gateway padrão é necessário para enviar tráfego fora da rede local. O tráfego não pode ser encaminhado para fora da rede local se não houver gateway padrão, o endereço de gateway padrão não estiver configurado ou o gateway padrão estiver inativo.

### Um host direciona para o gateway padrão

Uma tabela de roteamento de host normalmente inclui um gateway padrão. No IPv4, o host recebe o endereço IPv4 do gateway padrão dinamicamente do DHCP (Dynamic Host Configuration Protocol) ou configurado manualmente. No IPv6, o roteador anuncia o endereço de gateway padrão ou o host pode ser configurado manualmente.

A configuração do gateway padrão cria uma rota padrão na tabela de roteamento do computador. Uma rota padrão é a rota ou o caminho que o computador usa quando tenta entrar em contato com uma rede remota.

### Tabelas de Roteamento dos Hosts

Em um host do Windows, o comando **route print** ou **netstat -r** pode ser usado para exibir a tabela de roteamento do host. Ambos os comandos geram a mesma saída. O resultado pode parecer confuso no começo, mas é bastante simples de entender.

**Observação:** A saída exibe apenas a tabela de rotas IPv4.

A inserção do comando **netstat -r** ou o comando equivalente **route print** exibe três seções relacionadas às conexões de rede TCP / IP atuais:

- **Lista de interfaces** - lista o endereço MAC (Media Access Control) e o número de interface atribuído de todas as interfaces com capacidade de rede no host, incluindo adaptadores Ethernet, Wi-Fi e Bluetooth.
- **Tabela de rotas IPv4** - lista todas as rotas IPv4 conhecidas, incluindo conexões diretas, rede local e rotas padrão locais.
- **Tabela de rotas IPv6** - lista todas as rotas IPv6 conhecidas, incluindo conexões diretas, rede local e rotas padrão locais

# Introdução ao Roteamento

### Decisão de Encaminhamento de Pacotes do Roteador

A maioria das redes também contém roteadores, que são dispositivos intermediários. Os roteadores também contêm tabelas de roteamento. Este tópico aborda as operações do roteador na camada de rede. Quando um host envia um pacote para outro host, ele consulta sua tabela de roteamento para determinar para onde enviar o pacote. Se o host de destino estiver em uma rede remota, o pacote será encaminhado para o gateway padrão, que geralmente é o roteador local.

O que acontece quando um pacote chega na interface do roteador?

O roteador examina o endereço IP de destino do pacote e pesquisa sua tabela de roteamento para determinar para onde encaminhar o pacote. A tabela de roteamento contém uma lista de todos os endereços de rede conhecidos (prefixos) e para onde encaminhar o pacote. Essas entradas são conhecidas como entradas de rota ou rotas. O roteador encaminhará o pacote usando a melhor (mais longa) entrada de rota correspondente.

### Tabela de Roteamento do Roteador IP

A tabela de roteamento armazena três tipos de entradas de rota:

- **Redes conectadas diretamente** - Essas entradas de rota de rede são interfaces de roteador ativas. Os roteadores adicionam uma rota diretamente conectada quando uma interface está configurada com um endereço IP e está ativada. Cada interface do roteador está conectada a um segmento de rede diferente. Na figura, as redes diretamente conectadas na tabela de roteamento IPv4 R1 seriam 192.168.10.0/24 e 209.165.200.224/30.
- **Redes remotas** - Essas entradas de rotas de rede são conectadas a outros roteadores. Os roteadores aprendem sobre redes remotas sendo explicitamente configurados por um administrador ou trocando informações de rota usando um protocolo de roteamento dinâmico. Na figura, a rede remota na tabela de roteamento IPv4 R1 seria 10.1.1.0/24.
- **Rota padrão** - Como um host, a maioria dos roteadores também inclui uma entrada de rota padrão, um gateway de último recurso. A rota padrão é usada quando não há correspondência melhor (mais) na tabela de roteamento IP. Na figura, a tabela de roteamento IPv4 R1 provavelmente incluiria uma rota padrão para encaminhar todos os pacotes para o roteador R2.
![[Pasted image 20241117193119.png]]

Um roteador pode aprender sobre redes remotas de duas maneiras:

- **Manualmente** - As redes remotas são inseridas manualmente na tabela de rotas usando rotas estáticas.
- **Dinamicamente** - As rotas remotas são aprendidas automaticamente usando um protocolo de roteamento dinâmico.

### Roteamento estático

Rotas estáticas são entradas de rota configuradas manualmente.

Se houver uma alteração na topologia da rede, a rota estática não será atualizada automaticamente e deverá ser reconfigurada manualmente.

O roteamento estático tem as seguintes características:

- Uma rota estática deve ser configurada manualmente.
- O administrador precisa reconfigurar uma rota estática se houver uma alteração na topologia e a rota estática não for mais viável.
- Uma rota estática é apropriada para uma rede pequena e quando há poucos ou nenhum vínculo redundante.
- Uma rota estática é comumente usada com um protocolo de roteamento dinâmico para configurar uma rota padrão.

### Roteamento dinâmico

Um protocolo de roteamento dinâmico permite que os roteadores aprendam automaticamente sobre redes remotas, incluindo uma rota padrão, de outros roteadores. Os roteadores que usam protocolos de roteamento dinâmico compartilham automaticamente informações de roteamento com outros roteadores e compensam qualquer alteração de topologia sem envolver o administrador da rede. Se houver uma alteração na topologia de rede, os roteadores compartilham essas informações usando o protocolo de roteamento dinâmico e atualizam automaticamente suas tabelas de roteamento.

Os protocolos de roteamento dinâmico incluem OSPF e Enhanced Interior Gateway Routing Protocol (EIGRP).

A configuração básica requer apenas que o administrador de rede habilite as redes conectadas diretamente dentro do protocolo de roteamento dinâmico. O protocolo de roteamento dinâmico fará automaticamente o seguinte:

- Descobrir redes remotas;
- Manter as informações de roteamento atualizadas;
- Escolha o melhor caminho para as redes de destino;
- Tente encontrar um novo melhor caminho se o caminho atual não estiver mais disponível.

Quando um roteador é configurado manualmente com uma rota estática ou aprende sobre uma rede remota dinamicamente usando um protocolo de roteamento dinâmico, o endereço de rede remota e o endereço de próximo salto são inseridos na tabela de roteamento IP.

**Observação:** É comum que alguns roteadores usem uma combinação de rotas estáticas e um protocolo de roteamento dinâmico.

### Introdução a uma tabela de roteamento IPv4

O comando de modo EXEC **show ip route** privilegiado é usado para exibir a tabela de roteamento IPv4 em um roteador Cisco IOS.

No início de cada entrada de tabela de roteamento é um código que é usado para identificar o tipo de rota ou como a rota foi aprendida. As fontes comuns de rotas (códigos) incluem:

- **L** - Endereço IP da interface local diretamente conectado
- **C** - Rede diretamente conectada
- **S** - A rota estática foi configurada manualmente por um administrador
- **O** - OSPF
- **D** - EIGRP