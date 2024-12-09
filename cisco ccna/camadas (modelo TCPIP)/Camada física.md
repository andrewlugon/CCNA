A camada física do modelo OSI fornece os meios para transportar os bits que formam um quadro da camada de enlace de dados no meio físico de rede. Essa camada aceita um quadro completo da camada de enlace de dados e o codifica como uma série de sinais que são transmitidos à mídia local. Os bits codificados que formam um quadro são recebidos por um dispositivo final ou por um dispositivo intermediário.

Os protocolos e operações das camadas OSI superiores são executados usando software desenvolvido por engenheiros de software e cientistas da computação. Os serviços e protocolos na suíte TCP/IP são definidos pela Internet Engineering Task Force (IETF).

A camada física consiste em circuitos eletrônicos, meios físicos e conectores desenvolvidos pelos engenheiros. Portanto, é aconselhável que os padrões que regem esse hardware sejam definidos pelas organizações de engenharia de comunicações e elétrica relevantes.

Há muitas organizações nacionais e internacionais diferentes, organizações reguladoras de governo e empresas privadas envolvidas no estabelecimento e na manutenção de padrões da camada física. Por exemplo, os padrões de hardware, mídia, codificação e sinalização da camada física são definidos e governados por essas organizações de padrões:

- International Organization for Standardization (ISO)
- Telecommunications Industry Association/Electronic Industries Association (TIA/EIA)
- União Internacional de Telecomunicações (ITU)
- Instituto Nacional de Padronização Americano (ANSI)
- Institute of Electrical and Electronics Engineers (IEEE)
- Autoridades reguladoras de telecomunicações nacionais, incluem Federal Communication Commission (FCC) nos EUA e European Telecommunications Standards Institute (ETSI)

Meios físicos diferentes aceitam a transferência de bits a taxas diferentes. A transferência de dados é geralmente discutida em termos de largura de banda. Largura de banda é a capacidade na qual um meio pode transportar dados. A largura de banda digital mede a quantidade de dados que podem fluir de um lugar para outro durante um determinado tempo. A largura de banda é normalmente medida em kilobits por segundo (kbps), megabits por segundo (Mbps) ou gigabits por segundo (Gbps). Às vezes, a largura de banda é pensada como a velocidade em que os bits viajam, no entanto, isso não é preciso. **Por exemplo, na Ethernet de 10 Mbps e 100 Mbps, os bits são enviados na velocidade da eletricidade. A diferença é o número de bits que são transmitidos por segundo.**


Os termos usados para medir a qualidade da largura de banda incluem:

- Latência;
- Rendimento;
- Dados úteis.

**Latência**

O termo latência se refere ao tempo necessário para os dados viajarem de um ponto a outro, incluindo atrasos.

Em uma internetwork ou em uma rede com vários segmentos, a taxa de transferência não pode ser mais rápida que o link mais lento no caminho da origem ao destino. Mesmo que todos ou a maioria dos segmentos tenham alta largura de banda, será necessário apenas um segmento no caminho com baixa taxa de transferência para criar um gargalo na taxa de transferência de toda a rede.

**Taxa de transferência**

Taxa de transferência é a medida da transferência de bits através da mídia durante um determinado período.

Devido a alguns fatores, geralmente a taxa de transferência não corresponde à largura de banda especificada nas implementações da camada física. A taxa de transferência geralmente é menor que a largura de banda. Existem muitos fatores que influenciam a taxa de transferência:

- A quantidade de tráfego;
- O tipo de tráfego;
- A latência criada pelo número de dispositivos de rede encontrados entre a origem e o destino.

Existem muitos testes de velocidade on-line que podem revelar a taxa de transferência de uma conexão com a Internet. A figura fornece exemplos de resultados de um teste de velocidade.

**Dados úteis**

Há uma terceira medida para avaliar a transferência de dados utilizáveis; é conhecido como goodput. Goodput é a medida de dados usáveis transferidos em um determinado período. Goodput é a taxa de transferência menos a sobrecarga de tráfego para estabelecer sessões, reconhecimentos, encapsulamento e bits retransmitidos. O goodput é sempre menor que a taxa de transferência, que geralmente é menor do que a largura de banda.


### Características do Cabeamento de Cobre

Os dados são transmitidos por cabos de cobre como pulsos elétricos. Um detector na interface de rede de um dispositivo destino tem que receber um sinal que poderá ser decodificado com êxito para corresponder ao sinal enviado. No entanto, quanto mais o sinal viaja, mais ele se deteriora. Isso se chama atenuação de sinal. Por isso, todas as mídias de cobre devem seguir limitações de distância rigorosas, conforme especificado nos padrões de orientação.

Para contrabalançar os efeitos negativos da EMI e da RFI, alguns tipos de cabos de cobre têm proteção metálica e exigem conexões devidamente aterradas.

Para contrabalançar os efeitos negativos do crosstalk, alguns tipos de cabos de cobre têm pares de cabos de circuitos opostos juntos, o que efetivamente cancela o crosstalk.

A suscetibilidade dos cabos de cobre ao ruído eletrônico também pode ser limitada usando estas recomendações:

- Selecionando o tipo ou categoria de cabo mais adequado para um determinado ambiente de rede
- Projetar uma infraestrutura de cabos para evitar fontes conhecidas e potenciais de interferência na estrutura do edifício
- Usando técnicas de cabeamento que incluem o manuseio e a terminação adequados dos cabos

Há três tipos principais de mídias de cobre usadas em redes:

![[Pasted image 20241103194157.png]]

O cabeamento de par trançado não blindado (UTP) é o meio físico de rede mais comum. O cabeamento UTP, terminado com conectores RJ-45, é usado para interconectar hosts de rede com dispositivos de rede intermediários, como comutadores e roteadores.

