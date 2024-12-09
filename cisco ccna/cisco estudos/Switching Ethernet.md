
Ela opera na camada de enlace de dados e na camada física. É uma família de tecnologias de rede definidas nos padrões IEEE 802.2 e 802.3. A Ethernet suporta larguras de banda de dados do seguinte:

- 10 Mbps
- 100 Mbps
- 1000 Mbps (1 Gbps)
- 10,000 Mbps (10 Gbps)
- 40,000 Mbps (40 Gbps)
- 100,000 Mbps (100 Gbps)

Lembre-se de que LLC e MAC têm as seguintes funções na camada de link de dados:

- **Subcamada LLC Sublayer** - Essa subcamada IEEE 802.2 se comunica entre o software de rede nas camadas superiores e o hardware do dispositivo nas camadas inferiores. Ela coloca a informação no quadro que identifica qual protocolo de camada de rede está sendo usado para o quadro. Essas informações permitem que vários protocolos da camada 3, como IPv4 e IPv6, usem a mesma interface de rede e mídia.
- **Subcamada MAC** - Esta subcamada (IEEE 802.3, 802.11 ou 802.15 por exemplo) é implementada em hardware e é responsável pelo encapsulamento de dados e controle de acesso a mídia. Ele fornece endereçamento de camada de link de dados e é integrado com várias tecnologias de camada física.

### Campos de um Quadro Ethernet

O tamanho mínimo de quadro Ethernet é 64 bytes e o máximo é 1518 bytes. Isso inclui todos os bytes do campo de endereço MAC de destino através do campo FCS (Frame Check Sequence). O campo de preâmbulo não é incluído ao descrever o tamanho do quadro.

Qualquer quadro com comprimento menor que 64 bytes é considerado um"fragmento de colisão" ou um "quadro desprezível" e é automaticamente descartado pelas estações receptoras. Quadros com mais de 1.500 bytes de dados são considerados “jumbo” ou “baby giant”.

Se o tamanho de um quadro transmitido for menor que o mínimo ou maior que o máximo, o dispositivo receptor descarta o quadro. É provável que quadros perdidos sejam resultado de colisões ou outros sinais indesejados. Eles são considerados inválidos. Os quadros jumbo geralmente são suportados pela maioria dos switches e NICs Fast Ethernet e Gigabit Ethernet.
![[Pasted image 20241117164911.png]]

# Endereços MAC Ethernet

Ao usar hexadecimal, os zeros à esquerda são sempre exibidos para concluir a representação de 8 bits. Por exemplo, na tabela, o valor binário 0000 1010 é mostrado em hexadecimal como 0A.

Números hexadecimais são frequentemente representados pelo valor precedido por **0x** (por exemplo, 0x73) para distinguir entre valores decimal e hexadecimais na documentação.

O hexadecimal também pode ser representado por um subscript 16, ou o número hexadecimal seguido por um H (por exemplo, 73H).

Talvez seja necessário converter entre valores decimal e hexadecimais. Se tais conversões forem necessárias, converta o valor decimal ou hexadecimal em binário e, em seguida, converta o valor binário em decimal ou hexadecimal, conforme apropriado.

Um endereço MAC Ethernet é um endereço de 48 bits expresso usando 12 dígitos hexadecimais
Como um byte é igual a 8 bits, também podemos dizer que um endereço MAC tem 6 bytes de comprimento.

Todos os endereços MAC devem ser exclusivos do dispositivo Ethernet ou da interface Ethernet. Para garantir isso, todos os fornecedores que vendem dispositivos Ethernet devem se registrar no IEEE para obter um código hexadecimal exclusivo de 6 (ou seja, 24 bits ou 3 bytes) chamado identificador exclusivo organizacionalmente (OUI).

Quando um fornecedor atribui um endereço MAC a um dispositivo ou interface Ethernet, o fornecedor deve fazer o seguinte:

- Use sua OUI atribuída como os primeiros 6 dígitos hexadecimais.
- Atribua um valor exclusivo nos últimos 6 dígitos hexadecimais.

Portanto, um endereço MAC Ethernet consiste em um código OUI do fornecedor hexadecimal 6 seguido por um valor hexadecimal atribuído ao fornecedor 6

