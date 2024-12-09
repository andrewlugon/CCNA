
A camada de enlace de dados do modelo OSI (Camada 2), conforme mostrado na figura, prepara os dados da rede para a rede física. A camada de enlace de dados é responsável pela placa de interface de rede (NIC) para comunicações de placa de interface de rede. A camada de enlace de dados faz o seguinte:

- Permite que as camadas superiores acessem a mídia. O protocolo de camada superior não está completamente ciente do tipo de mídia que é usado para encaminhar os dados.
- Aceita dados, geralmente pacotes de Camada 3 (ou seja, IPv4 ou IPv6), e os encapsula em quadros da Camada 2.
- Controla como os dados são colocados e recebidos na mídia.
- Troca quadros entre pontos de extremidade através da mídia de rede.
- Recebe dados encapsulados, geralmente pacotes de Camada 3, e os direciona para o protocolo de camada superior apropriado.
- Executa a detecção de erros e rejeita qualquer quadro corrompido.

Os padrões IEEE 802 LAN/MAN são específicos para LANs Ethernet, LANs sem fio (WLAN), redes pessoais sem fio (WPAN) e outros tipos de redes locais e metropolitanas. A camada de link de dados LAN/MAN IEEE 802 consiste nas seguintes duas subcamadas:

- **Logical Link Control (LLC)** - Esta subcamada IEEE 802.2 comunica entre o software de rede nas camadas superiores e o hardware do dispositivo nas camadas inferiores. Ela coloca a informação no quadro que identifica qual protocolo de camada de rede está sendo usado para o quadro. Essas informações permitem que vários protocolos da camada 3, como IPv4 e IPv6, usem a mesma interface de rede e mídia.
- **Controle de Acesso a Mídia (MAC)** - Implementa esta subcamada (IEEE 802.3, 802.11 ou 802.15) no hardware. É responsável pelo encapsulamento de dados e controle de acesso à mídia. Ele fornece endereçamento de camada de link de dados e é integrado com várias tecnologias de camada física.

A subcamada LLC pega os dados do protocolo de rede, que geralmente é um pacote IPv4 ou IPv6, e adiciona informações de controle da camada 2 para ajudar a entregar o pacote ao nó de destino. 

A subcamada MAC controla a NIC e outro hardware responsável pelo envio e recebimento de dados no meio LAN/MAN com ou sem fio.

A subcamada MAC fornece encapsulamento de dados:

- **Delimitação de quadros** - O processo de enquadramento fornece delimitadores importantes para identificar campos dentro de um quadro. Esses bits de delimitação promovem a sincronização entre os nós de transmissão e de recepção.
- **Endereçamento** - Fornece endereçamento de origem e destino para transportar o quadro da Camada 2 entre dispositivos na mesma mídia compartilhada.
- **Detecção de erro** - Inclui um trailer usado para detectar erros de transmissão.

Em cada salto ao longo do caminho, um roteador executa as seguintes funções da Camada 2:

1. Aceita um quadro de um meio;
2. Desencapsula o quadro;
3. Encapsula novamente o pacote em um novo quadro;
4. Encaminha o novo quadro apropriado para o meio desse segmento da rede física.


### Padrões da Camada de Enlace de Dados

Os protocolos da camada de enlace de dados geralmente não são definidos por RFCs (Request for Comments), ao contrário dos protocolos das camadas superiores do conjunto TCP / IP. A Internet Engineering Task Force (IETF) mantém os protocolos e serviços funcionais do conjunto de protocolos TCP / IP nas camadas superiores, mas eles não definem as funções e a operação da camada de acesso à rede TCP / IP.

As organizações de engenharia que definem padrões abertos e protocolos que se aplicam à camada de acesso à rede (ou seja, as camadas físicas e de link de dados OSI) incluem o seguinte:

- Institute of Electrical and Electronics Engineers (IEEE)
- International Telecommunication Union (ITU)
- International Organization for Standardization (ISO)
- Instituto Nacional Americano de Padronização (ANSI)

### Topologias Físicas e Lógicas

A topologia de uma rede é a organização, ou o relacionamento, dos dispositivos de rede e as interconexões entre eles.

Existem dois tipos de topologias usadas ao descrever redes LAN e WAN:

- **Topologia física** - Identifica as conexões físicas e como os dispositivos finais e intermediários (ou seja, roteadores, comutadores e pontos de acesso sem fio) são interconectados. A topologia também pode incluir a localização específica do dispositivo, como o número do quarto e a localização no rack do equipamento. As topologias físicas são geralmente ponto a ponto ou estrela.
- **Topologia lógica** - refere-se à maneira como uma rede transfere quadros de um nó para o próximo. Esta topologia identifica conexões virtuais usando interfaces de dispositivo e esquemas de endereçamento IP da Camada 3.

