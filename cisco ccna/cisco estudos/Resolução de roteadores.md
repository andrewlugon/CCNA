# MAC e IP

### Destino na Mesma Rede

Às vezes, um host deve enviar uma mensagem, mas ele só sabe o endereço IP do dispositivo de destino. O host precisa saber o endereço MAC desse dispositivo, mas como ele pode ser descoberto? É aí que a resolução de endereços se torna crítica.

Dois endereços principais são atribuídos a um dispositivo em uma LAN Ethernet:

- **Endereço físico (o endereço MAC)** - Usado para comunicações de NIC para NIC na mesma rede Ethernet.
- **Endereço lógico (o endereço IP)** - Usado para enviar o pacote do dispositivo de origem para o dispositivo de destino. O endereço IP de destino pode estar na mesma rede IP da fonte ou em uma rede remota.

Os endereços físicos da camada 2 (ou seja, endereços Ethernet Ethernet) são usados para entregar o quadro de enlace de dados com o pacote IP encapsulado de uma NIC para outra NIC que está na mesma rede. Se o endereço IP de destino estiver na mesma rede, o endereço MAC de destino será o do dispositivo de destino.

### Destino na Rede Remota

Quando o endereço IP de destino (IPv4 ou IPv6) estiver em uma rede remota, o endereço MAC de destino será o endereço do gateway padrão do host (ou seja, a interface do roteador).

Como os endereços IP dos pacotes IP em um fluxo de dados são associados aos endereços MAC em cada link ao longo do caminho até o destino? Para pacotes IPv4, isso é feito através de um processo chamado ARP (Address Resolution Protocol). Para pacotes IPv6, o processo é ICMPv6 Descoberta de vizinhos (ND).

### Visão geral do ARP

Cada dispositivo IP em uma rede Ethernet tem um endereço MAC Ethernet exclusivo. Quando um dispositivo envia um quadro Ethernet Layer 2, ele contém estes dois endereços:

- **Endereço MAC de destino** - O endereço MAC Ethernet do dispositivo de destino no mesmo segmento de rede local. Se o host de destino estiver em outra rede, o endereço de destino no quadro será o do gateway padrão (ou seja, roteador).
- **Endereço MAC de origem** - O endereço MAC da Ethernet NIC no host de origem.

Para enviar um pacote para outro host na mesma rede IPv4 local, um host deve saber o endereço IPv4 e o endereço MAC do dispositivo de destino. Os endereços IPv4 de destino do dispositivo são conhecidos ou resolvidos pelo nome do dispositivo. No entanto, os endereços MAC devem ser descobertos.

Um dispositivo utiliza o protocolo ARP (Address Resolution Protocol) para determinar o endereço MAC de destino de um dispositivo local quando conhece o endereço IPv4.

O ARP fornece duas funções básicas:

- Resolução de endereços IPv4 em endereços MAC
- Mantendo uma tabela de mapeamentos de endereços IPv4 para MAC

### Funções do ARP

Quando um pacote é enviado à camada de enlace de dados para ser encapsulado em um quadro Ethernet, o dispositivo consulta uma tabela em sua memória para encontrar o endereço MAC que é mapeado para o endereço IPv4. Esta tabela é armazenada temporariamente na memória RAM e denominada tabela ARP ou cache ARP.

O dispositivo emissor pesquisará em sua tabela ARP um endereço IPv4 destino correspondente a um endereço MAC.

- Se o endereço IPv4 destino do pacote estiver na mesma rede que o endereço IPv4 origem, o dispositivo pesquisará o endereço IPv4 destino na tabela ARP.
- Se o endereço IPv4 destino do pacote estiver em uma rede diferente do endereço IPv4 origem, o dispositivo pesquisará o endereço IPv4 do gateway padrão na tabela ARP.

Nos dois casos, a pesquisa é por um endereço IPv4 e um endereço MAC correspondente para o dispositivo.

Cada entrada (linha) da tabela ARP vincula um endereço IPv4 a um endereço MAC. Chamamos a relação entre os dois valores de um mapa. Isso significa simplesmente que você pode localizar um endereço IPv4 na tabela e descobrir o endereço MAC correspondente. A tabela ARP salva (armazena em cache) temporariamente o mapeamento dos dispositivos da LAN.

Se o dispositivo localizar o endereço IPv4, seu endereço MAC correspondente será usado como endereço MAC de destino no quadro. Se nenhuma entrada for encontrada, o dispositivo enviará uma requisição ARP.

