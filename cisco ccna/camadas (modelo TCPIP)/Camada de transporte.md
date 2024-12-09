Conexão orientada

- **TCP** - Protocolo de controle de transmissão. Permite a comunicação confiável entre processos executados em hosts separados e fornece transmissões confiáveis e reconhecidas que confirmam a entrega bem-sucedida.

Sem Conexão

- **UDP** - Protocolo de datagrama do usuário. Permite que um processo em execução em um host envie pacotes para um processo em execução em outro host. No entanto, o UDP não confirma a transmissão bem-sucedida do datagrama.

### Propósito da Camada de Transporte

Os programas da camada de aplicação geram dados que devem ser trocados entre os hosts de origem e de destino. A camada de transporte é responsável pela comunicação lógica entre aplicativos executados em hosts diferentes. Isso pode incluir serviços como o estabelecimento de uma sessão temporária entre dois hosts e a transmissão confiável de informações para um aplicativo.

A camada de transporte não tem conhecimento do tipo de host de destino, o tipo de mídia pela qual os dados devem percorrer, o caminho percorrido pelos dados, o congestionamento em um link ou o tamanho da rede.

A camada de transporte inclui dois protocolos:

- Protocolo TCP (Transmission Control Protocol)
- Protocolo UDP (User Datagram Protocol)

### Responsabilidades da Camada de Transporte

**Rastreamento de Conversações Individuais**

Na camada de transporte, cada conjunto de dados que flui entre um aplicativo de origem e um aplicativo de destino é conhecido como conversa e é rastreado separadamente. É responsabilidade da camada de transporte manter e monitorar essas várias conversações.

Como ilustrado na figura, um host pode ter vários aplicativos que estão se comunicando pela rede simultaneamente.

A maioria das redes tem uma limitação da quantidade de dados que pode ser incluída em um único pacote. Portanto, os dados devem ser divididos em partes gerenciáveis.

**Segmentação de Dados e Remontagem de Segmentos**

É responsabilidade da camada de transporte dividir os dados do aplicativo em blocos de tamanho adequado. Dependendo do protocolo de camada de transporte usado, os blocos de camada de transporte são chamados de segmentos ou datagramas. 

A camada de transporte divide os dados em blocos menores (ou seja, segmentos ou datagramas) que são mais fáceis de gerenciar e transportar.

**Adicionar Informações de Cabeçalho**

O protocolo da camada de transporte também adiciona informações de cabeçalho contendo dados binários organizados em vários campos a cada bloco de dados. São os valores nesses campos que permitem que os vários protocolos da camada de transporte realizem diferentes funções no gerenciamento da comunicação de dados.

Por exemplo, as informações de cabeçalho são usadas pelo host de recebimento para remontar os blocos de dados em um fluxo de dados completo para o programa de camada de aplicativo de recebimento.

A camada de transporte garante que, mesmo com vários aplicativos em execução em um dispositivo, todos os aplicativos recebam os dados corretos.

**Identificação das Aplicações**

A camada de transporte deve separar e gerenciar várias comunicações com as diferentes necessidades de requisitos de transporte. Para passar fluxos de dados para os aplicativos adequados, a camada de transporte identifica o aplicativo de destino usando um identificador chamado número da porta. 

**Multiplexação das Conversas**

O envio de alguns tipos de dados (por exemplo, um vídeo de streaming) através de uma rede, como um fluxo de comunicação completo, pode consumir toda a largura de banda disponível. Isso impediria que outras conversas de comunicação ocorressem ao mesmo tempo. Isso também dificultaria a recuperação de erro e retransmissão dos dados danificados.

A verificação de erros pode ser realizada nos dados do segmento, para determinar se o segmento foi alterado durante a transmissão.

### Protocolos da Camada de Transporte

O IP está preocupado apenas com a estrutura, endereçamento e roteamento de pacotes. O IP não especifica como a entrega ou o transporte de pacotes ocorrem.

Os protocolos de camada de transporte especificam como transferir mensagens entre hosts e são responsáveis pelo gerenciamento dos requisitos de confiabilidade de uma conversa. A camada de transporte inclui os protocolos TCP e UDP.

Diferentes aplicações têm diferentes necessidades de confiabilidade de transporte. Portanto, o TCP/IP fornece dois protocolos de camada de transporte.

### Protocolo TCP (Transmission Control Protocol)

