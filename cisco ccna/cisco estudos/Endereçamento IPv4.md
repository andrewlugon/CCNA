# Estrutura do Endereço IPv4

![[Pasted image 20241119195055.png]]

Os bits na parte de rede do endereço devem ser iguais em todos os dispositivos que residem na mesma rede. Os bits na parte de host do endereço devem ser exclusivos para identificar um host específico dentro de uma rede. Se dois hosts tiverem o mesmo padrão de bits na parte de rede especificada do fluxo de 32 bits, esses dois hosts residirão na mesma rede.

Mas como os hosts sabem qual parte dos 32 bits identifica a rede e qual identifica o host? Esse é o papel da máscara de sub-rede.

atribuir um endereço IPv4 a um host requer o seguinte:

- **Endereço IPv4** - este é o endereço IPv4 exclusivo do host.
- **Máscara de sub-rede** - É usada para identificar a parte da rede / host do endereço IPv4.

**Observação:** Um endereço IPv4 de gateway padrão é necessário para acessar redes remotas e endereços IPv4 do servidor DNS são necessários para converter nomes de domínio em endereços IPv4.

A máscara de sub-rede IPv4 é usada para diferenciar a parte da rede da parte do host de um endereço IPv4. Quando um endereço IPv4 é atribuído a um dispositivo, a máscara de sub-rede é usada para determinar o endereço de rede do dispositivo. O endereço de rede representa todos os dispositivos na mesma rede.

![[Pasted image 20241119195314.png]]

Observe que, na verdade, a máscara de sub-rede não contém a parte da rede ou host de um endereço IPv4, apenas informa ao computador onde procurar a parte do endereço IPv4 que é a parte da rede e qual parte é a parte do host.

O processo real usado para identificar a parte da rede e a parte de host é chamado de AND.

### Comprimento do Prefixo

O comprimento do prefixo é o número de bits definido como 1 na máscara de sub-rede. Está escrito em "notação de barra", que é anotada por uma barra (/) seguida pelo número de bits definido como 1. Portanto, conte o número de bits da máscara de sub-rede e preceda-o com uma barra.

Consulte a tabela para exemplos. A primeira coluna lista várias máscaras de sub-rede que podem ser usadas com um endereço de host. A segunda coluna mostra o endereço binário de 32 bits convertido. A última coluna mostra o comprimento do prefixo resultante.

![[Pasted image 20241119195618.png]]

**Observação:** Um endereço de rede também é referido como prefixo ou prefixo de rede. Portanto, o comprimento do prefixo é o número de 1 bits na máscara de sub-rede.

Ao representar um endereço IPv4 usando um comprimento de prefixo, o endereço IPv4 é gravado seguido do comprimento do prefixo sem espaços. Por exemplo, 192.168.10.10 255.255.255.0 seria gravado como 192.168.10.10/24. O uso de vários tipos de comprimentos do prefixo será discutido mais tarde. Por enquanto, o foco estará no prefixo /24 (ou seja, 255.255.255.0)

### Determinando a rede - Lógica AND

Um AND lógico é uma das três operações booleanas usadas na lógica booleana ou digital. As outras duas são OR e NOT. A operação AND é usada para determinar o endereço de rede.

AND lógico é a comparação de dois bits que produz os resultados mostrados abaixo. Observe como somente 1 AND 1 produz um 1. Qualquer outra combinação resulta em um 0.

- 1 E 1 = 1
- 0 E 1 = 0
- 1 E 0 = 0
- 0 E 0 = 0

**Observação:** Na lógica digital, 1 representa Verdadeiro e 0 representa Falso. Ao usar uma operação AND, ambos os valores de entrada devem ser Verdadeiro (1) para que o resultado seja Verdadeiro (1).

Para identificar o endereço de rede de um host IPv4, é feito um AND lógico, bit a bit, entre o endereço IPv4 e a máscara de sub-rede. Quando se usa AND entre o endereço e a máscara de sub-rede, o resultado é o endereço de rede.