Por exemplo, suponha que a Cisco precisa atribuir um endereço MAC exclusivo a um novo dispositivo. O IEEE atribuiu à Cisco um OUI de **00-60-2F**. A Cisco configuraria o dispositivo com um código de fornecedor exclusivo, como **3A-07-BC**. Portanto, o endereço MAC Ethernet desse dispositivo seria **00-60-2F-3A-07-BC.**

Às vezes, o endereço MAC é referido como endereço gravado de fábrica (BIA, burned-in-address) porque o endereço é codificado na memória somente leitura (ROM) na NIC. Isso significa que o endereço é codificado no chip da ROM permanentemente.

**Observação:** Nos modernos sistemas operacionais de PC e NICs, é possível alterar o endereço MAC no software. Isso é útil para tentar obter acesso a uma rede que filtre com base no BIA. Consequentemente, a filtragem ou o controle de tráfego com base no endereço MAC não é mais tão seguro.

Quando o computador é inicializado, a NIC copia seu endereço MAC da ROM para a RAM. Quando um dispositivo está encaminhando uma mensagem para uma rede Ethernet, o cabeçalho Ethernet inclui:

- **Endereço MAC de origem** - Este é o endereço MAC da NIC do dispositivo de origem.
- **Endereço MAC de destino** - Este é o endereço MAC da NIC do dispositivo de destino.

Quando uma NIC recebe um quadro Ethernet, examina o endereço MAC de destino para verificar se corresponde ao endereço MAC físico armazenado na RAM. Se não houver correspondência, o dispositivo descartará o quadro. Caso haja, ele passará o quadro para cima nas camadas OSI, onde o processo de desencapsulamento ocorre.

**Note:** As NICs Ethernet também aceitarão quadros se o endereço MAC de destino for uma transmissão ou um grupo multicast do qual o host é membro.

### Endereço MAC Unicast

O processo que um host de origem usa para determinar o endereço MAC de destino associado a um endereço IPv4 é conhecido como ARP (Address Resolution Protocol). O processo que um host de origem usa para determinar o endereço MAC de destino associado a um endereço IPv6 é conhecido como ND (Neighbour Discovery Discovery).

**Observação:** O endereço MAC de origem deve ser sempre unicast.

### Endereço MAC Broadcast

Um quadro de transmissão Ethernet é recebido e processado por cada dispositivo na LAN Ethernet. Os recursos de uma transmissão Ethernet são os seguintes:

- Possui um endereço MAC de destino de FF-FF-FF-FF-FF-FF em hexadecimal (48 números binários (sendo eles no valor de 0 ou 1)).
- É inundada todas as portas de switch Ethernet, exceto a porta de entrada.
- Ele não é encaminhado por um roteador.

Se os dados encapsulados forem um pacote de transmissão IPv4, isso significa que o pacote contém um endereço IPv4 de destino que possui todos os 1s na parte do host. Essa numeração no endereço significa que todos os hosts naquela rede local (domínio de broadcast) receberão e processarão o pacote.

### Endereço MAC Multicast

Um quadro de multicast Ethernet é recebido e processado por um grupo de dispositivos na LAN Ethernet que pertencem ao mesmo grupo de multicast. Os recursos de um multicast Ethernet são os seguintes:

- Há um endereço MAC de destino 01-00-5E quando os dados encapsulados são um pacote multicast IPv4 e um endereço MAC de destino de 33-33 quando os dados encapsulados são um pacote multicast IPv6.
- Há outros endereços MAC de destino multicast reservados para quando os dados encapsulados não são IP, como STP (Spanning Tree Protocol) e LLDP (Link Layer Discovery Protocol).
- São inundadas todas as portas de switch Ethernet, exceto a porta de entrada, a menos que o switch esteja configurado para espionagem multicast.
- Ele não é encaminhado por um roteador, a menos que o roteador esteja configurado para rotear pacotes multicast.

