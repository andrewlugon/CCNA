
Projetado para ser o sucessor do IPv4, o IPv6 tem um maior espaço de endereços de 128 bits, fornecendo 340 undecilhões de endereços (340 seguido por 36 zeros). No entanto, o IPv6 é mais do que apenas endereços maiores.

Quando a IETF começou o desenvolvimento de um sucessor para o IPv4, aproveitou para corrigir as limitações do IPv4 e incluir aprimoramentos. Um exemplo é o ICMPv6 (Internet Control Message Protocol versão 6), que inclui a resolução de endereços e a configuração automática de endereços, não encontradas no ICMP para IPv4 (ICMPv4).

A redução do espaço de endereços IPv4 tem sido o principal fator para migrar para o IPv6. À medida que África, Ásia e outras áreas do mundo ficarem mais conectadas à Internet, não haverá endereços IPv4 suficientes para acomodar esse crescimento.

### Coexistência do IPv4 com o IPv6

A IETF criou vários protocolos e ferramentas para ajudar os administradores de rede a migrarem as redes para IPv6. As técnicas de migração podem ser divididas em três categorias:

Pilha dupla:
A pilha dupla permite que IPv4 e IPv6 coexistam no mesmo segmento de rede. Os dispositivos de pilha dupla executam os protocolos IPv4 e IPv6 simultaneamente. Conhecido como IPv6 nativo, isso significa que a rede do cliente tem uma conexão IPv6 com seu ISP e é capaz de acessar o conteúdo encontrado na internet através de IPv6.

Tunelamento:
Tunelamento é um método de transporte de pacote IPv6 através de uma rede IPv4. O pacote IPv6 é encapsulado dentro de um pacote IPv4, de forma semelhante a outros tipos de dados.

Conversão:
A NAT64 (Network Address Translation 64) permite que os dispositivos habilitados para IPv6 se comuniquem com os dispositivos habilitados para IPv4 usando uma técnica de conversão semelhante à NAT IPv4. Um pacote IPv6 é traduzido para um pacote IPv4 e um pacote IPv4 é traduzido para um pacote IPv6.

# Representação do Endereço IPv6

### Formatos de Endereço IPv6

Os endereços IPv6 têm 128 bits e são escritos como uma sequência de valores hexadecimais. Cada 4 bits são representados por um único dígito hexadecimal, totalizando 32 valores hexadecimais. Os endereços IPv6 não diferenciam maiúsculas e minúsculas e podem ser escritos tanto em minúsculas como em maiúsculas.

**Formato preferido**

o formato preferencial para escrever um endereço IPv6 é x: x: x: x: x: x: x: x, com cada “x” consistindo de quatro valores hexadecimais. O termo octeto refere-se aos oito bits de um endereço IPv4. No IPv6, um hexteto é o termo não oficial usado para se referir a um segmento de 16 bits ou quatro valores hexadecimais. Cada “x” equivale a um único hexteto, 16 bits ou quatro dígitos hexadecimais.

Formato preferencial significa que o endereço IPv6 é gravado usando todos os 32 dígitos hexadecimais. Isso não significa necessariamente que é o método ideal para representar o endereço IPv6. Existem duas regras que ajudam a reduzir o número de dígitos necessários para representar um endereço IPv6.

### Regra 1 - Omitir zeros à esquerda

A primeira regra para ajudar a reduzir a notação de endereços IPv6 é omitir os 0s (zeros) à esquerda de qualquer seção de 16 bits ou hexteto. Aqui estão quatro exemplos de maneiras de omitir zeros à esquerda:

- 01AB pode ser representado como 1AB
- 09f0 pode ser representado como 9f0
- 0a00 pode ser representado como a00
- 00ab pode ser representado como ab

Essa regra se aplica somente aos 0s à esquerda, e NÃO aos 0s à direita. Caso contrário, o endereço ficaria ambíguo. Por exemplo, o hexteto “abc” poderia ser “0abc” ou “abc0”, mas essas duas representações não se referem ao mesmo valor.

### Regra 2 - Dois pontos duplos

A segunda regra para ajudar a reduzir a notação de endereços IPv6 é que o uso de dois-pontos duplo (::) pode substituir uma única sequência contígua de um ou mais segmentos de 16 bits (hextetos) compostos exclusivamente por 0s. Por exemplo, 2001:db8:cafe: 1:0:0:0:1 (0s iniciais omitidos) poderia ser representado como 2001:db8:cafe:1::1. O dois-pontos duplos (::) é usado no lugar dos três hextets all-0 (0:0:0).

Os dois-pontos em dobro (::) só podem ser usados uma vez em um endereço; caso contrário, haveria mais de um endereço resultante possível. Quando associada à técnica de omissão dos 0s à esquerda, a notação de endereço IPv6 pode ser bastante reduzida. É o chamado formato compactado.