Para ilustrar como AND é usado para descobrir um endereço de rede, considere um host com endereço IPv4 192.168.10.10 e máscara de sub-rede 255.255.255.0, conforme mostrado na figura:

- **Endereço de host IPv4 (192.168.10.10)** - O endereço IPv4 do host em formatos decimais e binários pontilhados.
- **Máscara de sub-rede (255.255.255.0)** - A máscara de sub-rede do host em formatos decimais e binários pontilhados.
- **Endereço de rede (192.168.10.0)** - A operação lógica E entre o endereço IPv4 e a máscara de sub-rede resulta em um endereço de rede IPv4 mostrado em formatos decimais e binários pontilhados.
![[Pasted image 20241119195851.png]]

A operação AND entre um endereço de host IPv4 e uma máscara de sub-rede resulta no endereço de rede IPv4 para este host. Neste exemplo, a operação AND entre o endereço de host 192.168.10.10 e a máscara de sub-rede 255.255.255.0 (/24) resulta no endereço de rede IPv4 192.168.10.0/24. Esta é uma operação IPv4 importante, pois informa ao host a qual rede pertence.

### Endereços de Broadcast, de Host e de Rede
![[Pasted image 20241119202428.png]]

**Endereço de rede**

Um endereço de rede é um endereço que representa uma rede específica. Um dispositivo pertence a esta rede se atender a três critérios:

- Tem a mesma máscara de sub-rede que o endereço de rede.
- Ele tem os mesmos bits de rede que o endereço de rede, conforme indicado pela máscara de sub-rede.
- Ele está localizado no mesmo domínio de difusão que outros hosts com o mesmo endereço de rede.

Um host determina seu endereço de rede executando uma operação AND entre seu endereço IPv4 e sua máscara de sub-rede.

**Endereços de host**

Endereços de host são endereços que podem ser atribuídos a um dispositivo, como um host de computador, laptop, smartphone, câmera web, impressora, roteador, etc. Uma parte do host do endereço é os bits indicados por 0 bits na máscara de sub-rede . Os endereços de host podem ter qualquer combinação de bits na parte do host, exceto para todos os 0 bits (isso seria um endereço de rede) ou todos os 1 bits (isso seria um endereço de difusão).

Todos os dispositivos dentro da mesma rede devem ter a mesma máscara de sub-rede e os mesmos bits de rede. Somente os bits do host serão diferentes e devem ser exclusivos.

Observe que na tabela, há um primeiro e último endereço de host:

- **Primeiro endereço de host** - Este primeiro host dentro de uma rede tem todos os 0 bits com o último bit (mais à direita) como um bit. Neste exemplo, é 192.168.10.1/24.
- **Último endereço de host** - Este último host dentro de uma rede tem todos os 1 bits com o último bit (mais à direita) como um bit 0. Neste exemplo, é 192.168.10.254/24.

Quaisquer endereços entre e inclusive, 192.168.10.1/24 a 192.168.10.254/24 podem ser atribuídos a um dispositivo na rede.

**Endereço de broadcast**

Um endereço de difusão é um endereço que é usado quando é necessário acessar todos os dispositivos na rede IPv4. Conforme mostrado na tabela, o endereço de difusão de rede tem todos os 1 bits na parte do host, conforme determinado pela máscara de sub-rede. Neste exemplo, o endereço de rede é 192.168.10.255/24. Um endereço de difusão não pode ser atribuído a um dispositivo.

# Unicast, broadcast e multicast IPv4

### Unicast

Transmissão unicast refere-se a um dispositivo que envia uma mensagem para outro dispositivo em comunicações um-para-um.

Um pacote unicast tem um endereço IP de destino que é um endereço unicast que vai para um único destinatário. Um endereço IP de origem só pode ser um endereço unicast, porque o pacote só pode originar-se de uma única origem. Isso independentemente de o endereço IP de destino ser unicast, broadcast ou multicast.