Uma solicitação ARP é enviada quando um dispositivo precisa determinar o endereço MAC associado a um endereço IPv4 e não possui uma entrada para o endereço IPv4 em sua tabela ARP.

As mensagens do ARP são encapsuladas diretamente em um quadro Ethernet. Não há cabeçalho IPv4. A requisição ARP é encapsulada em um quadro Ethernet usando as seguintes informações de cabeçalho:

- **Endereço MAC de destino** - Este é um endereço de broadcast FF-FF-FF-FF-FF-FF, exigindo que todas as NICs Ethernet na LAN aceitem e processem a solicitação ARP.
- **Endereço MAC de origem** - Este é o endereço MAC do remetente da solicitação ARP.
- **Tipo** - As mensagens ARP têm um campo de tipo 0x806. Ele informa à NIC de recebimento que a parte de dados do quadro precisa ser transferida para o processo ARP.

Como as solicitações de ARP são transmissões, elas são inundadas em todas as portas pelo switch, exceto a porta de recebimento. Todas as NICs Ethernet no processo de LAN transmite e devem entregar a solicitação ARP ao seu sistema operacional para processamento. Cada dispositivo deve processar a requisição ARP para ver se o endereço IPv4 destino corresponde ao seu. Um roteador não encaminhará broadcasts pelas outras interfaces.

Somente um dispositivo na LAN terá um endereço IPv4 correspondente ao endereço IPv4 na requisição ARP. Nenhum outro dispositivo responderá.

Somente o dispositivo com o endereço IPv4 de destino associado à solicitação ARP responderá com uma resposta ARP. A resposta ARP é encapsulada em um quadro Ethernet usando as seguintes informações de cabeçalho:

- **Endereço MAC de destino** - Este é o endereço MAC do remetente da solicitação ARP.
- **Endereço MAC de origem** - Este é o endereço MAC do remetente da resposta ARP.
- **Tipo** - As mensagens ARP têm um campo de tipo 0x806. Ele informa à NIC de recebimento que a parte de dados do quadro precisa ser transferida para o processo ARP.

Apenas o dispositivo que enviou originalmente uma requisição ARP receberá a resposta ARP unicast. Depois que a resposta do ARP é recebida, o dispositivo adiciona o endereço IPv4 e o endereço MAC correspondente à sua tabela ARP. Agora os pacotes destinados a esse endereço IPv4 podem ser encapsulados em quadros com o endereço MAC correspondente.

Se nenhum dispositivo responder à requisição ARP, o pacote será descartado porque não será possível criar um quadro.

As entradas na tabela ARP têm carimbo de data/hora (timestamp). Se um dispositivo não receber um quadro de um dispositivo específico antes que o carimbo de data / hora expire, a entrada desse dispositivo será removida da tabela ARP.

Além disso, entradas de mapa estáticas podem ser inseridas em uma tabela ARP, mas isso é raro. As entradas estáticas na tabela ARP não expiram com o tempo e devem ser removidas manualmente.

**Observação:** O IPv6 usa um processo semelhante ao ARP para IPv4, conhecido como ND (ICMPv6 Descoberta de vizinhos). O IPv6 usa mensagens de requisição e de anúncio de vizinho, semelhantes a solicitações ARP e respostas ARP no IPv4.

#### Função ARP nas comunicações remotas

Quando o endereço IPv4 destino não está na mesma rede que o endereço IPv4 origem, o dispositivo de origem precisa enviar o quadro para o gateway padrão. Essa é a interface do roteador local. Sempre que um dispositivo de origem tiver um pacote com um endereço IPv4 em outra rede, ele encapsulará esse pacote em um quadro usando o endereço MAC de destino do roteador.

O endereço IPv4 do gateway padrão é armazenado na configuração IPv4 dos hosts. Quando um host cria um pacote para um destino, ele compara o endereço IPv4 destino e seu próprio endereço IPv4 para determinar se os dois endereços IPv4 estão localizados na mesma rede de Camada 3. Se o host de destino não estiver na mesma rede, a origem usará a tabela ARP para obter uma entrada com o endereço IPv4 do gateway padrão. Se não houver uma entrada, ela usará o processo de ARP para determinar um endereço MAC do gateway padrão.

Clique em Reproduzir para ver uma demonstração de uma requisição ARP e de uma resposta ARP associadas ao gateway padrão.

### Remoção de Entradas de uma Tabela ARP

Em cada dispositivo, um temporizador da cache ARP remove entradas ARP que não tenham sido usadas durante um determinado período. Os horários diferem dependendo do sistema operacional do dispositivo. Por exemplo, os sistemas operacionais Windows mais recentes armazenam entradas da tabela ARP entre 15 e 45 segundos