Aqui está um exemplo do uso incorreto de dois pontos: 2001:db8::abcd::1234.

O dois-pontos duplo é usado duas vezes no exemplo acima. Aqui estão as possíveis expansões deste endereço de formato compactado incorreto:

- 2001:db8::abcd:0000:0000:1234
- 2001:db8::abcd:0000:0000:0000:1234
- 2001:db8:0000:abcd::1234
- 2001:db8:0000:0000:abcd::1234

Se um endereço tiver mais de uma cadeia contígua de todos os hextets 0, a prática recomendada é usar dois pontos duplos (::) na cadeia mais longa. Se as strings forem iguais, a primeira string deve usar dois pontos duplos (::).

# Tipos de Endereço IPv6

existem três grandes categorias de endereços IPv6:

- **Unicast** - Um endereço IPv6 unicast identifica exclusivamente uma interface em um dispositivo habilitado para IPv6.
- **Multicast** - Um endereço IPv6 multicast é usado para enviar um único pacote IPv6 para vários destinos.
- **Anycast** - Um endereço IPv6 anycast é qualquer endereço IPv6 unicast que possa ser atribuído a vários dispositivos. Um pacote enviado a um endereço de anycast é roteado para o dispositivo mais próximo que tenha esse endereço. Os endereços anycast estão fora do escopo deste curso.

Ao contrário do IPv4, o IPv6 não possui um endereço de broadcast. No entanto, há um endereço multicast para todos os nós IPv6 que fornece basicamente o mesmo resultado.

### Comprimento do Prefixo IPv6

Lembre-se de que o prefixo (a parte de rede) de um endereço IPv4 pode ser identificado pelo comprimento do prefixo (notação em barra) ou por uma máscara de sub-rede decimal com pontos. Por exemplo, o endereço IPv4 192.168.1.10 com máscara de sub-rede decimal com pontos 255.255.255.0 é equivalente a 192.168.1.10/24.

No IPv4 o /24 é chamado de prefixo. No IPv6 é chamado de comprimento do prefixo. O IPv6 não usa a notação decimal com pontos da máscara de sub-rede. Como o IPv4, o comprimento do prefixo é representado na notação de barra e é usado para indicar a parte da rede de um endereço IPv6.

O comprimento do prefixo pode variar de 0 a 128. O comprimento do prefixo IPv6 recomendado para LANs e a maioria dos outros tipos de redes é /64, conforme mostrado na figura.
![[Pasted image 20241122221739.png]]

É altamente recomendável usar um ID de interface de 64 bits para a maioria das redes. Isso ocorre porque a configuração automática de endereço sem estado (SLAAC) usa 64 bits para o ID de interface. Também facilita a criação e o gerenciamento de sub-redes.

### Outros Tipos de Endereços IPv6 Unicast

Um endereço IPv6 unicast identifica exclusivamente uma interface em um dispositivo habilitado para IPv6. Um pacote enviado a um endereço unicast é recebido pela interface à qual foi atribuído esse endereço. Semelhante ao IPv4, o endereço IPv6 origem deve ser um endereço unicast. O endereço IPv6 destino pode ser um endereço unicast ou multicast. A figura mostra os diferentes tipos de endereços unicast IPv6.
![[Pasted image 20241122221907.png]]

Ao contrário dos dispositivos IPv4 que têm apenas um único endereço, os endereços IPv6 normalmente têm dois endereços unicast:

- **Um endereço unicast global(GUA)** é semelhante a um endereço IPv4 público. São endereços de Internet roteáveis e globalmente exclusivos. GUAs podem ser configurados estaticamente ou dinamicamente distribuídos
- **Endereço LLA (Link-Local Address)** - Isso é necessário para cada dispositivo habilitado para IPv6. Os LLAs são usados para se comunicar com outros dispositivos no mesmo link local. No IPv6, o termo link se refere a uma sub-rede. Limitados a um único link. Sua exclusividade só deve ser confirmada nesse link, porque eles não são roteáveis além do link. Em outras palavras, os roteadores não encaminham pacotes com um endereço de link local origem ou destino.

### Uma observação sobre o endereço local exclusivo

Endereços locais exclusivos (intervalo fc00::/7 a fdff::/7) ainda não são comumente implementados. Portanto, este módulo abrange apenas a configuração GUA e LLA. No entanto, endereços locais exclusivos podem eventualmente ser usados para endereçar dispositivos que não devem ser acessíveis de fora, como servidores internos e impressoras.

Os endereços IPv6 unique local têm alguma semelhança com endereços privados do RFC 1918 para o IPv4, mas há diferenças significativas:

- Os endereços unique local são utilizados para endereçamento local dentro de um site ou entre um número limitado de sites.
- Os endereços unique local podem ser usados para dispositivos que nunca precisarão ou terão acesso por outra rede.
- Endereços locais exclusivos não são globalmente roteados ou traduzidos para um endereço IPv6 global.

**Observação:** Muitos locais usam a natureza privada de endereços da RFC 1918 para proteger sua rede contra possíveis riscos à segurança ou ocultá-la. No entanto, essa nunca foi a finalidade dessas tecnologias. A IETF sempre recomendou que os sites tomassem as devidas precauções de segurança em seu roteador de Internet.

### GUA IPv6

O endereço IPv6 unicast global (GUA) é globalmente exclusivo e roteável na Internet IPv6. Esses endereços são equivalentes aos endereços públicos do IPv4. O Internet Committee for Assigned Names and Numbers (ICANN), operador da Internet Assigned Numbers Authority (IANA), aloca blocos de endereço IPv6 para os cinco RIRs. No momento, somente endereços unicast globais com os primeiros três bits de 001 ou 2000::/3 estão sendo atribuídos.

A figura mostra o intervalo de valores para o primeiro hexteto onde o primeiro dígito hexadecimal para GUAs atualmente disponíveis começa com um 2 ou um 3. Isso é apenas um oitavo do espaço de endereço IPv6 total disponível, excluindo uma parte muito pequena de outros tipos de endereços unicast e multicast.

**Observação:** O endereço 2001:db8::/32 foi reservado para fins de documentação, incluindo o uso em exemplos.

![[Pasted image 20241122222812.png]]

A GUA tem três partes:

- Prefixo global de roteamento
- ID da Sub-Rede
- ID da Interface

### Estrutura IPv6 GUA

**Prefixo de roteamento global**

O prefixo global de roteamento é o prefixo (parte de rede) do endereço que é atribuído pelo provedor (como um ISP) a um cliente ou um site. Por exemplo, é comum que os ISPs atribuam um prefixo de roteamento global /48 a seus clientes. O prefixo de roteamento global geralmente varia dependendo das políticas do ISP.

A figura anterior mostra um GUA usando um prefixo de roteamento global /48. Os prefixos /48 são os prefixos de roteamento global mais comuns atribuídos e serão usados na maioria dos casos ao longo deste curso.

Por exemplo, o endereço IPv6 2001:db8:acad::/ 48 possui um prefixo de roteamento global que indica que os primeiros 48 bits (3 hextets) (2001:db8:acad) são como o ISP conhece esse prefixo (rede). Dois-pontos duplo (::) antes do comprimento de prefixo /48 significa que o restante do endereço contém apenas 0s. O tamanho do prefixo de roteamento global determina o tamanho da ID da sub-rede.

**ID da sub-rede**

O campo ID de sub-rede é a área entre o Prefixo de roteamento global e o ID da interface. Ao contrário do IPv4, onde você deve pedir bits emprestados da parte do host para criar sub-redes, o IPv6 foi projetado tendo em mente a sub-rede. A ID da sub-rede é usada por uma empresa para identificar sub-redes localmente. Quanto maior a ID da sub-rede, mais sub-redes disponíveis.

**Observação:** Muitas organizações estão recebendo um prefixo de roteamento global /32. Usar o prefixo /64 recomendado para criar um ID de interface de 64 bits, deixa um ID de sub-rede de 32 bits. Isso significa que uma organização com um prefixo de roteamento global /32 e um ID de sub-rede de 32 bits terá 4,3 bilhões de sub-redes, cada uma com 18 quintilhões de dispositivos por sub-rede. Isso é tantas sub-redes quanto há endereços IPv4 públicos!

O endereço IPv6 na figura anterior tem um prefixo de roteamento global /48, que é comum entre muitas redes corporativas. Isso torna especialmente fácil examinar as diferentes partes do endereço. Usando um tamanho típico de prefixo / 64, os quatro primeiros hexteto são para a parte da rede do endereço, com o quarto hexteto indicando o ID da sub-rede. Os quatro hextetos restantes são para a ID da interface.

**ID da interface**

A ID da interface IPv6 equivale à parte de host de um endereço IPv4. O termo ID da interface é usado porque um único host pode ter várias interfaces, cada uma com um ou mais endereços IPv6. A figura mostra um exemplo da estrutura de um GUA IPv6. É altamente recomendável que as sub-redes /64 sejam usadas na maioria dos casos. Um ID de interface de 64 bits permite 18 quintilhões de dispositivos ou hosts por sub-rede.