O TCP é considerado um protocolo de camada de transporte confiável, completo, que garante que todos os dados cheguem ao destino. O TCP inclui campos que garantem a entrega dos dados do aplicativo. Esses campos exigem processamento adicional pelos hosts de envio e recebimento.

**Nota**: O TCP divide os dados em segmentos.

O transporte TCP é análogo a enviar pacotes que são rastreados da origem ao destino. Se um pedido pelo correio estiver dividido em vários pacotes, um cliente poderá verificar on-line a sequência de recebimento do pedido.

O TCP fornece confiabilidade e controle de fluxo usando estas operações básicas:

- Número e rastreamento de segmentos de dados transmitidos para um host específico a partir de um aplicativo específico;
- Confirmar dados recebidos;
- Retransmitir todos os dados não confirmados após um determinado período de tempo
- Dados de sequência que podem chegar em ordem errada
- Enviar dados a uma taxa eficiente que seja aceitável pelo receptor.

Para manter o estado de uma conversa e rastrear as informações, o TCP deve primeiro estabelecer uma conexão entre o remetente e o receptor. É por isso que o TCP é conhecido como um protocolo orientado a conexão.

### Protocolo UDP (User Datagram Protocol)

O UDP é um protocolo de camada de transporte mais simples do que o TCP. Ele não fornece confiabilidade e controle de fluxo, o que significa que requer menos campos de cabeçalho. Como o remetente e os processos UDP receptor não precisam gerenciar confiabilidade e controle de fluxo, isso significa que datagramas UDP podem ser processados mais rápido do que segmentos TCP. O UDP fornece as funções básicas para fornecer datagramas entre os aplicativos apropriados, com muito pouca sobrecarga e verificação de dados.

**Nota**: O UDP divide os dados em datagramas que também são chamados de segmentos.

UDP é um protocolo sem conexão. Como o UDP não fornece confiabilidade ou controle de fluxo, ele não requer uma conexão estabelecida. Como o UDP não controla informações enviadas ou recebidas entre o cliente e o servidor, o UDP também é conhecido como um protocolo sem estado.

UDP também é conhecido como um protocolo de entrega de melhor esforço porque não há confirmação de que os dados são recebidos no destino. Com o UDP, não há processo de camada de transporte que informe ao remetente se a entrega foi bem-sucedida.

O UDP é como colocar uma carta regular, não registrada, no correio. O remetente da carta não tem conhecimento se o destinatário está disponível para receber a carta. Nem a agência de correio é responsável por rastrear a carta ou informar ao remetente se ela não chegar ao destino final.

### O protocolo de Camada de Transporte Certo para a Aplicação Certa

Alguns aplicativos podem tolerar a perda de dados durante a transmissão pela rede, mas atrasos na transmissão são inaceitáveis. Para esses aplicativos, o UDP é a melhor escolha, pois requer menos sobrecarga da rede. O UDP é preferível para aplicativos como Voz sobre IP (VoIP). Confirmações e retransmissão atrasariam a entrega e tornariam a conversa por voz inaceitável.

O UDP também é usado por aplicativos de solicitação e resposta onde os dados são mínimos, e a retransmissão pode ser feita rapidamente. Por exemplo, o serviço de nome de domínio (DNS) usa UDP para esse tipo de transação. O cliente solicita endereços IPv4 e IPv6 para um nome de domínio conhecido de um servidor DNS. Se o cliente não receber uma resposta em um período predeterminado de tempo, ele simplesmente envia a solicitação novamente.

Por exemplo, se um ou dois segmentos de uma transmissão de vídeo ao vivo não conseguir chegar, isso criará apenas uma interrupção momentânea na transmissão. Isso pode aparecer como uma distorção na imagem ou no som, mas pode não ser notado pelo usuário. Se o dispositivo de destino considerasse os dados perdidos, a transmissão poderia atrasar, enquanto aguardasse as retransmissões, causando, portanto, grandes perdas de áudio e vídeo. Nesse caso, é melhor fornecer a melhor experiência de mídia com os segmentos recebidos e descartar a confiabilidade.

Para outras aplicações, é importante que todos os dados cheguem e que possam ser processados em sua sequência adequada. Para esses tipos de aplicativos, o TCP é usado como o protocolo de transporte. Por exemplo, aplicações como bancos de dados, navegadores e clientes de e-mail exigem que todos os dados enviados cheguem ao destino em seu estado original. Quaisquer dados ausentes podem corromper uma comunicação, tornando-a incompleta ou ilegível. Por exemplo, é importante ao acessar informações bancárias pela web certificar-se de que todas as informações são enviadas e recebidas corretamente.