Se os dados encapsulados forem um pacote multicast IP, os dispositivos que pertencem a um grupo multicast recebem um endereço IP do grupo multicast. O intervalo de endereços multicast IPv4 é 224.0.0.0 a 239.255.255.255. O intervalo de endereços multicast IPv6 começa com ff00::/8. Como os endereços multicast representam um grupo de endereços (às vezes chamado de grupo de hosts), eles só podem ser utilizados como destino de um pacote. A origem sempre será um endereço unicast.

Assim como nos endereços unicast e broadcast, o endereço IP multicast requer um endereço MAC multicast correspondente para entregar quadros em uma rede local. O endereço MAC multicast está associado e usa informações de endereçamento do endereço multicast IPv4 ou IPv6.

# A Tabela de Endereços MAC

Um switch Ethernet da camada 2 usa endereços MAC da camada 2 para tomar decisões de encaminhamento. Desconhece completamente os dados (protocolo) que estão sendo transportados na parte de dados do quadro, como um pacote IPv4, uma mensagem ARP ou um pacote ND IPv6. O switch toma suas decisões de encaminhamento com base apenas nos endereços MAC Ethernet da camada 2.

Um switch Ethernet examina sua tabela de endereços MAC para tomar uma decisão de encaminhamento para cada quadro, ao contrário dos hubs Ethernet herdados que repetem bits em todas as portas, exceto a porta de entrada.

**Observação:** A tabela de endereços MAC às vezes é chamada de tabela de memória de conteúdo endereçável (CAM). Embora o termo "tabela CAM" seja muito comum, neste curso nós a chamaremos de tabela de endereços MAC.

Todo quadro que entra em um switch é verificado quanto ao aprendizado de novas informações. Isso é feito examinando o endereço MAC de origem do quadro e o número da porta em que o quadro entrou no comutador. Se o endereço MAC de origem não existe, é adicionado à tabela juntamente com o número da porta de entrada. Se o endereço MAC de origem existir, o switch atualizará o cronômetro de atualização para essa entrada na tabela. Por padrão, a maioria dos switches Ethernet mantém uma entrada na tabela por 5 minutos.

**Nota:** Se o endereço MAC de origem não existir na tabela, mas em uma porta diferente, o switch tratará isso como uma nova entrada. A entrada é substituída usando o mesmo endereço MAC, mas com o número de porta mais atual.

Se o endereço MAC de destino for um endereço unicast, o switch procurará uma correspondência entre o endereço MAC de destino do quadro e uma entrada em sua tabela de endereços MAC. Se o endereço MAC de destino estiver na tabela, ele encaminhará o quadro pela porta especificada. Se o endereço MAC de destino não estiver na tabela, o switch encaminhará o quadro por todas as portas, exceto a de entrada. Isso é chamado de unicast desconhecido.

**Nota:** Se o endereço MAC de destino for um broadcast ou multicast, o quadro também inundará todas as portas, exceto a porta de entrada.

#### Anotações:
Quando um quadro eh enviado e não está na tabela MAC do switch  o quadro é encaminhado para todas as portas disponíveis (excerto a de entrada) e o endereço MAC de origem é adicionado na tabela MAC:

![[Pasted image 20241117173345.png]]

# Métodos de encaminhamento e velocidades de switches

Com os switches Cisco, existem realmente dois métodos de encaminhamento de quadros e há boas razões para usar um em vez do outro, dependendo da situação.

Os switches usam um dos seguintes métodos de encaminhamento para o switching (comutação) de dados entre suas interfaces de rede:

- **Switching store-and-forward** - Este método de encaminhamento de quadros recebe o quadro inteiro e calcula o CRC. O CRC usa uma fórmula matemática, baseada no número de bits (valores 1) no quadro, para determinar se o quadro recebido apresenta erro. Se o CRC é válido, o switch procura o endereço de destino, que determina a interface de saída. Em seguida, o quadro é encaminhado para fora da porta correta.
- **Switching cut-through** - Esse método de encaminhamento de quadros encaminha o quadro antes de ser totalmente recebido. Pelo menos o endereço de destino do quadro deve ser lido para que o quadro possa ser encaminhado.