A camada de enlace de dados “vê” a topologia lógica da rede quando controla o acesso de dados ao meio físico. É a topologia lógica que influencia o tipo de enquadramento de rede e o controle de acesso ao meio usado.

Ponto a Ponto - Estrela - Malha

Um híbrido é uma variação ou combinação de qualquer topologia. Por exemplo, uma malha parcial é uma topologia híbrida em que alguns dispositivos finais, mas não todos, são interconectados.

### Topologia de WAN ponto a ponto

As topologias ponto a ponto físicas conectam diretamente dois nós, como mostrado na figura. Nessa organização, dois nós não têm de compartilhar o meio físico com outros hosts. Além disso, ao usar um protocolo de comunicação serial como o protocolo ponto a ponto (PPP), um nó não precisa determinar se um quadro de entrada é destinado a ele ou a outro nó. Portanto, os protocolos de enlace de dados podem ser muito simples, assim como todos os quadros no meio físico podem trafegar apenas para os dois nós ou a partir deles. O nó coloca os quadros na mídia em uma extremidade e esses quadros são retirados da mídia pelo nó na outra extremidade do circuito ponto a ponto.

**Observação:** Uma conexão ponto a ponto via Ethernet requer que o dispositivo determine se o quadro de entrada está destinado a esse nó.

Um nó de origem e destino pode ser indiretamente conectado entre si por alguma distância geográfica, usando vários dispositivos intermediários. No entanto, o uso de dispositivos físicos na rede não afeta a topologia lógica, conforme ilustrado na figura. Na figura, adicionar conexões físicas intermediárias pode não alterar a topologia lógica. A conexão lógica ponto a ponto é a mesma.

### Topologias LAN

Em LANs multiacesso, os dispositivos finais (isto é, nós) são interligados usando topologias estelares ou estelares estendidas. Neste tipo de topologia, os dispositivos finais são conectados a um dispositivo intermediário central, neste caso, um switch Ethernet. A **extended star** estende essa topologia interconectando vários switches Ethernet. As topologias em estrela e estendidas são fáceis de instalar, muito escalonáveis (fáceis de adicionar e remover dispositivos finais) e fáceis de solucionar problemas. As primeiras topologias em estrela interconectavam dispositivos finais usando hubs Ethernet

As primeiras tecnologias Ethernet e Token Ring LAN legadas incluíam dois outros tipos de topologias:

- **Barramento** - Todos os sistemas finais são encadeados e terminados de alguma forma em cada extremidade. Os dispositivos de infraestrutura, como switches, não são necessários para interconectar os dispositivos finais. As redes Ethernet herdadas costumavam ser topologias de barramento usando cabos coaxiais, porque era barato e fácil de configurar.
- **Anel** - Os sistemas finais são conectados ao respectivo vizinho formando um anel. O anel não precisa ser terminado, ao contrário da topologia de barramento. As redes de interface de dados distribuídos de fibra herdada (FDDI) e Token Ring usavam topologias de anel.

### Comunicação em half e full duplex

**Comunicação Half-duplex**

Ambos os dispositivos podem transmitir e receber no meio físico, mas não podem fazer isso simultaneamente. WLANs e topologias de barramento herdadas com hubs Ethernet usam o modo half-duplex. O half-duplex permite que apenas um dispositivo envie ou receba por vez na mídia compartilhada.

**Comunicação Full-duplex**

Ambos os dispositivos podem transmitir e receber simultaneamente na mídia compartilhada. A camada de enlace de dados supõe que o meio físico está disponível para transmissão para ambos os nós a qualquer momento. Os comutadores Ethernet operam no modo full-duplex por padrão, mas podem operar no modo half-duplex se estiverem conectados a um dispositivo como um hub Ethernet.

Em resumo, as comunicações half-duplex restringem a troca de dados a uma direção de cada vez. O modo full-duplex permite o envio e o recebimento simultâneos de dados.

É importante que duas interfaces interconectadas, como uma NIC de host e uma interface em um comutador Ethernet, operem usando o mesmo modo duplex. Caso contrário, haverá uma incompatibilidade de duplex que criará ineficiência e latência no link.

### Métodos de controle de acesso

Algumas redes multiacesso requerem regras para controlar como os dispositivos compartilham a mídia física. Existem dois métodos básicos de controle de acesso para meio físico compartilhado.

- Acesso baseado em contenção
- Acesso controlado

**Acesso baseado em Contenção** 

Em redes multiacesso baseadas em contenção, todos os nós estão operando em half-duplex, competindo pelo uso do meio. No entanto, apenas um dispositivo pode enviar por vez. Portanto, há um processo se mais de um dispositivo transmitir ao mesmo tempo. Exemplos de métodos de acesso baseados em contenção incluem o seguinte:

- Acesso múltiplo com detecção de colisão (CSMA/CD) usado em LANs Ethernet de topologia de barramento herdada
- Acesso múltiplo por operadora com prevenção de colisão (CSMA / CA) usado em LANs sem fio

**Acesso Controlado**

Em uma rede multiacesso controlada, cada nó tem seu próprio tempo para usar o meio. Esses tipos determinísticos de redes herdadas são ineficientes porque um dispositivo deve aguardar sua vez para acessar o meio. Exemplos de redes multiacesso que usam acesso controlado incluem o seguinte:

- Anel de token legados
- ARCNET legado

**Observação:** Atualmente, as redes Ethernet operam em full-duplex e não exigem um método de acesso.

### Acesso baseado em contenção - CSMA / CD

Exemplos de redes de acesso baseadas em contenção incluem o seguinte:

- LAN sem fio (usa CSMA/CA)
- LAN Ethernet de topologia de barramento legado (usa CSMA/CD)
- LAN Ethernet herdada usando um hub (usa CSMA/CD)

Essas redes operam no modo half-duplex, o que significa que apenas um dispositivo pode enviar ou receber de cada vez. Isso requer um processo que determine quando um dispositivo pode enviar e o que acontece quando vários dispositivos enviam ao mesmo tempo.

Se dois dispositivos transmitirem simultaneamente, ocorre uma colisão. Para LANs Ethernet herdadas, ambos os dispositivos detectam a colisão na rede. Esta é a parte de detecção de colisão (CD) do CSMA/CD. A NIC compara os dados transmitidos com os dados recebidos ou reconhecendo que a amplitude do sinal é maior que o normal na mídia. Os dados enviados por ambos os dispositivos serão corrompidos e precisarão ser reenviados.

### Acesso baseado em contenção - CSMA / CA

Outra forma de CSMA usada pelas WLANs IEEE 802.11 é o acesso múltiplo por detecção de portadora / prevenção de colisão (CSMA / CA).

O CMSA/CA usa um método semelhante ao CSMA/CD para detectar se a mídia está livre. O CMSA / CA usa técnicas adicionais. Em ambientes sem fio pode não ser possível para um dispositivo detectar uma colisão. O CMSA/CA não detecta colisões, mas tenta evitá-las esperando antes de transmitir. Cada dispositivo que transmite inclui o tempo necessário para a transmissão. Todos os outros dispositivos sem fio recebem essas informações e sabem quanto tempo a mídia ficará indisponível.

**Observação:** As LANs Ethernet que usam comutadores não usam um sistema baseado em contenção porque o comutador e a NIC do host operam no modo full-duplex.

### O Quadro

A camada de link de dados prepara os dados encapsulados (geralmente um pacote IPv4 ou IPv6) para o transporte pela mídia local, encapsulando-o com um cabeçalho e um trailer para criar um quadro.

O protocolo de link de dados é responsável pelas comunicações NIC para NIC dentro da mesma rede. Embora existam muitos protocolos de camada de enlace de dados diferentes que descrevem os quadros de camada de enlace de dados, cada tipo de quadro tem três partes básicas:

- Cabeçalho;
- Dados;
- Trailer.
Ao contrário de outros protocolos de encapsulamento, a camada de link de dados acrescenta informações na forma de um trailer no final do quadro.

Todos os protocolos da camada de enlace de dados encapsulam os dados dentro do campo de dados do quadro. No entanto, a estrutura do quadro e os campos contidos no cabeçalho e trailer variam de acordo com o protocolo.

Não há uma estrutura de quadro que satisfaça a todas as necessidades de todo transporte de dados através de todos os tipos de mídia. Dependendo do ambiente, a quantidade de informações de controle necessária no quadro varia para corresponder às exigências de controle de acesso ao meio físico e à topologia lógica. Por exemplo, um quadro WLAN deve incluir procedimentos para evitar colisões e, portanto, requer informações de controle adicionais quando comparado a um quadro Ethernet.

### Campos do Quadro

Os campos de quadro incluem o seguinte:

- **Sinalizadores de início e fim do quadro** Usado para identificar os limites de início e fim do quadro.
- **Endereçamento** - indica os nós de origem e destino na mídia.
- **Tipo** - identifica o protocolo da camada 3 no campo de dados.
- **Controle** - Identifica serviços especiais de controle de fluxo, como qualidade de serviço (QoS). A QoS dá prioridade ao encaminhamento para certos tipos de mensagens. Por exemplo, os quadros de voz sobre IP (VoIP) normalmente recebem prioridade porque são sensíveis ao atraso.
- **Dados** - Contém a carga útil do quadro (ou seja, cabeçalho do pacote, cabeçalho do segmento e os dados).
- **Detecção de Erro** - Incluído após os dados para formar o trailer.