Os desenvolvedores de aplicações devem escolher que tipo de protocolo de transporte é apropriado com base nas necessidades de suas aplicações. O vídeo pode ser enviado através de TCP ou UDP. Os aplicativos que transmitem áudio e vídeo armazenados normalmente usam TCP. O aplicativo usa TCP para executar buffer, sondagem de largura de banda e controle de congestionamento, a fim de controlar melhor a experiência do usuário.

Vídeo e voz em tempo real geralmente usam UDP, mas também podem usar TCP, ou UDP e TCP. Um aplicativo de videoconferência pode usar UDP por padrão, mas como muitos firewalls bloqueiam UDP, o aplicativo também pode ser enviado por TCP.

Os aplicativos que transmitem áudio e vídeo armazenados usam TCP. Por exemplo, se sua rede, repentinamente, não comportar a largura de banda necessária para a transmissão de um filme sob demanda, a aplicação interrompe a reprodução. Durante essa interrupção, você deverá ver uma mensagem de “buffering...” , enquanto o TCP age para restabelecer a transmissão. Quando todos os segmentos estão em ordem e um nível mínimo de largura de banda é restaurado, a sessão TCP é retomada e o filme retoma a reprodução.

# Visão geral do TCP

### Recursos TCP

Além de suportar as funções básicas de segmentação e remontagem de dados, o TCP também fornece os seguintes serviços:

- **Estabelece uma sessão** - O TCP é um protocolo orientado à conexão que negocia e estabelece uma conexão (ou sessão) permanente entre os dispositivos de origem e de destino antes de encaminhar qualquer tráfego. Com o estabelecimento da sessão, os dispositivos negociam o volume de tráfego esperado que pode ser encaminhado em determinado momento e os dados de comunicação entre os dois podem ser gerenciados atentamente.
- **Garante a entrega confiável** - Por várias razões, é possível que um segmento seja corrompido ou perdido completamente, pois é transmitido pela rede. O TCP garante que cada segmento enviado pela fonte chegue ao destino.
- **Fornece entrega no mesmo pedido** - Como as redes podem fornecer várias rotas que podem ter taxas de transmissão diferentes, os dados podem chegar na ordem errada. Ao numerar e sequenciar os segmentos, o TCP garante que os segmentos sejam remontados na ordem correta.
- **Suporta controle de fluxo** - os hosts de rede têm recursos limitados (ou seja, memória e poder de processamento). Quando percebe que esses recursos estão sobrecarregados, o TCP pode requisitar que a aplicação emissora reduza a taxa de fluxo de dados. Para isso, o TCP regula o volume de dados transmitido pelo dispositivo origem. O controle de fluxo pode impedir a necessidade de retransmissão dos dados quando os recursos do host receptor estão sobrecarregados.

### Cabeçalho TCP

TCP é um protocolo stateful, o que significa que ele controla o estado da sessão de comunicação. Para manter o controle do estado de uma sessão, o TCP registra quais informações ele enviou e quais informações foram confirmadas. A sessão com estado começa com o estabelecimento da sessão e termina com o encerramento da sessão.

Um segmento TCP adiciona 20 bytes (ou seja, 160 bits) de sobrecarga ao encapsular os dados da camada de aplicativo. A figura mostra os campos em um cabeçalho TCP.

![[Pasted image 20241126183751.png]]

### Campos de cabeçalho TCP
![[Pasted image 20241126183822.png]]

### Aplicações que usam TCP
O TCP é um bom exemplo de como as diferentes camadas do conjunto de protocolos TCP / IP têm funções específicas. O TCP lida com todas as tarefas associadas à divisão do fluxo de dados em segmentos, fornecendo confiabilidade, controlando o fluxo de dados e reordenando segmentos. O TCP libera a aplicação da obrigação de gerenciar todas essas tarefas. Aplicações como as mostradas na figura, podem simplesmente enviar o fluxo de dados à camada de transporte e usar os serviços TCP.
![[Pasted image 20241126183925.png]]

# Visão Geral do UDP

### Recursos UDP

O UDP é um protocolo simples, normalmente descrito nos termos do que ele não faz em comparação ao TCP.

Os recursos UDP incluem o seguinte:

- Os dados são reagrupados na ordem em que são recebidos.
- Quaisquer segmentos perdidos não são reenviados.
- Não há estabelecimento de sessão.
- O envio não é informado sobre a disponibilidade do recurso.

### Cabeçalho UDP