Uma grande vantagem da troca de armazenamento e encaminhamento é que ele determina se um quadro tem erros antes de propagar o quadro. Quando um erro é detectado em um quadro, o switch o descarta. O descarte de quadros com erros reduz o consumo de largura de banda por dados corrompidos. O switch store-and-forward é necessário para a análise de qualidade de serviço (QoS) em redes convergentes onde a classificação de quadros para priorização de tráfego é necessária. Por exemplo, os fluxos de dados de voz sobre IP (VoIP) precisam ter prioridade sobre o tráfego de navegação na web.

### Switching cut-through

No switching cut-through, o switch atua nos dados assim que eles são recebidos, mesmo que a transmissão não tenha sido concluída. O switch armazena em buffer apenas o quadro suficiente para ler o endereço MAC de destino, para que possa determinar para qual porta deve encaminhar os dados. O endereço MAC de destino está localizado nos primeiros 6 bytes do quadro após o preâmbulo. O switch consulta o endereço MAC de destino na tabela de switching, determina a porta da interface de saída e encaminha o quadro ao seu destino pela porta de switch designada. O switch não realiza nenhuma verificação de erros no quadro.

Há duas formas de switching cut-through:

- **Comutação Fast-forward** - A comutação de avanço rápido oferece o menor nível de latência. e encaminha imediatamente um pacote depois de ler o endereço de destino. Como o switching fast-forward começa o encaminhamento antes de receber todo o pacote, alguns pacotes podem ser retransmitidos com erros. Isso ocorre com pouca freqüência e a NIC de destino descarta o pacote com defeito após o recebimento. No modo fast-forward, a latência é medida do primeiro bit recebido até o primeiro bit transmitido. Switching fast-forward é o método cut-through típico de switching.
- **Comutação Fragment-free** - Na alternância sem fragmentos, o switch armazena os primeiros 64 bytes do quadro antes de encaminhar. Esse tipo de switching pode ser encarado como um compromisso entre o switching store-and-forward e o switching fast-forward. O motivo de o switching fragment-free armazenar somente os primeiros 64 bytes do quadro é que a maioria dos erros e das colisões de rede ocorre durante os primeiros 64 bytes. O switching fragment-free tenta melhorar o switching fast-forward executando uma pequena verificação de erros nos primeiros 64 bytes do quadro para garantir que não ocorra uma colisão antes de encaminhar o quadro. O switching fragment-free é um compromisso entre a alta latência e a alta integridade do switching store-and-forward e a baixa latência e a integridade reduzida do switching fast-forward.

Alguns switches são configurados para executar o switching cut-through por porta até que um limite de erro definido pelo usuário seja atingido e, depois, mudam automaticamente para store-and-forward. Quando a taxa de erros fica abaixo do limite, a porta retorna automaticamente para o switching cut-through.

### Buffers de Memória em Switches

Um switch Ethernet pode usar uma técnica de armazenamento de quadros em buffers antes de enviá-los. O buffer também pode ser usado quando a porta de destino está ocupada devido ao congestionamento. O switch armazena o quadro até que ele possa ser transmitido.

Como mostrado na tabela, existem dois métodos de buffer de memória:

![[Pasted image 20241117173954.png]]

O buffer de memória compartilhada também resulta na capacidade de armazenar quadros maiores com potencialmente menos quadros descartados. Isso é importante com a comutação assimétrica, que permite taxas de dados diferentes em portas diferentes, como ao conectar um servidor a uma porta de switch de 10 Gbps e PCs a portas de 1 Gbps.

### MDIX Automático

A maioria dos dispositivos de switch agora suporta o recurso de (Auto-MDIX) interface dependente automática. Quando ativado, o switch detecta automaticamente o tipo de cabo conectado à porta e configura as interfaces de acordo. Com isso, você pode utilizar um cabo cruzado ou direto para conexões a uma porta 10/100/1000 de cobre no switch, seja qual for o tipo de dispositivo na outra extremidade da conexão.

O recurso auto-MDIX é ativado por padrão em switches que executam o Cisco IOS Release 12.2 (18) SE ou posterior. No entanto, o recurso pode ser desativado. Por esse motivo, você sempre deve usar o tipo de cabo correto e não confiar no recurso Auto-MDIX. O Auto-MDIX pode ser reativado usando o comando de configuração de **mdix auto** interface.