Os protocolos da DLL acrescentam um trailer ao final de cada quadro. Em um processo chamado detecção de erros, o trailer determina se o quadro chegou sem erros. Ele coloca um resumo lógico ou matemático dos bits que compõem o quadro no trailer. A camada de enlace de dados adiciona detecção de erro porque os sinais na mídia podem estar sujeitos a interferências, distorções ou perdas que alterariam substancialmente os valores de bits que esses sinais representam.

Um nó de transmissão cria um resumo lógico dos conteúdos do quadro, conhecido como valor de verificação de redundância cíclica (cyclic redundancy check - CRC) Este valor é colocado no campo FCS (Sequência de Verificação de Quadro) para exibição ou conteúdo do quadro. No trailer Ethernet, o FCS fornece um método para o nó de recebimento determinar se o quadro apresentou erros de transmissão.

### Endereços da camada 2

A camada de enlace provê o endereçamento usado no transporte de quadro através de uma mídia local compartilhada. Os endereços de dispositivos nesta camada são chamados de endereços físicos. O endereçamento da camada de enlace de dados está contido no cabeçalho do quadro e especifica o nó destino do quadro na rede local. Normalmente, ele está no início do quadro, portanto, a NIC pode determinar rapidamente se ela corresponde ao seu próprio endereço de Camada 2 antes de aceitar o restante do quadro. O cabeçalho do quadro também pode conter o endereço de origem do quadro.

Diferente dos endereços lógicos de Camada 3, que são hierárquicos, os endereços físicos não indicam em qual rede o dispositivo está localizado. Em vez disso, o endereço físico é um endereço exclusivo do dispositivo específico. Um dispositivo ainda funcionará com o mesmo endereço físico da Camada 2, mesmo que o dispositivo se mova para outra rede ou sub-rede. Portanto, os endereços de Camada 2 são usados apenas para conectar dispositivos dentro da mesma mídia compartilhada, na mesma rede IP.

O endereço da camada de enlace de dados é usado apenas para entrega local. Os endereços nessa camada não têm significado além da rede local. Compare isso com a Camada 3, na qual os endereços no cabeçalho do pacote são transportados do host origem para o host destino, apesar do número de saltos de rede ao longo da rota.

Se os dados precisarem passar para outro segmento de rede, será necessário um dispositivo intermediário, como um roteador. O roteador deve aceitar o quadro com base no endereço físico e desencapsula o quadro para examinar o endereço hierárquico, que é o endereço IP. Usando o endereço IP, o roteador pode determinar a localização da rede do dispositivo de destino e o melhor caminho para alcançá-lo. Quando sabe para onde encaminhar o pacote, o roteador cria um novo quadro para o pacote e o novo quadro é enviado para o próximo segmento de rede em direção ao seu destino final.

### Quadros de LAN e WAN

Protocolos Ethernet são usados por LANs com fio. As comunicações sem fio se enquadram nos protocolos WLAN (IEEE 802.11). Esses protocolos foram projetados para redes multiacesso.

As WANs tradicionalmente usavam outros tipos de protocolos para vários tipos de topologias ponto a ponto, hub-spoke e malha completa. Alguns dos protocolos WAN comuns ao longo dos anos incluíram:

- Protocolo ponto a ponto (PPP);
- Controle de Enlace de Dados de Alto Nível (HDLC);
- Frame Relay;
- Modo de Transferência Assíncrona (ATM);
- X.25;

Esses protocolos de Camada 2 agora estão sendo substituídos na WAN por Ethernet.

Em uma rede TCP/IP, todos os protocolos de Camada 2 do modelo OSI trabalham com o IP na Camada 3 do modelo. No entanto, o protocolo de Camada 2 usado depende da topologia lógica e do meio físico.

Uma LAN normalmente usa uma tecnologia de alta largura de banda capaz de suportar um grande número de hosts. A área geográfica relativamente pequena de uma LAN (um único edifício ou um campus com vários edifícios) e sua alta densidade de usuários tornam essa tecnologia econômica.

No entanto, o uso de uma tecnologia de alta largura de banda geralmente não é economicamente viável para WANs que abrangem grandes áreas geográficas (cidades ou várias cidades, por exemplo). O custo dos links físicos de longa distância e a tecnologia usada para transportar os sinais por essas distâncias geralmente resultam em menor capacidade de largura de banda.

A diferença na largura de banda resulta normalmente no uso de diferentes protocolos para LANs e WANs.

Os protocolos da camada de enlace de dados incluem:

- Ethernet;
- 802.11 sem fio;
- Protocolo ponto a ponto (PPP);
- Controle de Enlace de Dados de Alto Nível (HDLC);
- Frame Relay.