UDP é um protocolo sem estado, o que significa que nem o cliente nem o servidor rastreiam o estado da sessão de comunicação. Se a confiabilidade for necessária ao usar o UDP como protocolo de transporte, ela deve ser tratada pela aplicação.

Um dos requisitos mais importantes para transmitir vídeo ao vivo e voz sobre a rede é que os dados continuem fluindo rapidamente. Vídeo ao vivo e aplicações de voz podem tolerar alguma perda de dados com efeito mínimo ou sem visibilidade e são perfeitos para o UDP.

Os blocos de comunicação no UDP são chamados de datagramas ou segmentos. Esses datagramas são enviados como o melhor esforço pelo protocolo da camada de transporte.

O cabeçalho UDP é muito mais simples do que o cabeçalho TCP porque só tem quatro campos e requer 8 bytes (ou seja, 64 bits). A figura mostra os campos em um cabeçalho UDP.
![[Pasted image 20241126184145.png]]

### Campos de Cabeçalho UDP
![[Pasted image 20241126184202.png]]

### Aplicações que usam UDP
Há três tipos de aplicações que são mais adequadas para o UDP:

- **Aplicativos de vídeo e multimídia ao vivo** - Esses aplicativos podem tolerar a perda de dados, mas requerem pouco ou nenhum atraso. Os exemplos incluem VoIP e transmissão de vídeo ao vivo.
- **Solicitações simples e aplicativos de resposta** - aplicativos com transações simples em que um host envia uma solicitação e pode ou não receber uma resposta. Os exemplos incluem DNS e DHCP.
- **Aplicativos que lidam com a confiabilidade** - Comunicações unidirecionais em que o controle de fluxo, a detecção de erros, as confirmações e a recuperação de erros não são necessários ou podem ser gerenciados pelo aplicativo. Os exemplos incluem SNMP e TFTP.

A figura identifica aplicativos que exigem UDP.
![[Pasted image 20241126184248.png]]

# Números de porta

### Várias comunicações separadas

Independentemente do tipo de dados que estão sendo transportados, tanto o TCP quanto o UDP usam números de porta.

O número da porta de origem está associado ao aplicativo de origem no host local, enquanto o número da porta de destino está associado ao aplicativo de destino no host remoto.

Por exemplo, suponha que um host está iniciando uma solicitação de página da Web a partir de um servidor Web. Quando o host inicia a solicitação de página da Web, o número da porta de origem é gerado dinamicamente pelo host para identificar exclusivamente a conversa. Cada solicitação gerada por um host usará um número de porta de origem criado dinamicamente diferente. Este processo permite que várias conversações ocorram simultaneamente.

Na solicitação, o número da porta de destino é o que identifica o tipo de serviço que está sendo solicitado do servidor Web de destino. Por exemplo, quando um cliente especifica a porta 80 na porta de destino, o servidor que receber a mensagem sabe que os serviços Web são solicitados.

Um servidor pode oferecer mais de um serviço simultaneamente, como serviços web na porta 80, enquanto oferece o estabelecimento de conexão FTP (File Transfer Protocol) na porta 21.

### Pares de Sockets

As portas origem e destino são colocadas no segmento. Os segmentos são encapsulados em um pacote IP. O pacote IP contém o endereço IP de origem e destino. A combinação do endereço IP de origem e o número de porta de origem, ou do endereço IP de destino e o número de porta de destino é conhecida como um socket.

No exemplo na figura, o PC está solicitando simultaneamente serviços FTP e Web do servidor de destino.
![[Pasted image 20241126184608.png]]

O socket é usado para identificar o servidor e o serviço que está sendo solicitado pelo cliente. Um socket do cliente pode ser assim, com 1099 representando o número da porta de origem: 192.168.1.5:1099

O socket em um servidor da web pode ser 192.168.1.7:80

Juntos, esses dois sockets se combinam para formar um _par de sockets_: 192.168.1.5:1099, 192.168.1.7:80

Os sockets permitem que vários processos em execução em um cliente se diferenciem uns dos outros, e várias conexões com um processo no servidor sejam diferentes umas das outras.

Este número de porta age como um endereço de retorno para a aplicação que faz a solicitação. A camada de transporte rastreia essa porta e a aplicação que iniciou a solicitação, de modo que quando uma resposta é retornada, ela pode ser encaminhada para a aplicação correta.

### Grupos de Números de Porta