Uma sub-rede /64 ou prefixo (Prefixo de roteamento global + ID da sub-rede) deixa 64 bits para o ID da interface. Isso é recomendado para permitir que dispositivos habilitados para SLAAC criem seu próprio ID de interface de 64 bits. Também torna o desenvolvimento de um plano de endereçamento IPv6 simples e eficaz.

**Observação:** Ao contrário do IPv4, no IPv6 todos os endereços de host apenas com 0s ou apenas com 1s podem ser atribuídos a um dispositivo. O endereço todos-1s pode ser usado porque os endereços de broadcast não são usados dentro do IPv6. O endereço apenas de 0s também pode ser usado, mas é reservado como endereço anycast de roteadores de sub-redes e só deve ser atribuído a roteadores.

### IPv6 LLA

Um endereço IPv6 de link-local permite que um dispositivo se comunique com outros dispositivos habilitados para IPv6 no mesmo link e somente nesse link (sub-rede). Os pacotes com endereço de link local origem ou destino não podem ser roteados além do link de onde o pacote foi originado.

O GUA não é um requisito. No entanto, cada interface de rede habilitada para IPv6 deve ter um LLA.

Se um LLA não estiver configurado manualmente em uma interface, o dispositivo criará automaticamente um próprio, sem se comunicar com um servidor DHCP. Os hosts habilitados para LLA IPv6 criarão um endereço IPv6 mesmo que não tenha sido atribuído um endereço IPv6 unicast global ao dispositivo. Isso permite que dispositivos habilitados para IPv6 se comuniquem com outros dispositivos semelhantes na mesma sub-rede. Isso inclui a comunicação com o gateway padrão (roteador).

**Observação:** Normalmente, é o LLA do roteador, e não a GUA, que é usado como o gateway padrão para outros dispositivos no link.

Há duas maneiras pelas quais um dispositivo pode obter um LLA:

- **Estaticamente** - Isso significa que o dispositivo foi configurado manualmente.
- **Dinamicamente** - Isso significa que o dispositivo cria seu próprio ID de interface usando valores gerados aleatoriamente ou usando o método de Identificador Único Extended (EUI), que usa o endereço MAC do cliente juntamente com bits adicionais.

# Configuração Estática do GUA e do LLA

### Configuração de GUA estática em um roteador

A maioria dos comandos de configuração e verificação do IPv6 no Cisco IOS são semelhantes aos seus equivalentes no IPv4. Em muitos casos, a única diferença é o uso de **ipv6** no lugar **ip** de dentro dos comandos.

Por exemplo, o comando Cisco IOS para configurar um endereço IPv4 em uma interface é **ip address** _ip-address subnet-mask._ Em contraste, o comando para configurar um GUA IPv6 em uma interface é **ipv6 address** ipv6-address/prefix-length.

Observe que não há espaço entre _ipv6-address_ e _prefix-length._
![[Pasted image 20241124201613.png]]

### Configuração de GUA estática em um Host Windows

Assim como ocorre no IPv4, a configuração de endereços estáticos em clientes não escala para ambientes maiores. Por esse motivo, a maioria dos administradores de redes IPv6 permite a atribuição dinâmica de endereços IPv6.

Há duas maneiras de um dispositivo obter um endereço IPv6 unicast global automaticamente:

- Configuração automática de endereço stateless (SLAAC)
- Com estado DHCPv6

O SLAAC e o DHCPv6 são abordados no tópico seguinte.

**Observação:** Quando o DHCPv6 ou o SLAAC é usado, o LLA do roteador será especificado automaticamente como o endereço de gateway padrão.

### Configuração estática de um endereço Unicast local de link

A configuração manual do LLA permite criar um endereço reconhecível e fácil de lembrar. Geralmente, só é necessário criar endereços de link local reconhecíveis nos roteadores. Isso é benéfico porque os LLAs do roteador são usados como endereços de gateway padrão e no roteamento de mensagens de anúncio.

Os LLAS podem ser configurados manualmente usando o comando **ipv6 address** **link-local** _ipv6-link-local-address_. Quando um endereço começa com esse hextet dentro do intervalo de fe80 a febf, o **link-local** parâmetro deve seguir o endereço.

![[Pasted image 20241124201844.png]]

Os LLAs configurados estaticamente são usados para torná-los mais facilmente reconhecíveis como pertencentes ao roteador R1. Neste exemplo, todas as interfaces do roteador R1 foram configuradas com um LLA que começa com **fe80::1:**_n_ e um dígito exclusivo à direita “n”. O “**1**” representa o roteador R1.

Seguindo a mesma sintaxe do roteador R1, se a topologia incluísse o roteador R2, ele teria suas três interfaces configuradas com os LLAS fe80::2:1, fe80::2:2 e fe80: 2:3.