Os endereços de host unicast IPv4 estão no intervalo de endereços de 1.1.1.1 a 223.255.255.255. Contudo, dentro desse intervalo há muitos endereços que já são reservados para fins especiais. 

### Broadcast

Um pacote de broadcast possui um endereço IP de destino com todos os (1s) na parte do host ou 32 (um) bits.

**Note:** O IPv4 usa pacotes de difusão. No entanto, não há pacotes de difusão com IPv6.

Um pacote de difusão deve ser processado por todos os dispositivos no mesmo domínio de difusão. Um domínio de difusão identifica todos os hosts no mesmo segmento de rede. Uma transmissão pode ser direcionada ou limitada. Um broadcast direcionado é enviado para todos os hosts em uma rede específica. Por exemplo, um host na rede 172.16.4.0/24 envia um pacote para 172.16.4.255. Uma broadcast limitado é enviado para 255.255.255.255. Por padrão, os roteadores não encaminham broadcasts.

Pacotes de transmissão usam recursos na rede e fazem com que todos os hosts receptores da rede processem o pacote. Portanto, o tráfego broadcast deve ser limitado para não prejudicar o desempenho da rede ou dos dispositivos. Como os roteadores separam domínios de broadcast, subdividir as redes pode melhorar seu desempenho ao eliminar o excesso de tráfego broadcast.

**Transmissões direcionadas por IP**

Além do endereço de transmissão 255.255.255.255, há um endereço IPv4 de transmissão para cada rede. Chamado de transmissão direcionada, este endereço usa o endereço mais alto na rede, que é o endereço onde todos os bits de host são 1s. Por exemplo, o endereço de difusão direcionado para 192.168.1.0/24 é 192.168.1.255. Este endereço permite a comunicação com todos os hosts nessa rede. Para enviar dados para todos os hosts em uma rede, um host pode enviar um único pacote endereçado ao endereço de difusão da rede.

Um dispositivo que não esteja diretamente conectado à rede de destino encaminha uma transmissão direcionada por IP da mesma forma que encaminharia pacotes IP unicast destinados a um host nessa rede. Quando um pacote de difusão direcionada atinge um roteador conectado diretamente à rede de destino, esse pacote é transmitido na rede de destino.

**Observação:** Devido a preocupações de segurança e abuso prévio de usuários mal-intencionados, as transmissões direcionadas são desativadas por padrão, começando com o Cisco IOS Release 12.0 com o comando de configuração global **no ip directed-broadcasts**.

### Multicast

Ela reduz o tráfego, permitindo que um host envie um único pacote para um conjunto de hosts selecionados que participem de um grupo multicast.

Um pacote multicast é um pacote com um endereço IP de destino que é um endereço multicast. O IPv4 reservou os endereços 224.0.0.0 a 239.255.255.255 como intervalo de multicast.

Os hosts que recebem pacotes multicast específicos são chamados de clientes multicast. Os clientes multicast usam serviços solicitados por um programa cliente para se inscrever no grupo multicast.

Cada grupo multicast é representado por um único endereço IPv4 multicast de destino. Quando um host IPv4 se inscreve em um grupo multicast, o host processa pacotes endereçados tanto a esse endereço multicast como a seu endereço unicast alocado exclusivamente.

Protocolos de roteamento, como OSPF, usam transmissões multicast. Por exemplo, os roteadores habilitados com OSPF se comunicam entre si usando o endereço multicast OSPF reservado 224.0.0.5. Somente dispositivos habilitados com OSPF processarão esses pacotes com 224.0.0.5 como endereço IPv4 de destino. Todos os outros dispositivos ignorarão esses pacotes.

# Tipos de endereços IPv4