A Internet Assigned Numbers Authority (IANA) é a organização de padrões responsável por atribuir vários padrões de endereçamento, incluindo os números de porta de 16 bits. Os 16 bits usados para identificar os números de porta de origem e destino fornecem um intervalo de portas de 0 a 65535.

A IANA dividiu a gama de números nos três grupos de portos seguintes.
![[Pasted image 20241126184720.png]]
**Observação:** Alguns sistemas operacionais clientes podem usar números de porta registrados em vez de números de porta dinâmicos para atribuir portas de origem.

A tabela exibe alguns números de porta conhecidos comuns e seus aplicativos associados.
![[Pasted image 20241126184827.png]]Algumas aplicações podem usar tanto TCP quanto UDP. Por exemplo, o DNS usa o protocolo UDP quando os clientes enviam requisições a um servidor DNS. Contudo, a comunicação entre dois servidores DNS sempre usa TCP.

### O Comando netstat

Conexões TCP desconhecidas podem ser uma ameaça de segurança maior. Elas podem indicar que algo ou alguém está conectado ao host local. Às vezes é necessário conhecer quais conexões TCP ativas estão abertas e sendo executadas em um host de rede. O netstat é um utilitário de rede importante que pode ser usado para verificar essas conexões. Como mostrado abaixo, digite o comando **netstat** para listar os protocolos em uso, o endereço local e os números de porta, o endereço externo e os números de porta e o estado da conexão.

Por padrão, o comando **netstat** tentará resolver endereços IP para nomes de domínio e números de porta para aplicativos conhecidos. A **-n** opção pode ser usada para exibir endereços IP e números de porta em sua forma numérica.

# Processo de Comunicação TCP

### Processos em Servidores TCP

Um servidor individual não pode ter dois serviços atribuídos ao mesmo número de porta dentro dos mesmos serviços de camada de transporte. Por exemplo, um host executando um aplicativo de servidor web e um aplicativo de transferência de arquivos não pode ter os dois configurados para usar a mesma porta, como a porta TCP 80.

Um aplicativo de servidor ativo atribuído a uma porta específica é considerado aberto, o que significa que a camada de transporte aceita e processa os segmentos endereçados a essa porta. Qualquer solicitação de cliente que chega endereçada ao soquete correto é aceita e os dados são transmitidos à aplicação do servidor. Pode haver muitas portas abertas ao mesmo tempo em um servidor, uma para cada aplicação de servidor ativa.

### Estabelecimento de Conexão TCP

**Etapa 1. SYN**

O cliente iniciador requisita uma sessão de comunicação cliente-servidor com o servidor.

**Etapa 2. ACK e SYN**

O servidor confirma a sessão de comunicação cliente-servidor e requisita uma sessão de comunicação de servidor-cliente.

**Etapa 3. ACK**

O cliente iniciador confirma a sessão de comunicação de servidor-cliente.

### Encerramento da Sessão

Para fechar uma conexão, o flag de controle Finish (FIN) deve ser ligado no cabeçalho do segmento. Para terminar cada sessão TCP de uma via, um handshake duplo, consistindo de um segmento FIN e um segmento ACK (Acknowledgment) é usado. Portanto, para terminar uma conversação única permitida pelo TCP, quatro trocas são necessárias para finalizar ambas as sessões. O cliente ou o servidor podem iniciar o encerramento.

**Etapa 1. FIN**

Quando o cliente não tem mais dados para enviar no fluxo, ele envia um segmento com um flag FIN ligado.

**Etapa 2. ACK**

O servidor envia ACK para confirmar o recebimento de FIN para encerrar a sessão do cliente com o servidor.

**Etapa 3. FIN**

O servidor envia um FIN ao cliente para encerrar a sessão do servidor-para-cliente.

**Etapa 4. ACK**

O cliente responde com um ACK para reconhecer o FIN do servidor.

![[Pasted image 20241126185650.png]]

### Análise do Handshake Triplo do TCP

Os hosts mantêm o estado, rastreiam cada segmento de dados em uma sessão e trocam informações sobre quais dados são recebidos usando as informações no cabeçalho TCP. O TCP é um protocolo full-duplex, em que cada conexão representa duas sessões de comunicação unidirecional. Para estabelecer uma conexão, os hosts realizam um handshake triplo (three-way handshake). 

Estas são as funções do handshake de três vias:

- Estabelece que o dispositivo de destino está presente na rede.
- Ele verifica se o dispositivo de destino possui um serviço ativo e está aceitando solicitações no número da porta de destino que o cliente inicial pretende usar.
- Ele informa ao dispositivo de destino que o cliente de origem pretende estabelecer uma sessão de comunicação nesse número de porta.