**Observação:** O mesmo LLA pode ser configurado em cada link, desde que seja exclusivo nesse link. Isso é possível porque as interfaces de link local só precisam ser exclusivas nesse link. No entanto, a prática comum é criar um LLA diferente em cada interface do roteador para facilitar a identificação do roteador e da interface específica.

# Endereçamento dinâmico para GUAs IPv6

Se você não quiser configurar as GUAs IPv6 estaticamente, não precisa se preocupar. A maioria dos dispositivos obtém suas GUAs IPv6 dinamicamente. Este tópico explica como esse processo funciona usando mensagens de anúncio de roteador (RA) e solicitação de roteador (RS). Este tópico fica bastante técnico, mas quando você entende a diferença entre os três métodos que um anúncio de roteador pode usar, bem como o processo EUI-64 para criar um ID de interface difere de um processo gerado aleatoriamente, você terá dado um grande salto em sua experiência IPv6!

Para o GUA, um dispositivo obtém o endereço dinamicamente através de mensagens ICMPv6 (Internet Control Message Protocol versão 6). Os roteadores IPv6 enviam mensagens ICMPv6 de RA a cada 200 segundos para todos os dispositivos habilitados para IPv6 na rede. Uma mensagem de RA também é enviada em resposta a um host que envie uma mensagem ICMPv6 de RS (Solicitação de Roteador).
![[Pasted image 20241124202824.png]]
1. As mensagens RS são enviadas a todos os roteadores IPv6 por hosts solicitando informações de endereçamento.
2. Mensagens RA são enviadas para todos os nós IPv6. Se o Método 1 (somente SLAAC) for usado, o RA incluirá informações de prefixo de rede, prefixo e gateway padrão.

As mensagens de RA estão em interfaces Ethernet de roteador IPv6. O roteador deve estar habilitado para roteamento IPv6, que não está habilitado por padrão. Para ativar um roteador como roteador IPv6, deve ser usado o comando de **ipv6 unicast-routing** configuração global ipv6 unicast-routing.

A mensagem ICMPv6 de RA é uma sugestão para um dispositivo sobre como obter um endereço IPv6 unicast global. A decisão final é do sistema operacional do dispositivo. A mensagem ICMPv6 de RA inclui:

- **Prefixo de rede e comprimento do prefixo** - Informa ao dispositivo a que rede ele pertence.
- **Endereço do gateway padrão** - É um endereço LLA IPv6, o endereço IPv6 origem da mensagem de RA.
- **Endereços DNS e nome de domínio** - Endereços de servidores DNS e um nome de domínio.

Existem três métodos para mensagens RA:

- **Method 1: SLAAC** - “Eu tenho tudo o que você precisa, incluindo o prefixo, comprimento do prefixo e endereço de gateway padrão.”
- **Method 2: SLAAC com um servidor DHCPv6 sem estado** - "Aqui estão as minhas informações, mas você precisa obter outras informações, como endereços DNS, de um servidor DHCPv6 sem estado".
- **Method 3: DHCPv6 com estado (sem SLAAC)** - “Posso dar-te o seu endereço de gateway padrão. Você precisa pedir a um servidor DHCPv6 com estado para todas as suas outras informações.”

### Método 1 - SLAAC

SLAAC é um método que permite que um dispositivo crie seu próprio GUA sem os serviços do DHCPv6. Com SLAAC, os dispositivos dependem das mensagens ICMPv6 de RA (Anúncio de Roteador) do roteador local para obter as informações necessárias.

Por padrão, a mensagem de RA sugere que o dispositivo de recebimento use as informações dessa mensagem para criar seu próprio endereço IPv6 unicast global e para todas as demais informações. Os serviços de um servidor DHCPv6 não são obrigatórios.

SLAAC é stateless, o que significa que não existe servidor central (por exemplo, um servidor DHCPv6 stateful) alocando endereços unicast globais e mantendo uma lista de dispositivos e seus endereços. Com SLAAC, o dispositivo cliente usa as informações da mensagem de RA para criar seu próprio endereço unicast global. Como mostrado na Figura , as duas partes do endereço são criadas da seguinte forma:

- **Prefixo** - Isso é anunciado na mensagem RA.
- **ID da Interface** - Isso usa o processo EUI-64 ou gera um número aleatório de 64 bits, dependendo do sistema operacional do dispositivo.

### Opção 2 de RA - SLAAC e DHCPv6 stateless

Uma interface de roteador pode ser configurada para enviar um anúncio de roteador usando SLAAC e DHCPv6 sem estado.

Como mostrado na figura, com esse método, a mensagem RA sugere que os dispositivos usem o seguinte:

- SLAAC para criar seu próprio IPv6 GUA
- O LLA do roteador, que é o endereço IPv6 de origem RA, como o endereço de gateway padrão
- Um servidor DHCPv6 stateless para obter outras informações como o endereço de um servidor DNS e um nome de domínio