Endereços IPv4 públicos são endereços roteados globalmente entre os roteadores do provedor de serviços de Internet (ISP). No entanto, nem todos os endereços IPv4 disponíveis podem ser usados na Internet . Existem blocos de endereços (conhecidos como endereços privados) que são usados pela maioria das organizações para atribuir endereços IPv4 a hosts internos.

Em meados dos anos 90, com a introdução da World Wide Web (WWW), endereços IPv4 privados foram introduzidos devido ao esgotamento do espaço de endereços IPv4. Os endereços IPv4 privados não são exclusivos e podem ser usados internamente em qualquer rede.

**Observação:** A solução a longo prazo para o esgotamento de endereços IPv4 foi o IPv6.

![[Pasted image 20241119204621.png]]

### Roteamento para a Internet

Os pacotes com um endereço privado devem ser filtrados (descartados) ou traduzidos para um endereço público antes de encaminhar o pacote para um ISP.

Antes que o ISP possa encaminhar esse pacote, ele deve traduzir o endereço IPv4 de origem, que é um endereço privado, para um endereço IPv4 público usando a Conversão de Endereços de Rede (NAT). O NAT é usado para converter entre endereços IPv4 privados e IPv4 públicos. Isso geralmente é feito no roteador que conecta a rede interna à rede ISP. Os endereços IPv4 privados na intranet da organização serão traduzidos para endereços IPv4 públicos antes do encaminhamento para a Internet.

**Observação:** Embora um dispositivo com um endereço IPv4 privado não seja diretamente acessível a partir de outro dispositivo através da Internet, o IETF não considera endereços IPv4 privados ou NAT como medidas de segurança eficazes.

As organizações que têm recursos disponíveis para a Internet, como um servidor Web, também terão dispositivos com endereços IPv4 públicos. Como mostrado na figura, esta parte da rede é conhecida como a DMZ (zona desmilitarizada).

**Note:** Endereços IPv4 privados são comumente usados para fins educacionais em vez de usar um endereço IPv4 público que provavelmente pertence a uma organização.

### Endereços IPv4 de Uso Especial

Existem determinados endereços, como o endereço de rede e o endereço de broadcast, que não podem ser atribuídos aos hosts. Há também endereços especiais que podem ser atribuídos a hosts, mas com restrições quanto ao modo como interagem na rede.

**Endereços de loopback**

Os endereços de loopback (127.0.0.0 / 8 ou 127.0.0.1 a 127.255.255.254) são mais comumente identificados como apenas 127.0.0.1, esses são endereços especiais usados por um host para direcionar o tráfego para si próprio. Por exemplo, ele pode ser usado em um host para testar se a configuração TCP / IP está operacional

**Endereços link local**

Os endereços locais de link (169.254.0.0 / 16 ou 169.254.0.1 a 169.254.255.254) são mais conhecidos como endereços de endereçamento IP privado automático (APIPA) ou endereços auto-atribuídos. Eles são usados por um cliente DHCP do Windows para auto-configurar no caso de não existirem servidores DHCP disponíveis. Endereços de link local podem ser usados em uma conexão ponto a ponto, mas não são comumente usados para esse fim.

### Endereçamento Classful Legado