Após a conclusão da comunicação, as sessões são fechadas e a conexão é encerrada. Os mecanismos de conexão e sessão ativam a função de confiabilidade do TCP.

Os seis bits no campo Bits de Controle do cabeçalho do segmento TCP são também conhecidos como flags. Uma flag (sinalizador, bandeira) é um bit que é definido como ligado (1) ou desligado (0).

Os seis bits de controle sinalizadores são os seguintes:

- **URG** - Campo de ponteiro urgente significativo.
- **ACK** - Indicador de confirmação usado no estabelecimento de conexão e encerramento de sessão.
- **PSH** - Função Push.
- **RST** - Redefina a conexão quando ocorrer um erro ou tempo limite.
- **SYN** - Sincronizar números de sequência usados no estabelecimento de conexão.
- **FIN** - Não há mais dados do remetente e usados no encerramento da sessão.

# Confiabilidade e controle de fluxo

### Confiabilidade do TCP - Entrega garantida e solicitada

A razão pela qual o TCP é o melhor protocolo para alguns aplicativos é porque, ao contrário do UDP, ele reenvia pacotes descartados e números de pacotes para indicar sua ordem correta antes da entrega. O TCP também pode ajudar a manter o fluxo de pacotes para que os dispositivos não fiquem sobrecarregados. Este tópico aborda esses recursos do TCP em detalhes.

Pode haver momentos em que os segmentos TCP não chegam ao seu destino. Outras vezes, os segmentos TCP podem chegar fora de ordem. Para que a mensagem original seja entendida pelo destinatário, todos os dados devem ser recebidos e os dados nesses segmentos devem ser remontados na ordem original. Os números de sequência são atribuídos no cabeçalho de cada pacote para alcançar esse objetivo. O número de sequência representa o primeiro byte de dados do segmento TCP.

Durante o estabelecimento de uma sessão, um número de sequência inicial (ISN) é definido. Este ISN representa o valor inicial dos bytes que são transmitidos ao aplicativo receptor. À medida que os dados são transmitidos durante a sessão, número de sequência é incrementado do número de bytes que foram transmitidos. Esse rastreamento dos bytes de dados permite que cada segmento seja identificado e confirmado de forma única. Segmentos perdidos podem então, ser identificados.

O ISN não começa em um, mas é efetivamente um número aleatório. Isso é para impedir determinados tipos de ataques maliciosos. Para simplificar os exemplos desse capítulo, usaremos um ISN de 1.

Os números de sequência do segmento indicam como remontar e reordenar os segmentos recebidos![[Pasted image 20241126190147.png]]
O processo TCP receptor coloca os dados de um segmento em um buffer receptor. Os segmentos são então colocados na ordem de sequência correta e passados para a camada de aplicativo quando remontados. Qualquer segmento que chegue com números de sequência fora de ordem são retidos para processamento posterior. Por isso, quando os segmentos com os bytes que faltavam chegam, esses segmentos são processados.

### Confiabilidade do TCP - Perda de dados e retransmissão

O número de sequência (SEQ) e o número de confirmação (ACK) são usados juntamente para confirmar o recebimento dos bytes de dados contidos nos segmentos. O número SEQ identifica o primeiro byte de dados no segmento que está sendo transmitido. O TCP usa o número de confirmação (ACK) enviado de volta à origem para indicar o próximo byte que o destino espera receber. Isto é chamado de confirmação antecipatória.

Antes de melhorias posteriores, o TCP só podia reconhecer o próximo byte esperado. Por exemplo, na figura, usando números de segmento para simplicidade, o host A envia os segmentos 1 a 10 para o host B. Se todos os segmentos chegarem, exceto os segmentos 3 e 4, o host B responderia com confirmação especificando que o próximo segmento esperado é o segmento 3. O Host A não tem idéia se outros segmentos chegaram ou não. O host A, portanto, reenviaria os segmentos 3 a 10. Se todos os segmentos reenviados chegarem com sucesso, os segmentos 5 a 10 seriam duplicados. Isso pode levar a atrasos, congestionamentos e ineficiências.
![[Pasted image 20241126190434.png]]