O par trançado blindado (STP) oferece maior proteção contra ruído do que o cabeamento UTP. No entanto, em comparação com o cabo UTP, o cabo STP é significativamente mais caro e difícil instalação. Assim como o cabo UTP, o STP usa um conector RJ-45.

Embora o cabo UTP tenha substituído essencialmente o cabo coaxial nas modernas instalações Ethernet, o design do cabo coaxial é usado nas seguintes situações:

- **Instalações sem fio** - Os cabos coaxiais conectam antenas a dispositivos sem fio. O cabo coaxial transporta a energia de radiofrequência (RF) entre as antenas e o equipamento de rádio.
- **Instalações de Internet a cabo** - Os provedores de serviços a cabo fornecem conectividade à Internet para seus clientes, substituindo partes do cabo coaxial e suportando elementos de amplificação por cabo de fibra óptica. No entanto, o cabeamento dentro das instalações do cliente ainda é coaxial.

### UTP:

A figura mostra três categorias de cabo UTP:

- A categoria 3 foi originalmente utilizada para comunicação de voz através de linhas de voz, mas mais tarde utilizada para transmissão de dados.
- As categorias 5 e 5e são utilizadas para a transmissão de dados. Categoria 5 suporta 100Mbps e Categoria 5e suporta 1000 Mbps.
- A categoria 6 tem um separador adicional entre cada par de fios para suportar velocidades mais altas. Categoria 6 suporta até 10 Gbps.
- Categoria 7 também suporta 10 Gbps.
- Categoria 8 suporta 40 Gbps.

Alguns fabricantes produzem cabos que excedem as especificações da Categoria TIA/EIA 6a e os classificam como Categoria 7.

Estes são os principais tipos de cabo obtidos com o uso de convenções de cabeamento específicas:

- **Ethernet direta** - O tipo mais comum de cabo de rede. Geralmente é usado para interconectar um host a um switch e um switch a um roteador.
- **Ethernet Crossover** - Um cabo usado para interconectar dispositivos semelhantes. Por exemplo, para conectar um switch a um switch, um host a um host ou um roteador a um roteador. No entanto, os cabos cruzados agora são considerados legados, pois as NICs usam o cruzamento de interface dependente médio (Auto-MDIX) para detectar automaticamente o tipo de cabo e fazer a conexão interna.

### Fibra Óptica

Os cabos de fibra óptica são amplamente classificados em dois tipos:

- Fibra monomodo (SMF)
- Fibra multimodo (MMF)

**Fibra monomodo**

O SMF consiste em um núcleo muito pequeno e usa a tecnologia laser cara para enviar um único raio de luz, conforme mostrado na figura. O SMF é popular em situações de longa distância que se estendem por centenas de quilômetros, como os exigidos em aplicações de telefonia de longo curso e TV a cabo.

**Fibra multimodo**

O MMF consiste em um núcleo maior e usa emissores de LED para enviar pulsos de luz. Especificamente, a luz de um LED entra na fibra multimodo em diferentes ângulos, como mostrado na figura. Popular nas LANs porque pode ser acionada por LEDs de baixo custo. Ela fornece largura de banda até 10 Gb/s por links de até 550 metros.

Agora, o cabeamento de fibra óptica é usado em quatro setores:

- **Redes corporativas** - Usadas para aplicativos de cabeamento de backbone e dispositivos de infraestrutura de interconexão.
- **FTTH (Fiber-to-the-Home)** - Usado para fornecer serviços de banda larga sempre ativos para residências e pequenas empresas.
- **Redes de longo curso** - Utilizadas por provedores de serviços para conectar países e cidades.
- **Redes de cabos submarinos** - Utilizadas para fornecer soluções confiáveis de alta velocidade e alta capacidade, capazes de sobreviver em ambientes submarinos adversos até distâncias transoceânicas. Pesquise na internet por “mapa de telegeografia de cabos submarinos” para visualizar vários mapas on-line.

### Meios sem fio

Estes são os padrões sem fio:

- **Wi-Fi (IEEE 802.11)** - Tecnologia de LAN sem fio (WLAN), geralmente chamada de Wi-Fi. A WLAN usa um protocolo baseado em contenção conhecido como acesso múltiplo / detecção de colisão de portadora (CSMA / CA). A NIC sem fio deve ouvir primeiro, antes de transmitir, para determinar se o canal de rádio está limpo. Se houver outro dispositivo sem fio transmitindo, a NIC deverá esperar até o canal estar limpo. Wi-Fi é uma marca comercial registrada da Wi-Fi Alliance. O Wi-Fi é usado com dispositivos WLAN certificados com base nos padrões IEEE 802.11.
- **Bluetooth (IEEE 802.15)** - Este é um padrão de rede pessoal sem fio (WPAN), comumente conhecido como “Bluetooth”. Ele usa um processo de emparelhamento de dispositivo para se comunicar em distâncias de 1 a 100 metros.
- **WiMAX (IEEE 802:16)** - Comumente conhecido como Interoperabilidade mundial para acesso por microondas (WiMAX), esse padrão sem fio usa uma topologia ponto a multiponto para fornecer acesso à banda larga sem fio.
- **Zigbee (IEEE 802.15.4)** - Zigbee é uma especificação usada para comunicações de baixa taxa de dados e baixa potência. Destina-se a aplicações que exigem taxas de dados de curto alcance, baixas e longa duração da bateria. Zigbee é normalmente usado para ambientes industriais e de Internet das Coisas (IoT), como interruptores de luz sem fio e coleta de dados de dispositivos médicos.