Os comandos também podem ser usados para remover manualmente algumas ou todas as entradas na tabela ARP. Após a remoção de uma entrada, o processo de envio de uma requisição ARP e de recebimento de uma resposta ARP deve ocorrer novamente para inserir o mapa na tabela ARP.

### Tabelas ARP

Em um roteador Cisco, **show ip arp** comando é usado para exibir a tabela ARP

Em um PC com Windows 10, o **arp -a** comando é usado para exibir a tabela ARP

### Problemas de ARP - Transmissões de ARP e falsificação de ARP

Como um quadro broadcast, uma requisição ARP é recebida e processada por todos os dispositivos na rede local. Em uma rede corporativa típica, esses broadcasts provavelmente teriam impacto mínimo no desempenho da rede. No entanto, se um grande número de dispositivos precisasse ser ligado e todos começassem a acessar serviços de rede ao mesmo tempo, poderia haver alguma redução no desempenho por um curto período. Depois que os dispositivos enviarem os broadcasts ARP iniciais e tiverem reconhecido os endereços MAC necessários, qualquer impacto na rede será minimizado.

Em alguns casos, o uso do ARP pode levar a um risco potencial à segurança. Um ator de ameaça pode usar falsificação ARP para realizar um ataque de envenenamento por ARP. Esta é uma técnica usada por um ator de ameaça para responder a uma solicitação ARP de um endereço IPv4 que pertence a outro dispositivo, como o gateway padrão. O agente da ameaça envia uma resposta ARP com seu próprio endereço MAC. O destinatário da resposta ARP adicionará o endereço MAC errado à sua tabela ARP e enviará esses pacotes ao agente de ameaça.  
  
Switches de nível corporativo incluem técnicas de mitigação conhecidas como inspeção dinâmica ARP (DAI).

# Descoberta de vizinhos de IPv6

Se sua rede estiver usando o protocolo de comunicação IPv6, o protocolo Descoberta de vizinhos ou ND é o que você precisa para corresponder endereços IPv6 aos endereços MAC.

### Mensagens de descoberta de vizinhos IPv6

O protocolo IPv6 Descoberta de vizinhos é às vezes referido como ND ou NDP. Neste curso, vamos nos referir a ele como ND. O ND fornece serviços de resolução de endereço, descoberta de roteador e redirecionamento para IPv6 usando ICMPv6. O ICMPv6 ND usa cinco mensagens ICMPv6 para executar estes serviços:

- Mensagens de solicitação de vizinho
- Mensagens de anúncio vizinho
- Mensagens de solicitação de roteador
- Mensagens de anúncio do roteador
- Redirecionar mensagem

As mensagens de solicitação de vizinho e anúncio de vizinho são usadas para mensagens de dispositivo a dispositivo, como resolução de endereço (semelhante ao ARP para IPv4). Os dispositivos incluem computadores host e roteadores.

As mensagens de solicitação de roteador e anúncio de roteador são para mensagens entre dispositivos e roteadores. Normalmente, a descoberta de roteador é usada para alocação de endereços dinâmicos e autoconfiguração de endereço sem estado (SLAAC).

**Observação:** A quinta mensagem ICMPv6 ND é uma mensagem de redirecionamento que é usada para melhor seleção do próximo salto. Isso está além do escopo deste curso.

IPv6 ND é definido no IETF RFC 4861.

### Descoberta de vizinhos IPv6 - Resolução de endereços

Assim como ARP para IPv4, os dispositivos IPv6 usam IPv6 ND para determinar o endereço MAC de um dispositivo que tem um endereço IPv6 conhecido.

As mensagens Solicitação de vizinho ICMPv6 e Anúncio de vizinho são usadas para a resolução de endereço MAC. Isso é semelhante às Solicitações ARP e Respostas ARP usadas pelo ARP para IPv4. Por exemplo, suponha que PC1 queira fazer ping em PC2 no endereço IPv6 2001:db8:acad: :11. Para determinar o endereço MAC para o endereço IPv6 conhecido, o PC1 envia uma mensagem de solicitação de vizinhos ICMPv6

As mensagens de solicitação de vizinhos ICMPv6 são enviadas usando endereços de multicast Ethernet e IPv6 especiais. Isso permite que a NIC Ethernet do dispositivo receptor determine se a mensagem de solicitação de vizinho é para si mesmo sem ter que enviá-la para o sistema operacional para processamento.

O PC2 responde à solicitação com uma mensagem de anúncio de vizinho ICMPv6 que inclui seu endereço MAC.