Hoje em dia, os sistemas operacionais de host utilizam um recurso TCP opcional chamado reconhecimento seletivo (SACK), negociado durante o handshake de três vias. Se ambos os hosts suportarem SACK, o receptor pode reconhecer explicitamente quais segmentos (bytes) foram recebidos, incluindo quaisquer segmentos descontínuos. O host de envio, portanto, só precisa retransmitir os dados ausentes. Por exemplo, na próxima figura, novamente usando números de segmento para simplicidade, o host A envia segmentos 1 a 10 para o host B. Se todos os segmentos chegarem, exceto os segmentos 3 e 4, o host B pode reconhecer que recebeu segmentos 1 e 2 (ACK 3) e reconhecer seletivamente os segmentos 5 a 10 (SACK 5-10). O host A só precisaria reenviar os segmentos 3 e 4.
![[Pasted image 20241126190512.png]]

**Nota**: O TCP normalmente envia ACKs para todos os outros pacotes, mas outros fatores além do escopo deste tópico podem alterar esse comportamento.

O TCP usa temporizadores para saber quanto tempo esperar antes de reenviar um segmento.

### Controle de Fluxo TCP - Tamanho da Janela e Confirmações

O TCP também fornece mecanismos para controle de fluxo. Controle de fluxo é a quantidade de dados que o destino pode receber e processar de forma confiável. O controle de fluxo ajuda a manter a confiabilidade da transmissão TCP definindo a taxa de fluxo de dados entre a origem e o destino em uma determinada sessão. Para realizar isso, o cabeçalho TCP inclui um campo de 16 bits chamado de tamanho da janela.

A figura mostra um exemplo de tamanho da janela e confirmações.
![[Pasted image 20241126190708.png]]

O tamanho da janela determina o número de bytes que podem ser enviados antes de esperar uma confirmação. O número de reconhecimento é o número do próximo byte esperado.

O tamanho da janela é número de bytes que o dispositivo de destino de uma sessão TCP pode aceitar e processar de uma vez. Neste exemplo, o tamanho da janela inicial do PC B para a sessão TCP é de 10.000 bytes. No caso do primeiro byte ser número 1, o último byte que PC A pode enviar sem receber uma confirmação é o byte 10.000. Isso é conhecido como janela de envio do PC A. O tamanho da janela é incluído em todos os segmentos TCP, para que o destino possa modificar o tamanho da janela a qualquer momento, dependendo da disponibilidade do buffer.

O tamanho da janela inicial é determinado quando a sessão é estabelecida durante o handshake triplo. O dispositivo de origem deve limitar o número de bytes enviados ao dispositivo de destino com base no tamanho da janela do destino. Somente depois que o dispositivo de origem receber uma confirmação de que os bytes foram recebidos, ele poderá continuar a enviar mais dados para a sessão. Normalmente, o destino não esperará que todos os bytes que a sua janela comporta sejam recebidos para responder confirmando. À medida que os bytes forem recebidos e processados, o destino enviará confirmações para informar à origem que pode continuar a enviar bytes adicionais.

Por exemplo, é típico que o PC B não espere até que todos os 10.000 bytes tenham sido recebidos antes de enviar uma confirmação. Isso significa que o PC A pode ajustar sua janela de envio ao receber confirmações do PC B. Como mostrado na figura, quando o PC A recebe uma confirmação com o número de confirmação 2.921, que é o próximo byte esperado. A janela de envio do PC A irá incrementar 2.920 bytes. Isso altera a janela de envio de 10.000 bytes para 12.920. O PC A agora pode continuar enviando até outros 10.000 bytes para o PC B, desde que não envie mais do que sua nova janela de envio em 12.920.

Um destino que envia confirmações enquanto processa os bytes recebidos e o ajuste contínuo da janela de envio de origem é conhecido como janelas deslizantes. No exemplo anterior, a janela de envio do PC A incrementa ou desliza sobre outros 2.921 bytes de 10.000 para 12.920.

Se a disponibilidade do espaço de buffer do destino diminui, ele pode reduzir o tamanho da sua janela para informar à origem que reduza o número de bytes que ela deveria enviar sem receber uma confirmação.

**Nota:** Os dispositivos hoje usam o protocolo de janelas deslizantes. O receptor normalmente envia uma confirmação após cada dois segmentos que recebe. O número de segmentos recebidos antes de ser confirmado pode variar. A vantagem de janelas deslizantes é que permite que o emissor transmita continuamente segmentos, desde que o receptor esteja reconhecendo segmentos anteriores. Os detalhes das janelas deslizantes estão fora do escopo deste curso.

### Controle de Fluxo TCP - Tamanho Máximo do Segmento (MSS)