**Observação:** Um servidor DHCPv6 stateless distribui endereços do servidor DNS e nomes de domínio. Não atribui GUAs.
![[Pasted image 20241125200333.png]]

### Método 3 - DHCPv6 com estado

Uma interface de roteador pode ser configurada para enviar um RA usando apenas DHCPv6 com estado.

O DHCPv6 stateful é semelhante ao DHCP para IPv4. Um dispositivo pode receber automaticamente suas informações de endereçamento, incluindo uma GUA, tamanho do prefixo e os endereços dos servidores DNS de um servidor DHCPv6 com monitoração de estado.

Como mostrado na figura, com esse método, a mensagem RA sugere que os dispositivos usam o seguinte:

- O LLA do roteador, que é o endereço IPv6 de origem RA, como o endereço de gateway padrão
- Um servidor DHCPv6 stateful para obter o endereço unicast global, o endereço do servidor DNS, o nome do domínio e todas as demais informações.
![[Pasted image 20241125200518.png]]

Um servidor DHCPv6 stateful aloca e mantém uma lista dos dispositivos que recebem endereços IPv6. O DHCP para IPv4 é stateful.

**Observação:** O endereço de gateway padrão só pode ser obtido dinamicamente a partir da mensagem RA. O servidor DHCPv6 stateless ou stateful não fornece o endereço de gateway padrão.

### Processo EUI-64 ou Gerado Aleatoriamente

Quando a mensagem de RA é SLAAC ou SLAAC com DHCPv6 stateless, o cliente deve gerar sua própria ID da interface. O cliente conhece a parte de prefixo do endereço da mensagem de RA, mas deve criar sua própria ID da interface. A ID da interface pode ser criada por meio do processo EUI-64 ou de um número de 64 bits gerado aleatoriamente, como mostrado na Figura 1.
![[Pasted image 20241125200707.png]]

### Processo EUI-64

A IEEE definiu o identificador exclusivo estendido (EUI) ou processo EUI-64 modificado. Esse processo usa o endereço MAC Ethernet de 48 bits de um cliente e insere outros 16 bits no meio do endereço MAC de 48 bits para criar uma ID da interface de 64 bits.

Geralmente representados em hexadecimal, os endereços MAC de Ethernet são compostos de duas partes:

- **Identificador Organizacional Exclusivo (OUI)** - O OUI é um código de 24 bits do fornecedor (6 dígitos hexadecimais) atribuído pela IEEE.
- **Identificador de dispositivo** - O identificador de dispositivo é um valor exclusivo de 24 bits (6 dígitos hexadecimais) com um OUI em comum.

Uma ID da interface EUI-64 é representada em binário e composta por três partes:

- OUI de 24 bits do endereço MAC do cliente, mas o sétimo bit (o bit universal/local (U/L)) é invertido. Isso significa que, se o sétimo bit for 0, ele se tornará 1, e vice-versa.
- O valor de 16 bits fffe (em hexadecimal) inserido.
- Identificador de dispositivo de 24 bits do endereço MAC do cliente.

O processo EUI-64 está ilustrado na Figura 2, usando o endereço MAC Gigabit Ethernet de R1 fc99:4775:cee0.
![[Pasted image 20241125200848.png]]

A saída de exemplo para o comando **ipconfig** mostra o GUA IPv6 sendo criado dinamicamente usando o SLAAC e o processo EUI-64. Uma maneira fácil de identificar que um endereço provavelmente foi criado usando o EUI-64**fffe** é o localizado no meio do ID da interface.

A vantagem do EUI-64 é o endereço MAC Ethernet que pode ser usado para determinar a ID da interface. Ele também permite que os administradores de rede rastreiem facilmente um endereço IPv6 para um dispositivo final usando o endereço MAC exclusivo. No entanto, isso causou preocupações de privacidade entre muitos usuários que se preocupavam que seus pacotes pudessem ser rastreados para o computador físico real. Devido a essas preocupações, poderá ser utilizada uma ID da interface gerada de forma aleatória.
![[Pasted image 20241125200947.png]]

### IDs da Interface Geradas Aleatoriamente

Dependendo do sistema operacional, um dispositivo pode usar uma ID da interface gerada de forma aleatória em vez de usar o endereço MAC e o processo EUI-64. Por exemplo, do Windows Vista em diante, o Windows usa uma ID da interface gerada de forma aleatória em vez de uma criada com o EUI-64. O Windows XP e os sistemas operacionais Windows anteriores usavam o EUI-64.