Em 1981, os endereços IPv4 foram atribuídos usando o endereço classful, conforme definido na RFC 790 ([https://tools.ietf.org/html/rfc790](https://tools.ietf.org/html/rfc790)), números atribuídos Os clientes receberam um endereço de rede com base em uma das três classes, A, B ou C. A RFC dividiu os intervalos de unicast em classes específicas da seguinte maneira:

- **Classe A (0.0.0.0/8 to 127.0.0.0/8)** - Projetado para suportar redes extremamente grandes com mais de 16 milhões de endereços de host. A Classe A usou um prefixo fixo /8 com o primeiro octeto para indicar o endereço de rede e os três octetos restantes para endereços de host (mais de 16 milhões de endereços de host por rede).
- **Classe B (128.0.0.0 /16 - 191.255.0.0 /16)** - Projetado para suportar as necessidades de redes de tamanho moderado a grande, com até aproximadamente 65.000 endereços de host. A Classe B usou um prefixo fixo /16 com os dois octetos de alta ordem para indicar o endereço de rede e os dois octetos restantes para endereços de host (mais de 65.000 endereços de host por rede).
- **Classe C (192.0.0.0 /24 - 223.255.255.0 /24)** - Projetado para suportar redes pequenas com um máximo de 254 hosts. A Classe C usou um prefixo fixo / 24 com os três primeiros octetos para indicar a rede e o octeto restante para os endereços de host (apenas 254 endereços de host por rede).

**Observação:** Há também um bloco multicast de Classe D que consiste em 224.0.0.0 a 239.0.0.0 e um bloco de endereço experimental de Classe E que consiste em 240.0.0.0 - 255.0.0.0.

Em meados da década de 1990, com a introdução da World Wide Web (WWW), o endereçamento clássico foi obsoleto para alocar de forma mais eficiente o espaço de endereços IPv4 limitado. A alocação de endereço de classe foi substituída por endereçamento sem classe, que é usado hoje. O endereçamento sem classe ignora as regras das classes (A, B, C). Endereços de rede IPv4 públicos (endereços de rede e máscaras de sub-rede) são alocados com base no número de endereços que podem ser justificados.

### Atribuição de Endereços IP

Endereços IPv4 públicos são endereços roteados globalmente pela Internet. Endereços IPv4 públicos devem ser exclusivos.

Os endereços IPv4 e IPv6 são gerenciados pela IANA (Internet Assigned Numbers Authority). A IANA gerencia e aloca blocos de endereços IP aos registros regionais de Internet (RIRs). Os cinco RIRs são mostrados na figura.

Os RIRs são responsáveis por alocar endereços IP aos ISPs que fornecem blocos de endereços IPv4 para organizações e ISPs menores. As organizações também podem obter seus endereços diretamente de um RIR (sujeito às políticas desse RIR).
![[Pasted image 20241119205559.png]]

- **AfriNIC** (Centro de Informação de Redes Africanas) - Região da África
- **APNIC** (Centro de informações de redes da Ásia-Pacífico) - Região Ásia/Pacífico
- **ARIN** (Registro Americano de Números da Internet) - Região da América do Norte
- **LACNIC** (Registro regional de endereços IP da América Latina e do Caribe) - América Latina e algumas ilhas do Caribe
- **RIPE NCC** (Centro de coordenação da rede Réseaux IP Européens) - Europa, Oriente Médio e Ásia Central

# Segmentação de rede

### Domínios de transmissão e segmentação

Em uma LAN Ethernet, os dispositivos usam transmissões e o Protocolo de Resolução de Endereços (ARP) para localizar outros dispositivos. O ARP envia difusões da Camada 2 para um endereço IPv4 conhecido na rede local para descobrir o endereço MAC associado. Os dispositivos em LANs Ethernet também localizam outros dispositivos usando serviços. Um host normalmente adquire sua configuração de endereço IPv4 usando o protocolo DHCP (Dynamic Host Configuration Protocol) que envia difusões na rede local para localizar um servidor DHCP.

Os switches propagam broadcasts por todas as interfaces, exceto a interface em que foram recebidos.

Roteadores não propagam broadcasts. Quando um roteador recebe um broadcast, ele não o encaminha por outras interfaces. Por exemplo, quando R1 recebe um broadcast na interface Gigabit Ethernet 0/0, ele não o encaminha por outra interface.

Portanto, cada interface do roteador se conecta a um domínio de broadcast e as transmissões são propagadas apenas dentro desse domínio de broadcast específico.

### Problemas com Grandes Domínios de Broadcast

Um grande domínio de broadcast é uma rede que conecta vários hosts. Um problema desse tipo de domínio é que os hosts podem gerar broadcasts em excesso e afetar a rede de forma negativa.
Isso resulta em operações de rede lentas devido à quantidade significativa de tráfego que pode causar e operações de dispositivo lentas porque um dispositivo deve aceitar e processar cada pacote de difusão.

A solução é reduzir o tamanho da rede para criar domínios de broadcast menores em um processo denominado divisão em sub-redes. Os espaços de rede menores são chamados de sub-redes.

Observação: os termos sub-rede e rede costumam ser usados de maneira intercambiável. A maioria das redes são uma sub-rede de um bloco de endereços maior.

### Razões para segmentar redes

A divisão em sub-redes reduz o tráfego total da rede e melhora seu desempenho. Além disso, permite que o administrador implemente políticas de segurança como, por exemplo, quais sub-redes podem ou não se comunicar com quais sub-redes. Outra razão é que reduz o número de dispositivos afetados pelo tráfego anormal de transmissão devido a configurações incorretas, problemas de hardware/software ou intenção mal-intencionada.

É fundamental que todos os administradores de redes entendam a divisão da rede em sub-redes. Vários métodos foram criados para ajudar a entender esse processo. Embora um pouco esmagador a princípio, preste muita atenção aos detalhes e, com a prática, a sub-rede se tornará mais fácil.

# Sub-rede de uma rede IPv4

As sub-redes IPv4 são criadas com um ou mais bits de host sendo usados como bits de rede. Isso é feito estendendo-se a máscara de sub-rede para pegar emprestado alguns dos bits da parte de host do endereço e criar bits de rede adicionais. Quanto mais bits de host forem emprestados, mais sub-redes poderão ser definidas. Quanto mais bits forem emprestados para aumentar o número de sub-redes reduz o número de hosts por sub-rede.

É mais fácil dividir redes em sub-redes nos limites dos octetos: /8, /16 e /24. A tabela identifica esses comprimentos de prefixo.
![[Pasted image 20241119210712.png]]

Para compreender como a divisão em sub-redes nos limites dos octetos pode ser útil, considere o exemplo a seguir. Suponha que uma empresa tenha escolhido o endereço privado 10.0.0.0/8 como endereço da rede interna. Esse endereço de rede pode conectar 16.777.214 hosts em um único domínio de broadcast. Obviamente, ter mais de 16 milhões de hosts em uma única sub-rede não é ideal.

A empresa ainda pode sub-rede o endereço 10.0.0.0/8 no limite de octeto de / 16, conforme mostrado na tabela. Isso daria à empresa a capacidade de definir até 256 sub-redes (isto é, 10.0.0.0/16 - 10.255.0.0/16) com cada sub-rede capaz de conectar 65.534 hosts. Observe como os dois primeiros octetos identificam a parte da rede do endereço, enquanto os dois últimos octetos são para endereços IP do host.

### Sub-rede dentro de um limite de octeto

Os exemplos mostrados até agora emprestaram bits de host dos prefixos de rede comuns / 8, / 16 e / 24. Entretanto, as sub-redes podem pedir emprestado bits de qualquer posição dos bits de host para criar outras máscaras.

Por exemplo, um endereço de rede /24 costuma ser dividido em sub-redes usando prefixos mais longos ao pedir bits emprestados do quarto octeto. Assim, o administrador tem mais flexibilidade na hora de atribuir endereços de rede a um número menor de dispositivos finais.

Para cada bit emprestado no quarto octeto, o número de sub-redes disponíveis é dobrado, enquanto reduz o número de endereços de host por sub-rede:

- **Linha /25** - O empréstimo 1 bit do quarto octeto cria 2 sub-redes que suportam 126 hosts cada.
- **Linha /26** - O empréstimo de 2 bits cria 4 sub-redes que suportam 62 hosts cada.
- **Linha /27** - O empréstimo de 3 bits cria 8 sub-redes que suportam 30 hosts cada.
- **Linha /28** - O empréstimo de 4 bits cria 16 sub-redes que suportam 14 hosts cada.
- **Linha /29** - O empréstimo de 5 bits cria 32 sub-redes que suportam 6 hosts cada.
- **Linha /30** - O empréstimo de 6 bits cria 64 sub-redes que suportam 2 hosts cada.

# Sub-rede uma barra 16 e um prefixo de barra 8

Algumas sub-redes são mais fáceis do que outras sub-redes. Este tópico explica como criar sub-redes que tenham o mesmo número de hosts.

Em uma situação que exige um número maior de sub-redes, é necessária uma rede IPv4 com mais bits de host disponíveis para empréstimo. Por exemplo, o endereço de rede 172.16.0.0 tem uma máscara padrão 255.255.0.0 ou /16. Esse endereço tem 16 bits na parte de rede e 16 bits na parte de host. Esses 16 bits da parte de host estão disponíveis para serem emprestados na criação de sub-redes.

### Crie 100 sub-redes com um prefixo barra 16

![[Pasted image 20241120150303.png]]


### Crie 1000 sub-redes com um prefixo barra 8

Para satisfazer o requisito de 100 sub-redes para a empresa, 7 bits (ou seja, 27 128 sub-redes) precisam ser emprestados (para um total de 128 sub-redes), conforme mostrado na figura.

![[Pasted image 20241120150530.png]]


omar emprestado 10 bits para criar as sub-redes, deixa 14 bits de host para cada sub-rede. Subtrair dois hosts por sub-rede (um para o endereço de rede e outro para o endereço de difusão) equivale a 214 - 2 = 16382 hosts por sub-rede. Isso significa que cada uma das 1000 sub-redes pode suportar até 16.382 hosts

# Divisão em sub-redes para atender a requisitos


### Espaço de Endereços IPv4 Privado de Sub-rede Público

- **Intranet** - Esta é a parte interna da rede de uma empresa, acessível apenas dentro da organização. Os dispositivos na intranet usam endereços IPv4 privados.
- **DMZ** - Faz parte da rede da empresa que contém recursos disponíveis para a internet, como um servidor web. Os dispositivos na DMZ usam endereços IPv4 públicos.

Tanto a intranet quanto a DMZ têm seus próprios requisitos e desafios de sub-rede.

A intranet usa espaço de endereçamento IPv4 privado. Isso permite que uma organização use qualquer um dos endereços de rede IPv4 privados, incluindo o prefixo 10.0.0.0/8 com 24 bits de host e mais de 16 milhões de hosts. Usar um endereço de rede com 24 bits de host torna a sub-rede mais fácil e flexível. Isso inclui a sub-rede em um limite de octeto usando um /16 ou /24.

Por exemplo, o endereço de rede IPv4 privado 10.0.0.0/8 pode ser sub-rede usando uma máscara /16. Conforme mostrado na tabela, isso resulta em 256 sub-redes, com 65.534 hosts por sub-rede. Se uma organização precisar de menos de 200 sub-redes, permitindo algum crescimento, isso dará a cada sub-rede endereços de host mais do que suficientes.

**E sobre a DMZ?**

Como esses dispositivos precisam ser acessíveis publicamente a partir da Internet, os dispositivos na DMZ exigem endereços IPv4 públicos. O esgotamento do espaço de endereços IPv4 público tornou-se um problema a partir de meados da década de 1990. Desde 2011, a IANA e quatro de cinco RIRs estão sem espaço de endereços IPv4. Embora as organizações estejam fazendo a transição para o IPv6, o espaço de endereço IPv4 restante permanece severamente limitado. Isso significa que uma organização deve maximizar seu próprio número limitado de endereços IPv4 públicos. Isso requer que o administrador de rede subnet seu espaço de endereço público em sub-redes com diferentes máscaras de sub-rede, a fim de minimizar o número de endereços de host não utilizados por sub-rede. Isso é conhecido como Variable Subnet Length Masking (VLSM).

### Minimizar endereços IPv4 de host não utilizados e maximizar sub-redes

Para minimizar o número de endereços IPv4 de host não utilizados e maximizar o número de sub-redes disponíveis, há duas considerações ao planejar sub-redes: o número de endereços de host necessários para cada rede e o número de sub-redes individuais necessárias.

A tabela exibe os detalhes específicos para a sub-rede de uma rede /24. Note que há um relacionamento inverso entre o número de sub-redes e o número de hosts. Quanto mais bits forem emprestados para criar sub-redes, menos bits do host permanecerão disponíveis. Se forem necessários mais endereços de host, mais bits de host serão exigidos, resultando em menos sub-redes.

O número de endereços de host exigidos na maior sub-rede determina quantos bits devem ser deixados na parte de host. Lembre-se de que dois dos endereços não podem ser usados, portanto o número utilizável de endereços pode ser calculado como 2^n -2.

Os administradores de rede precisam preparar um esquema de endereçamento da rede que acomode o máximo possível de hosts para cada rede e o número de sub-redes. O esquema de endereçamento deve permitir o crescimento do número de endereços de host por sub-rede e do número total de sub-redes.

# VLSM

Conforme mencionado no tópico anterior, os endereços públicos e privados afetam a maneira como você faria a sub-rede da rede. Há também outros problemas que afetam os esquemas de sub-rede. Um esquema de sub-rede padrão /16 cria sub-redes que cada uma tem o mesmo número de hosts. Nem todas as sub-redes criadas precisarão de tantos hosts, deixando muitos endereços IPv4 não utilizados. Talvez você precise de uma sub-rede que contenha muitos mais hosts. É por isso que a máscara de sub-rede de comprimento variável (VLSM) foi desenvolvida.

### Conservação de endereços IPv4

Devido ao esgotamento do espaço de endereços IPv4 público, tirar o máximo proveito dos endereços de host disponíveis é uma preocupação principal ao fazer sub-redes de redes IPv4.

**Observação:** O endereço IPv6 maior permite um planejamento e alocação de endereços muito mais fáceis do que o IPv4 permite. Conservar endereços IPv6 não é um problema. Esta é uma das forças motrizes para a transição para o IPv6.

Usando a divisão em sub-redes tradicional, o mesmo número de endereços é alocado para cada sub-rede. Se todas as sub-redes tiverem os mesmos requisitos para o número de hosts ou se não houver problema em conservar o espaço de endereços IPv4, esses blocos de endereços de tamanho fixo seriam eficientes. Normalmente, com endereços IPv4 públicos, esse não é o caso.

Além disso, limita o crescimento futuro porque reduz o número total de sub-redes disponíveis. Esse uso ineficiente de endereços é característico da divisão em sub-redes tradicional. A aplicação de um esquema de divisão em sub-redes tradicional a esse cenário não é muito eficaz e resulta em desperdício.

A máscara de sub-rede de comprimento variável (VLSM) foi desenvolvida para evitar o desperdício de endereços, permitindo-nos sub-rede de uma sub-rede.

Em todos os exemplos de sub-redes anteriores, a mesma máscara de sub-rede foi aplicada a todas as sub-redes. Isso significa que cada sub-rede tem o mesmo número de endereços de host disponíveis. Conforme ilustrado no lado esquerdo da figura, a sub-rede tradicional cria sub-redes de tamanho igual. Cada sub-rede em um esquema tradicional usa a mesma máscara de sub-rede. Conforme mostrado no lado direito da figura, o VLSM permite que um espaço de rede seja dividido em partes desiguais. Com a VLSM, a máscara de sub-rede vai variar de acordo com o número de bits que foram pegos emprestados para uma determinada sub-rede, ou seja, a parte “variável” da VLSM.