Na figura, a fonte está transmitindo 1.460 bytes de dados dentro de cada segmento TCP. Normalmente, este é o tamanho máximo do segmento (MSS) que o dispositivo de destino pode receber. O MSS faz parte do campo de opções no cabeçalho TCP que especifica a maior quantidade de dados, em bytes, que um dispositivo pode receber em um único segmento TCP. O tamanho do MSS não inclui o cabeçalho TCP. O MSS é normalmente incluído durante o handshake de três vias.
![[Pasted image 20241126191001.png]]

Um MSS comum é 1.460 bytes ao usar IPv4. Um host determina o valor do campo de MSS subtraindo os cabeçalhos de IP e de TCP da MTU (Maximum transmission unit, Unidade máxima de transmissão) da Ethernet. Em uma interface Ethernet, a MTU padrão é 1500 bytes. Subtraindo o cabeçalho IPv4 de 20 bytes e o cabeçalho TCP de 20 bytes, o tamanho padrão do MSS será 1460 bytes, conforme mostrado na figura.
![[Pasted image 20241126191035.png]]

### Controle de Fluxo TCP - Prevenção de Congestionamento

Quando ocorre um congestionamento em uma rede, isso resulta em pacotes sendo descartados pelo roteador sobrecarregado. Quando pacotes contendo segmentos TCP não atingem seu destino, eles são deixados sem serem reconhecidos. Ao determinar a taxa na qual os segmentos TCP são enviados, mas não confirmados, a origem pode pressupor um certo nível de congestionamento da rede.

Sempre que ocorrer um congestionamento, ocorrerá a retransmissão de segmentos TCP perdidos por parte da origem. Se a retransmissão não for devidamente controlada, a retransmissão adicional dos segmentos TCP pode agravar o congestionamento. Não só novos pacotes com segmentos TCP são introduzidos na rede, como também o efeito de feedback dos segmentos retransmitidos que foram perdidos aumentarão o congestionamento. Para evitar e controlar o congestionamento, o TCP emprega alguns mecanismos para lidar com o congestionamento, temporizadores e algoritmos.

Se a origem determina que os segmentos TCP não são confirmados ou não são confirmados em tempo hábil, isso pode reduzir o número de bytes enviados antes do recebimento de uma confirmação. Conforme ilustrado na figura, o PC A detecta que há congestionamento e, portanto, reduz o número de bytes que envia antes de receber uma confirmação do PC B.
![[Pasted image 20241126191152.png]]

Observe que é a origem que está reduzindo o número de bytes não confirmados que envia e não o tamanho da janela determinado pelo destino.

# Comunicação UDP

### Baixa Sobrecarga do UDP Versus Confiabilidade

O UDP fornece transporte de dados de baixa sobrecarga, porque tem um cabeçalho de datagrama pequeno e nenhum tráfego de gerenciamento de rede.

### Remontagem do Datagrama UDP

Como ocorre com segmentos TCP, quando múltiplos datagramas UDP são enviados a um destino, eles geralmente tomam caminhos diferentes e chegam na ordem errada. O UDP não rastreia os números de sequência da forma que o TCP faz. O UDP não tem como reordernar os datagramas na sua ordem de transmissão, como mostrado na figura.

Portanto, o UDP simplesmente remonta os dados na ordem que eles foram recebidos e os encaminha para a aplicação. Se a sequência de dados for importante para a aplicação, a aplicação deverá identificar a sequência apropriada e determinar como os dados devem ser processados.
![[Pasted image 20241126191551.png]]

### Processos em Servidores e Requisições UDP

Quando as aplicações ou processos estão sendo executados, eles aceitarão os dados correspondentes ao número de porta atribuído. Quando o UDP recebe um datagrama destinado a uma destas portas, ele encaminha os dados à aplicação apropriada com base em seu número de porta.

### Processos em Clientes UDP

Assim como o TCP, a comunicação cliente servidor é iniciada por uma aplicação cliente que requisita dados de um processo em um servidor. O processo no cliente UDP seleciona dinamicamente um número de porta a partir de uma faixa de números de portas e a usa como a porta de origem para a conversa. A porta de destino será geralmente o número de porta muito conhecida ou registrada atribuído ao processo no servidor.

Depois que um cliente seleciona as portas de origem e de destino, o mesmo par de portas é usado no cabeçalho de todos os datagramas na transação. Para dados que retornam para o cliente vindos do servidor, os números da porta de origem e de destino no cabeçalho do datagrama são invertidos.