Depois que a ID da interface for estabelecida, seja pelo processo de EUI-64 ou por geração aleatória, ela poderá ser combinada a um prefixo IPv6 da mensagem de RA para criar um endereço unicast global, como mostra a Figura 4.
![[Pasted image 20241125201039.png]]


# Endereçamento Dinâmico para LLAs IPv6

### LLAs dinâmicos

Todos os dispositivos IPv6 devem ter um IPv6 LLA. Assim como IPv6 GUAs, você também pode criar LLAs dinamicamente. Independentemente de como você cria seus LLAS (e seus GUAs), é importante que você verifique toda a configuração de endereço IPv6. Este tópico explica a verificação de configuração de LLAs e IPv6 gerados dinamicamente.

A Figura 1 mostra que o endereço de link local é criado dinamicamente com o prefixo FE80::/10 e que a ID da interface é criada por meio do processo EUI-64 ou por um número de 64 bits gerado aleatoriamente.
![[Pasted image 20241125201604.png]]

### LLAs dinâmicos no Windows

Sistemas operacionais, como o Windows, normalmente usarão o mesmo método para um GUA criado pelo SLAAC e um LLA atribuído dinamicamente. Veja as áreas destacadas nos exemplos a seguir que foram mostrados anteriormente.
![[Pasted image 20241125201650.png]]

### LLAs dinâmicos em Cisco Routers

Os roteadores Cisco criam automaticamente um endereço IPv6 de link local sempre que um endereço unicast global é atribuído à interface. Por padrão, os roteadores Cisco IOS usam o EUI-64 para gerar a ID da interface de todos os endereços de link local em interfaces IPv6. Em interfaces seriais, o roteador usará o endereço MAC de uma interface Ethernet. Lembre-se de que um endereço de link local deve ser exclusivo somente nesse link ou rede. No entanto, uma desvantagem ao usar o endereço link local atribuído dinamicamente é sua longa ID de interface, o que faz com que seja um desafio identificar e lembrar os endereços atribuídos.

Para tornar mais fácil reconhecer esses endereços em roteadores e lembrar deles, é comum configurar estaticamente endereços IPv6 de link local nos roteadores.

### Comandos

**show ipv6 interface brief**
O comando **show ipv6 interface brief** exibe o endereço MAC das interfaces Ethernet. EUI-64 usa esse endereço MAC para gerar a ID da interface para o endereço de link local. Além disso, o comando **show ipv6 interface brief** exibe a saída abreviada para cada uma das interfaces. A saída [up/up] na mesma linha que a interface indica que o estado da Camada 1/Camada 2 da interface. Isso é o mesmo que as colunas de status e de protocolo no comando IPv4 equivalente.

Observe que aqui cada interface tem dois endereços IPv6. O segundo endereço para cada interface é o GUA que foi configurado. O primeiro endereço, que começa com FE80, é o endereço de link local unicast da interface. Lembre-se de que o endereço de link local será automaticamente adicionado à interface quando um endereço unicast global for atribuído.

Além disso, observe que o endereço de link local da serial 0/0/0 de R1 é o mesmo da sua interface Gigabit Ethernet 0/0. Como as interfaces seriais não têm endereços MAC Ethernet, o Cisco IOS usa o endereço MAC da primeira interface Ethernet disponível. Isso é possível porque as interfaces de link local só precisam ser exclusivas nesse link.

**show ipv6 route**

o comando **show ipv6 route** pode ser usado para verificar se foram instalados redes IPv6 e endereços IPv6 específicos na tabela de roteamento IPv6. O comando **show ipv6 route** exibirá somente redes IPv6, não redes IPv4.

Na tabela de rotas, Um **C** ao lado de uma rota indica que se trata de uma rede diretamente conectada. Quando a interface de um roteador está configurada com um endereço unicast global e se encontra no estado “up/up”, o prefixo IPv6 e o comprimento do prefixo são adicionados à tabela de roteamento IPv6 como uma rota conectada.

**Observação:** O **L** indica uma rota local, o endereço IPv6 específico atribuído à interface. Isto não é um LLA. Os endereços de link local não são incluídos na tabela de roteamento do roteador, pois não são endereços roteáveis.

O endereço IPv6 unicast global configurado na interface também é instalado na tabela de roteamento como uma rota local. A rota local tem um prefixo /128. As rotas locais são usadas pela tabela de roteamento para processar de forma eficiente pacotes com um endereço destino igual ao endereço da interface do roteador.

**ping**

O comando **ping** para IPv6 é idêntico ao comando usado em IPv4, exceto pelo fato de ser usado um endereço IPv6. Ao fazer ping de um roteador para um endereço de link local, o Cisco IOS solicitará que o usuário escolha a interface de saída. Como o endereço de link local de destino pode estar em um ou mais de seus links ou redes, o roteador precisa saber para qual interface enviar o ping.

# Endereços IPv6 Multicast

### Endereços IPv6 Multicast Atribuídos

Anteriormente neste módulo, você aprendeu que existem três grandes categorias de endereços IPv6: unicast, anycast e multicast. Este tópico entra em mais detalhes sobre endereços multicast.

Os endereços IPv6 multicast são semelhantes aos endereços IPv4 multicast. Lembre-se de que um endereço multicast é usado para enviar um único pacote a um ou mais destinos (grupo multicast). Os endereços multicast IPv6 têm o prefixo ff00::/8.

**Observação:** Os endereços multicast podem ser apenas endereços de destino e não endereços de origem.

Há dois tipos de endereços IPv6 multicast:

- Endereços multicast conhecidos
- Endereços multicast do nó solicitados

### Endereços comuns de multicast IPv6.

Endereços comuns de multicast IPv6 são atribuídos. Os endereços multicast atribuídos são endereços multicast reservados para grupos predefinidos de dispositivos. Um endereço multicast atribuído é um único endereço usado para acessar um grupo de dispositivos que executam um serviço ou um protocolo comum. Os endereços multicast atribuídos são usados no contexto com protocolos específicos, como o DHCPv6.

Estes são dois grupos multicast atribuídos ao IPv6 comuns:

- **ff02::1 Grupo multicast de todos os nós** -Este é um grupo multicast ao qual todos os dispositivos habilitados para IPv6 se juntam. Um pacote enviado para esse grupo é recebido e processado por todas as interfaces IPv6 no link ou rede. Isso tem o mesmo efeito que um endereço de broadcast em IPv4. Um roteador IPv6 envia mensagens RA ICMPv6 ao grupo multicast de todos os nós.
- **ff02::2 Grupo multicast de todos os roteadores** - This is a multicast group that all IPv6 routers join. A router becomes a member of this group when it is enabled as an IPv6 router with the **ipv6 unicast-routing** comando de configuração global. Um pacote enviado para esse grupo é recebido e processado por todos os roteadores IPv6 no link ou rede.

### Endereços IPv6 Multicast do nó solicitado

Um endereço multicast do nó solicitado". é semelhante ao endereço multicast all-nodes. A vantagem do endereço multicast do nó solicitado". é que ele é mapeado para um endereço multicast Ethernet especial. Isso permite que a placa de rede Ethernet filtre o quadro, examinando o endereço MAC de destino sem enviá-lo ao processo IPv6 para ver se o dispositivo é o alvo pretendido do pacote IPv6.
![[Pasted image 20241125203032.png]]

# Sub-rede de uma rede IPv6

### Sub-rede usando o ID de sub-rede

Lembre-se que, com o IPv4, devemos pedir bits emprestados da parte do host para criar sub-redes. Isso ocorre porque a sub-rede foi um pensamento tardio com IPv4. No entanto, o IPv6 foi projetado com a sub-rede em mente. Um campo de ID de sub-rede separado no GUA IPv6 é usado para criar sub-redes.

![[Pasted image 20241125203209.png]]

O benefício de um endereço de 128 bits é que ele pode suportar sub-redes e hosts mais do que suficientes por sub-rede, para cada rede. Conservação de endereços não é um problema. Por exemplo, se o prefixo de roteamento global for /48, e usando um 64 bits típico para o ID de interface, isso criará um ID de sub-rede de 16 bits:

- **ID de sub-rede de 16 bits** - Cria até 65.536 sub-redes.
- **ID da interface de 64 bits** - Suporta até 18 quintilhões de endereços IPv6 de host por sub-rede (ou seja, 18.000.000.000.000.000.000).

**Observação:** A sub-rede no ID da interface de 64 bits (ou parte do host) também é possível, mas raramente é necessária.

A divisão de IPv6 em sub-redes também é mais fácil de implementar do que no IPv4, porque não há necessidade da conversão em binário. Para determinar a próxima sub-rede disponível, basta contar em ordem crescente em hexadecimal.

![[Pasted image 20241125203336.png]]

### Alocação de Sub-Redes IPv6

Com mais de 65.536 sub-redes para escolher, a tarefa do administrador de redes é projetar um esquema lógico de endereçamento da rede.

Conforme mostrado na figura, a topologia de exemplo requer cinco sub-redes, uma para cada LAN e também para o link serial entre R1 e R2. Ao contrário do exemplo para IPv4, com IPv6 a sub-rede de link serial terá o mesmo comprimento de prefixo que as LANs. Embora isso possa parecer "desperdiçar" endereços, a conservação de endereços não é uma preocupação ao usar o IPv6.

![[Pasted image 20241125203441.png]]

![[Pasted image 20241125203521.png]]
