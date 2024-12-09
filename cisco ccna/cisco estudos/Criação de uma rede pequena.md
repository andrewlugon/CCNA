
# Dispositivos em uma Rede Pequena

### Topologias de Redes Pequenas

Essa pequena rede requer um roteador, um switch e um ponto de acesso sem fio para conectar usuários com fio e sem fio, um telefone IP, uma impressora e um servidor. Redes pequenas geralmente têm uma única conexão WAN fornecida por DSL, cabo ou conexão Ethernet.

As redes grandes exigem que um departamento de TI mantenha, proteja e solucione problemas de dispositivos de rede e proteja dados organizacionais. O gerenciamento de uma rede pequena exige muitas das mesmas qualificações profissionais exigidas para o gerenciamento de uma rede grande. Pequenas redes são gerenciadas por um técnico de TI local ou por um profissional contratado.

### Seleção de Dispositivos para uma Rede Pequena

Como redes grandes, redes pequenas exigem planejamento e design para atender aos requisitos do usuário. O planejamento assegura que todos os requisitos, fatores de custo e opções de implantação recebam a devida consideração.

Uma das primeiras considerações de design é o tipo de dispositivos intermediários a serem usados para oferecer suporte à rede.

**Custo**
O custo de um switch ou roteador é determinado por sua capacidade e recursos. Isso inclui o número e os tipos de portas disponíveis e a velocidade do backplane. Outros fatores que influenciam o custo são recursos de gerenciamento de rede, tecnologias de segurança incorporadas e tecnologias de comutação avançadas opcionais. As despesas com o cabeamento necessário à conexão de cada dispositivo na rede também devem ser consideradas. Outro elemento importante que afeta as avaliações de custo é a quantidade de redundância a ser incorporada na rede.

**Velocidade e tipos de portas / interfaces**
A escolha do número e do tipo de portas em um roteador ou switch é uma decisão importante. Os computadores mais novos possuem NICs de 1 Gbps incorporadas. Alguns servidores podem até ter portas de 10 Gbps. Embora seja mais caro, a escolha de dispositivos da Camada 2 que podem acomodar velocidades maiores permite que a rede evolua sem substituir os dispositivos centrais.

**Expansibilidade**
Os dispositivos de rede estão disponíveis em configurações físicas fixas e modulares. Os dispositivos de configuração fixa têm um número e tipo específico de portas ou interfaces e não podem ser expandidos. Os dispositivos modulares possuem slots de expansão para adicionar novos módulos à medida que os requisitos evoluem. Os switches são disponibilizados com portas adicionais para uplinks de alta velocidade. Roteadores podem ser usados para conectar diferentes tipos de redes. Deve-se ter cuidado ao selecionar os módulos e interfaces apropriados para as mídias específicas.

**Recursos e serviços do sistema operacional**
Os dispositivos de rede devem ter sistemas operacionais que possam suportar os requisitos da organização, como os seguintes:

- Switching de Camada 3
- Tradução de Endereço de Rede (NAT)
- Protocolo de Configuração Dinâmica de Host (DHCP)
- Segurança
- Qualidade de Serviço (QoS - Quality-of-Service).
- VoIP (Voice over IP)

### Endereçamento IP para uma rede pequena

Ao implementar uma rede, crie um esquema de endereçamento IP e use-o. Todos os hosts e dispositivos em uma inter rede devem ter um endereço exclusivo.

Os dispositivos que serão fatoriais no esquema de endereçamento IP incluem o seguinte:

- Dispositivos do usuário final - O número e o tipo de conexão (ou seja, com fio, sem fio, acesso remoto)
- Servidores e dispositivos periféricos (por exemplo, impressoras e câmeras de segurança)
- Dispositivos intermediários, incluindo comutadores e pontos de acesso

É recomendável planejar, documentar e manter um esquema de endereçamento IP baseado no tipo de dispositivo. O uso de um esquema de endereçamento IP planejado facilita a identificação de um tipo de dispositivo e a solução de problemas, como por exemplo, ao solucionar problemas de tráfego de rede com um analisador de protocolo.

A organização requer três LANs de usuário (ou seja, 192.168.1.0/24, 192.168.2.0/24 e 192.168.3.0/24). A organização decidiu implementar um esquema de endereçamento IP consistente para cada LAN 192.168.x.0/24 usando o seguinte plano:
![[Pasted image 20241129175629.png]]

Observe que os intervalos de endereços IP atribuíveis foram alocados deliberadamente em limites de sub-rede para simplificar o resumo do tipo de grupo. Por exemplo, suponha que outro switch com endereço IP 192.168.2.6 seja adicionado à rede. Para identificar todos os switches em uma diretiva de rede, o administrador pode especificar o endereço de rede resumido 192.168.x.4/30.

### Redundância em uma Rede Pequena

Outra parte importante no projeto de rede é a confiabilidade. Em geral, mesmo as pequenas empresas confiam muito em suas redes para operações comerciais. Uma falha na rede pode sair bem cara.

Para manter um alto grau de confiabilidade, _redundância_ é necessária no design da rede. A redundância ajuda a eliminar os pontos únicos de falha.

Há várias maneiras de se efetuar redundância em uma rede. A redundância pode ser efetuada com a instalação de equipamento duplicado, mas também com o fornecimento de links de rede duplicados para áreas críticas, como mostrado na figura.
![[Pasted image 20241129175741.png]]
Redes pequenas geralmente fornecem um único ponto de saída para a Internet por meio de um ou mais gateways padrão. Se o roteador falhar, a rede inteira perderá a conectividade com a Internet. Por essa razão, pode ser aconselhável para pequenas empresas contratar um segundo provedor de serviços como backup.

### Gerenciamento de Tráfego
O objetivo de um bom design de rede, mesmo para uma pequena rede, é aumentar a produtividade dos funcionários e minimizar o tempo de inatividade da rede. O administrador de redes deve considerar os vários tipos de tráfego e o tratamento deles no projeto de rede.

Os roteadores e comutadores em uma rede pequena devem ser configurados para rastrear o tráfego em tempo real, como voz e vídeo, de maneira possível em relação a outro tráfego de dados. De fato, um bom design de rede implementará qualidade de serviço (QoS) para classificar o tráfego cuidadosamente de acordo com a prioridade, conforme mostrado na figura.
![[Pasted image 20241129175838.png]]
O enfileiramento com prioridade tem quatro filas. A fila de prioridade alta é sempre esvaziada primeiro.

# Aplicações e Protocolos de Redes Pequenas

### Aplicações Comuns

A rede é tão útil quanto as aplicações que estão nela. Há duas formas de programas de software ou processos que fornecem acesso à rede: aplicações de rede e serviços da camada de aplicação.

**Aplicações de rede**

Aplicações são programas de software usados para se comunicarem pela rede. Algumas aplicações de usuário final reconhecem a rede, o que significa que elas implementam protocolos da camada de aplicação e conseguem se comunicar diretamente com as camadas inferiores da pilha de protocolos. Clientes de e-mail e navegadores Web são exemplos desse tipo de aplicação.

**Serviços de camada de aplicativo**

Outros programas podem precisar da assistência dos serviços da camada de aplicação para utilizar recursos da rede, como transferência de arquivos ou spooling de impressão em rede. Embora transparentes para um funcionário, esses serviços são os programas que fazem interface com a rede e preparam os dados para transferência. Diferentes tipos de dados (texto, gráficos ou vídeo), exigem serviços de rede diferentes para garantir que sejam preparados adequadamente para processamento pelas funções que ocorrem nas camadas inferiores do modelo OSI.

Cada aplicação ou serviço de rede utiliza protocolos que definem os padrões e formatos de dados a serem utilizados. Sem protocolos, a rede de dados não teria uma maneira comum de formatar e direcionar os dados. Para entender a função de vários serviços de rede, é necessário se familiarizar com os protocolos subjacentes que regem sua operação.

### Protocolos Comuns

A maior parte do trabalho dos técnicos, seja em uma rede pequena ou grande, envolverá de alguma forma protocolos de rede. Protocolos de rede dão suporte às aplicações e serviços usados por funcionários em uma rede pequena.

Normalmente, os administradores de rede exigem acesso a dispositivos e servidores de rede. As duas soluções de acesso remoto mais comuns são Telnet e Secure Shell (SSH). O serviço SSH é uma alternativa segura ao Telnet. Quando conectados, os administradores podem acessar o dispositivo de servidor SSH como se estivessem conectados localmente.

SSH é usado para estabelecer uma conexão de acesso remoto segura entre um cliente SSH e outros dispositivos habilitados para SSH:

- **Dispositivo de rede** - O dispositivo de rede (por exemplo, roteador, switch, ponto de acesso, etc.) deve suportar SSH para fornecer serviços de servidor SSH de acesso remoto aos clientes.
- **Servidor** - O servidor (por exemplo, servidor web, servidor de e-mail, etc.) deve suportar serviços de servidor SSH de acesso remoto aos clientes.

Os administradores de rede também devem oferecer suporte a servidores de rede comuns e seus protocolos de rede relacionados necessários, conforme mostrado na figura.
![[Pasted image 20241129180244.png]]

**Servidor web**

- Clientes Web e servidores Web trocam tráfego da Web usando o HTTP (Hypertext Transfer Protocol).
- Hypertext Transfer Protocol Secure (HTTPS) é usado para comunicação web segura.

**Servidor de e-mail**

- Servidores e clientes de e-mail usam o SMTP (Simple Mail Transfer Protocol) para enviar e-mails.
- Os clientes de e-mail usam o POP3 (Protocolo de correio eletrônico) ou o IMAP (Internet Message Access Protocol) para recuperar o e-mail.
- Os destinatários são especificados usando o formato user@xyz[](https://www.netacad.com/content/itn/1.0/).xxx.

**Servidor FTP**

- O serviço File Transfer Protocol (FTP) permite que os arquivos sejam baixados e carregados entre um cliente e um servidor FTP.
- FTP Secure (FTPS) e Secure FTP (SFTP) são usados para proteger a troca de arquivos FTP.

**Servidor DHCP**

O DHCP (Dynamic Host Configuration Protocol) é usado pelos clientes para adquirir uma configuração IP (ou seja, endereço IP, máscara de sub-rede, gateway padrão e muito mais) de um servidor DHCP.

**Servidor DNS**

- Domain Name System (DNS) resolve um nome de domínio para um endereço IP (por exemplo, [cisco.com](http://cisco.com) = 72.163.4.185)
- O DNS fornece o endereço IP de um site (ou seja, nome de domínio) para um host solicitante.

**Observação:** Um servidor pode fornecer vários serviços de rede. Por exemplo, um servidor pode ser um servidor de e-mail, FTP e SSH.

Esses protocolos de rede compreendem as principais ferramentas de um profissional de redes. Cada um desses protocolos de rede define:

- Processos em cada extremidade de uma sessão de comunicação
- Tipos de mensagens
- Sintaxe das mensagens
- Significado dos campos de informação
- Como as mensagens são enviadas e a resposta esperada
- Interação com a próxima camada inferior

Muitas empresas estabeleceram uma política de uso de versões seguras (por exemplo, SSH, SFTP e HTTPS) desses protocolos sempre que possível.

### Aplicações de Voz e Vídeo

O administrador de redes deve assegurar que o equipamento adequado foi instalado na rede e que os dispositivos de rede foram configurados para garantir entrega prioritária.

**Infraestrutura**

- A infra-estrutura de rede deve suportar os aplicativos em tempo real.
- Os dispositivos e cabos existentes devem ser testados e validados.
- Produtos de rede mais recentes podem ser necessários.

**VoIP**

- Os dispositivos de VoIP convertem sinais telefônicos analógicos em pacotes IP digitais.
- Normalmente, o VOIP é mais barato que uma solução de telefonia IP, mas a qualidade das comunicações não atende aos mesmos padrões.
- Voz de rede pequena e vídeo sobre IP podem ser resolvidos usando versões Skype e não empresariais do Cisco WebEx.

**Telefonia IP**

- Um telefone IP realiza conversão de voz para IP com o uso de um servidor dedicado para controle de chamadas e sinalização.
- Muitos fornecedores fornecem soluções de telefonia IP para pequenas empresas, como os produtos Cisco Business Edition 4000 Series.

**Aplicações de Voz e Vídeo**

- A rede deve suportar mecanismos de qualidade de serviço (QoS) para minimizar problemas de latência para aplicativos de streaming em tempo real.
- O Protocolo de Transporte em Tempo Real (RTP) e o Protocolo de Controle de Transporte em Tempo Real (RTCP) são dois protocolos que atendem à essa exigência.

# Escalar para Redes Maiores

### Crescimento das Redes Pequenas

Se sua rede for para uma pequena empresa, presumivelmente, você deseja que essa empresa cresça e sua rede cresça junto com ela. Isso é chamado de dimensionamento de uma rede, e existem algumas práticas recomendadas para fazer isso.

O crescimento é um processo natural para muitas empresas de pequeno porte, e suas redes devem acompanhá-lo. Idealmente, o administrador da rede tem tempo de entrega suficiente para tomar decisões inteligentes sobre o crescimento da rede alinhado com o crescimento da empresa.

Para escalonar uma rede, vários elementos são necessários:

- **Documentação de rede** - Topologia física e lógica
- **Inventário de dispositivos** - Lista de dispositivos que usam ou compreendem a rede
- **Orçamento** - orçamento de TI detalhado, incluindo orçamento de compra de equipamentos do ano fiscal
- **Análise de tráfego** - Protocolos, aplicativos e serviços e seus respectivos requisitos de tráfego devem ser documentados

Esses elementos são usados para subsidiar a tomada de decisão que acompanha o crescimento de uma rede pequena.

### Análise de Protocolos

À medida que a rede cresce, torna-se importante determinar como gerenciar o tráfego de rede. É importante entender o tipo de tráfego que está atravessando a rede, bem como o fluxo de tráfego atual. Existem várias ferramentas de gerenciamento de rede que podem ser usadas para esse fim. No entanto, um analisador de protocolo simples, como o Wireshark, também pode ser usado.

Por exemplo, executar o Wireshark em vários hosts principais pode revelar os tipos de tráfego de rede que flui através da rede. A figura a seguir exibe estatísticas de hierarquia de protocolo Wireshark para um host Windows em uma rede pequena.
![[Pasted image 20241129180711.png]]

A captura de tela revela que o host está usando protocolos IPv6 e IPv4. A saída específica IPv4 também revela que o host usou DNS, SSL, HTTP, ICMP e outros protocolos.

Para determinar os padrões de fluxo de tráfego, é importante fazer o seguinte:

- Capturar o tráfego durante as horas de pico de utilização para obter uma boa ideia dos diferentes tipos de tráfego.
- Realize a captura em diferentes segmentos e dispositivos de rede, pois algum tráfego será local para um segmento específico.

As informações reunidas pelo analisador de protocolos são avaliadas com base na origem e destino do tráfego, bem como no tipo de tráfego que é enviado. Essa análise pode ser usada para tomar uma decisão sobre como gerenciar o tráfego com mais eficiência. Isso pode ser feito com a redução de fluxos de tráfego desnecessários ou alterando totalmente os padrões de fluxo com a mudança de um servidor, por exemplo.

Algumas vezes, a simples mudança de um servidor ou serviço para outro segmento de rede melhora o desempenho da rede e acomoda as necessidades do tráfego crescente. Outras vezes, a otimização do desempenho da rede exige uma maior intervenção e um novo projeto da rede.

### Utilização da Rede Pelos Funcionários

um host Windows fornece ferramentas como o Gerenciador de Tarefas, Visualizador de Eventos e Ferramentas de Uso de Dados.

Essas ferramentas podem ser usadas para consultar o estado atual de informações e processos, como as seguintes:

- Sistema Operacional e a versão desse sistema;
- Utilização da CPU;
- Utilização da memória RAM;
- Utilização das unidades de disco;
- Aplicativos que não são de rede;
- Aplicações de rede.

Documentar snapshots para funcionários em uma pequena rede por um período de tempo é muito útil para identificar requisitos de protocolo em evolução e fluxos de tráfego associados. Uma mudança na utilização dos recursos pode requerer que o administrador de redes ajuste a alocação de recursos da rede proporcionalmente.

A ferramenta de uso de dados do Windows 10 é especialmente útil para determinar quais aplicativos estão usando serviços de rede em um host. A ferramenta de uso de dados é acessada usando **Settings > Network & Internet > Data usage > network interface** (dos últimos 30 dias).

# Verificar a conectividade

### Verificar conectividade com ping

O comando **ping** é a maneira mais eficaz de testar rapidamente a conectividade da Camada 3 entre um endereço IP de origem e de destino. O comando também exibe várias estatísticas de tempo de ida e volta.

Especificamente, o **ping** comando usa as mensagens ICMP echo (ICMP Type 8) e echo reply (ICMP Type 0). O **ping** comando está disponível na maioria dos sistemas operacionais, incluindo Windows, Linux, macOS e Cisco IOS.

Em um host Windows 10, o comando **ping** envia quatro mensagens de eco ICMP consecutivas e espera quatro respostas de eco ICMP consecutivas do destino.

Por exemplo, suponha que PC A pings PC B. Como mostrado na figura, o host PC A Windows envia quatro mensagens de eco ICMP consecutivas para PC B (ou seja, 10.1.1.10).

Observe os caracteres **!!!!!** de saída. O comando **ping** IOS exibe um indicador para cada resposta de eco ICMP recebida. A tabela lista os caracteres de saída mais comuns do comando **ping**.
![[Pasted image 20241129181121.png]]

**Observação:** Outras possíveis respostas de ping incluem Q, M,? , ou &. No entanto, o significado destes estão fora do escopo para este módulo.

### Ping Estendido

Um **ping** padrão usa o endereço IP da interface mais próxima da rede de destino como a origem do **ping**.

O Cisco IOS oferece um modo "estendido" do **ping** comando. Esse modo permite que o usuário crie tipos especiais de pings ajustando parâmetros relacionados à operação de comando.

O ping estendido é inserido no modo EXEC privilegiado, digitando **ping** sem um endereço IP de destino. Em seguida, você receberá vários prompts para personalizar o estendido **ping**.

**Observação:** Pressing **Enter** aceita os valores padrão indicados.

Por exemplo, suponha que você queria testar a conectividade da LAN R1 (ou seja, 192.168.10.0/24) para a LAN 10.1.1.0. Isso pode ser verificado a partir do PC A. No entanto, um estendido **ping** pode ser configurado em R1 para especificar um endereço de origem diferente.

**Observação:** O **ping ipv6** comando é usado para pings estendidos do IPv6.

### Verifique a conectividade com o Traceroute

O **ping** comando é útil para determinar rapidamente se há um problema de conectividade da Camada 3. No entanto, ele não identifica onde o problema está localizado ao longo do caminho.

Traceroute pode ajudar a localizar áreas problemáticas da Camada 3 em uma rede. O comando trace retorna uma lista dos saltos no roteamento de um pacote pela rede. Ele pode ser usado para identificar o ponto ao longo do caminho onde o problema pode ser encontrado.

A sintaxe do comando trace varia entre sistemas operacionais.

A seguir está um exemplo de saída de **tracert** comando em um host Windows 10.
![[Pasted image 20241129181345.png]]
**Observação:** Use **Ctrl-C** to interrupt a **tracert** no Windows.

A única resposta bem-sucedida foi do gateway no R1. Solicitações de rastreamento para o próximo salto expirou conforme indicado pelo asterisco (*), o que significa que o próximo roteador de salto não respondeu. As solicitações de tempo limite indicam que há uma falha na rede fora da LAN ou que esses roteadores foram configurados para não responder às solicitações de eco usadas no rastreamento. Neste exemplo, parece haver um problema entre R1 e R2.

Uma saída de **traceroute** comando do Cisco IOS varia de acordo com o **tracert** comando do Windows. Por exemplo, consulte a seguinte topologia.
![[Pasted image 20241129181422.png]]

A seguir está um exemplo de saída do comando traceroute de R1.
![[Pasted image 20241129181437.png]]
Neste exemplo, o rastreamento validou que ele poderia alcançar com êxito o PC B.

Os tempos limite indicam um problema potencial. Por exemplo, se o host 10.1.1.10 não estivesse disponível, o **traceroute** comando exibiria a seguinte saída.
![[Pasted image 20241129181453.png]]

Use **Ctrl-Shift-6** para interromper um **traceroute** no Cisco IOS.

**Observação:** A implementação do traceroute (tracert) do Windows envia solicitações de eco do ICMP. Cisco IOS e Linux usam UDP com um número de porta inválido. O destino final retornará uma mensagem de porta ICMP inacessível.

### Traceroute estendido

Como o **ping** comando estendido, há também um comando **traceroute** estendido. Ele permite que o administrador ajuste parâmetros relacionados à operação de comando. Isso é útil para localizar o problema ao solucionar loops de roteamento, determinar o roteador do próximo salto exato ou determinar onde os pacotes estão sendo descartados ou negados por um roteador ou firewall.

O comando do Windows, nomeado de **tracert**, permite a entrada de vários parâmetros por meio de opções na linha de comando. No entanto, não é interativo como o comando traceroute estendido, encontrado no IOS. A saída a seguir exibe as opções disponíveis para o **tracert** comando do Windows.
![[Pasted image 20241129181547.png]]

A opção estendida do comando **traceroute** do Cisco IOS permite que o usuário crie um tipo especial de rastreamento ajustando parâmetros relacionados à operação do comando. O traceroute estendido é inserido no modo EXEC privilegiado digitando **traceroute** sem um endereço IP de destino. O IOS orientará você pelas opções de comando apresentando diversos prompts relacionados à configuração de todos os parâmetros diferentes.

**Observação:** Ao pressionar **Enter**, aceita-se os valores padrão indicados.

Conforme ilustrado no exemplo, o endereço IP de origem do **traceroute** comando estendido em R1 pode ser configurado para usar o endereço IP da interface LAN R1 (ou seja, 192.168.10.1).
![[Pasted image 20241129181636.png]]

### Linha de Base da Rede

Uma das ferramentas mais eficazes para o monitoramento e a solução de problemas de desempenho de rede é estabelecer uma linha de base da rede. A criação de uma linha de base de desempenho da rede eficaz é realizada ao longo de um período de tempo. Medir o desempenho em momentos e cargas variados ajudará a criar uma imagem melhor do desempenho geral da rede.

O resultado derivado dos comandos de rede contribui com dados para a linha de base da rede. Um método para iniciar uma linha de base é copiar e colar os resultados de um comando executando **ping**, **tracert** (ou traceroute) ou outros comandos relevantes em um arquivo de texto. Esses arquivos de texto podem ser marcados com a data e salvos em um arquivo para posterior recuperação e comparação.

Entre itens a serem considerados estão mensagens de erro e os tempos de resposta host a host. Se houver um aumento considerável nos tempos de resposta, pode existir um problema de latência a ser resolvido.

Por exemplo, a seguinte **ping** saída foi capturada e colada em um arquivo de texto.

**Agosto 19, 2019 as 08:14:43**
![[Pasted image 20241129181737.png]]

Observe que os tempos de **ping** ida e volta são inferiores a 1 ms.

Um mês depois, o ping é repetido e capturado.

**Setembro 19, 2019 as 10:18:21**

![[Pasted image 20241129181751.png]]Observe desta vez que os tempos de **ping** ida e volta são muito mais longos indicando um problema potencial.

Redes corporativas devem possuir linhas de base extensas, mais extensas do que podemos descrever neste curso. Ferramentas profissionais de software estão disponíveis para armazenamento e manutenção das informações de linha de base. Neste curso, vamos abranger algumas técnicas básicas e discutir o propósito das linhas de base.

As práticas recomendadas da Cisco para processos de linha de base podem ser encontradas pesquisando na Internet “Práticas recomendadas do processo de linha de base”.

# Host e comandos IOS

### Configuração de IP em um host do Windows

Verificar o endereçamento IP em dispositivos host é uma prática comum em rede para verificar e solucionar problemas de conectividade de ponta a ponta. No Windows 10, você pode acessar os detalhes do endereço IP do **Network and Sharing Center**, para visualizar rapidamente as quatro configurações importantes: endereço, máscara, roteador e DNS.

No entanto, os administradores de rede geralmente exibem as informações de endereçamento IP em um host Windows emitindo o comando **ipconfig** na linha de comando de um computador Windows, conforme mostrado na saída de exemplo.
![[Pasted image 20241129181951.png]]

Use o comando **ipconfig /all** para visualizar o endereço MAC, bem como vários detalhes sobre o endereçamento da Camada 3 do dispositivo, conforme mostrado na saída de exemplo.
![[Pasted image 20241129182008.png]]

Se um host estiver configurado como um cliente DHCP, a configuração do endereço IP poderá ser renovada usando os **ipconfig /release** comandos **ipconfig /renew** e, conforme mostrado na saída de exemplo.
![[Pasted image 20241129182028.png]]

O serviço Cliente DNS nos computadores com Windows também otimiza o desempenho da decisão do nome DNS ao armazenar nomes previamente definidos na memória. O **ipconfig /displaydns** comando exibe todas as entradas DNS armazenadas em cache em um sistema de computador Windows, conforme mostrado na saída de exemplo.
![[Pasted image 20241129182054.png]]

### Configuração de IP em um host Linux

A verificação das configurações de IP usando a GUI em uma máquina Linux será diferente dependendo da distribuição Linux (distro) e da interface de desktop.

Na linha de comando, os administradores de rede usam o comando **ifconfig** para exibir o status das interfaces ativas no momento e sua configuração IP, conforme mostrado na saída.
![[Pasted image 20241129182146.png]]
O comando Linux **ip address** é usado para exibir endereços e suas propriedades. Ele também pode ser usado para adicionar ou excluir endereços IP.

**Observação:** A saída exibida pode variar dependendo da distribuição Linux.

### Configuração de IP em um host macOS

Na GUI de um host Mac, abra **Network Preferences > Advanced** para obter as informações de endereçamento IP

No entanto, o Linux **ifconfig** comando também pode ser usado para verificar a configuração IP da interface mostrada na saída.
![[Pasted image 20241129182226.png]]

Outros comandos úteis do macOS para verificar as configurações de IP do host incluem **networksetup -listallnetworkservices** e o **networksetup -getinfo <**_network service_**>,** como mostrado na saída a seguir.
![[Pasted image 20241129182238.png]]

### O Comando arp

O comando **arp** é executado a partir do prompt de comando do Windows, Linux ou Mac. O comando lista todos os dispositivos atualmente no cache ARP do host, que inclui o endereço IPv4, endereço físico e o tipo de endereçamento (estático / dinâmico) para cada dispositivo.

Por exemplo, consulte a topologia na figura.
![[Pasted image 20241129182310.png]]

A saída do comando **arp -a** no host PC-A do Windows é exibida.
![[Pasted image 20241129182322.png]]

O comando **arp -a** exibe o endereço IP conhecido e a ligação de endereço MAC. Observe como o endereço IP 10.0.0.5 não está incluído na lista. Isso ocorre porque o cache do ARP exibe apenas informações de dispositivos que foram acessados recentemente.

Para garantir que o cache do ARP seja preenchido, **ping** um dispositivo para que ele tenha uma entrada na tabela ARP. Por exemplo, se PC-A tiver o ping 10.0.0.5, o cache ARP conterá uma entrada para esse endereço IP.

O cache pode ser limpo usando o comando **netsh interface ip delete arpcache** no caso de o administrador da rede desejar repovoar o cache com informações atualizadas.

**Observação:** Você pode precisar de acesso de administrador no host para poder usar o comando **netsh interface ip delete arpcache**.

### Comandos show Comuns Revisitados

Os comandos da CLI **show** do Cisco IOS exibem informações relevantes sobre a configuração e operação do dispositivo. Os técnicos de rede usam **show** extensivamente comandos para exibir arquivos de configuração, verificar o status das interfaces e processos do dispositivo e verificar o status operacional do dispositivo. O status de quase todos os processos ou funções do roteador pode ser exibido usando um comando **show**.

Comandos **show** comumente usados e quando usá-los são listados na tabela.
![[Pasted image 20241129182447.png]]

### O Comando show cdp neighbors

Há vários outros comandos IOS úteis. O Cisco Discovery Protocol (CDP) é um protocolo proprietário da Cisco que é executado na camada de enlace de dados. Como o CDP opera na camada de enlace de dados, dois ou mais dispositivos de rede da Cisco, como roteadores que suportam diferentes protocolos de camada de rede, podem obter informações de uns sobre os outros e vice-versa, mesmo que a conectividade da camada 3 não tenha sido estabelecida.

Quando um dispositivo Cisco é iniciado, o CDP é iniciado por padrão. O CDP descobre automaticamente dispositivos Cisco adjacentes executando CDP, independentemente de qual protocolo ou suíte de Camada 3 está em execução. O CDP troca informações de hardware e software do dispositivo com seus vizinhos CDP diretamente conectados.

O CDP fornece as seguintes informações sobre cada dispositivo CDP vizinho:

- **Identificadores de dispositivo** - O nome do host configurado de um switch, roteador ou outro dispositivo
- **Lista de endereços** - Até um endereço de camada de rede para cada protocolo suportado
- **Identificador de porta** - O nome da porta local e remota na forma de uma cadeia de caracteres ASCII, como FastEthernet 0/0
- **Lista de capacidades** - Por exemplo, se um dispositivo específico é um switch de Camada 2 ou um switch de Camada 3
- **Plataforma** - A plataforma de hardware do dispositivo - por exemplo, um roteador Cisco 1841 series.

O comando **show cdp neighbors detail** revela o endereço IP de um dispositivo vizinho. O CDP revelará o endereço IP do vizinho, independentemente de você poder ou não executar ping nesse vizinho. Este comando é muito útil quando os dois roteadores Cisco não podem rotear por seu link compartilhado de dados. O comando **show cdp neighbors detail** ajudará a determinar se um dos vizinhos do CDP possui um erro de configuração de IP.

Por mais útil que seja o CDP, também pode ser um risco à segurança, pois pode fornecer informações úteis sobre a infra-estrutura de rede aos agentes de ameaças. Por exemplo, por padrão muitas versões do IOS enviam anúncios CDP por todas as portas habilitadas. Entretanto, as melhores práticas sugerem que o CDP venha ativado apenas em interfaces que se conectam a outros dispositivos de infraestrutura Cisco. Os anúncios CDP devem ser desativados em portas de usuário.

Algumas versões do IOS enviam anúncios CDP por padrão, por isso é importante saber como desativar o CDP. Para desativar o CDP globalmente, use o comando de configuração global **no cdp run**. Para desativar o CDP em uma interface, use o comando interface **no cdp enable**.

### O Comando show ip interface brief

Um dos comandos mais frequentemente usados é o comando **show ip interface brief** . Este comando fornece uma saída mais abreviada que o comando **show ip interface** . Ele exibe um resumo das principais informações para todas as interfaces de rede em um roteador.

Por exemplo, a **show ip interface brief** saída exibe todas as interfaces no roteador, o endereço IP atribuído a cada interface, se houver, e o status operacional da interface.

**Verificar interfaces de switch**

O comando **show ip interface brief** também pode ser usado para verificar o status das interfaces do comutador

# Metodologias de solução de problemas

### Abordagens de solução de problemas básica

Os problemas de rede podem ser simples ou complexos e podem resultar de uma combinação de problemas de hardware, software e conectividade. Os técnicos precisam conseguir analisar o problema e identificar a causa do erro para poderem resolver a falha na rede. Esse processo é chamado de solução de problemas.

Uma metodologia comum e eficiente de solução de problemas é baseada no método científico.

A tabela mostra as seis principais etapas do processo de solução de problemas.
![[Pasted image 20241129182859.png]]

Para avaliar o problema, determine quantos dispositivos na rede estão enfrentando o problema. Se apenas um dispositivo na rede estiver enfrentando o problema, inicie o processo de solução de problemas por ele. Se todos os dispositivos na rede estiverem enfrentando o problema, inicie o processo de solução de problemas pelo dispositivo onde todos os outros dispositivos estiverem conectados. Você deve desenvolver um método lógico e consistente para diagnosticar problemas de rede eliminando um problema de cada vez.

### Resolver ou escalonar?

Em algumas situações, talvez não seja possível resolver o problema imediatamente. Um problema deve ser escalado quando requer uma decisão do gerente, algum conhecimento específico ou nível de acesso à rede indisponível para o técnico de solução de problemas.

Por exemplo, após a solução de problemas, o técnico concluirá que o módulo de roteador deverá ser substituído. Esse problema deve ser escalonado para a aprovação do gerente. O gerente talvez precise escalonar o problema novamente caso a compra no novo módulo exija aprovação do departamento financeiro.

Uma política da empresa deve indicar claramente quando e como um técnico deve escalar um problema.

### O comando de debug

Os processos, protocolos, mecanismos e eventos do SO geram mensagens para comunicar seu status. Essas mensagens podem apresentar informações valiosas ao solucionar problemas ou verificar as operações do sistema. O comando IOS **debug** permite que o administrador exiba essas mensagens em tempo real para análise. É uma ferramenta muito importante para monitorar eventos em um dispositivo Cisco IOS.

Todos **debug** os comandos são inseridos no modo EXEC privilegiado. O Cisco IOS permite restringir a saída para incluir **debug** apenas o recurso ou subfuncionalidade relevante. Isso é importante porque a depuração da saída recebe alta prioridade no processo da CPU e pode travar o sistema. Por esse motivo, use **debug** comandos apenas para solucionar problemas específicos.

Por exemplo, para monitorar o status das mensagens ICMP em um roteador Cisco, use **debug ip icmp**, conforme mostrado no exemplo
![[Pasted image 20241129183047.png]]

Para listar uma breve descrição de todas as opções de comando de depuração, use o comando **debug ?** no modo EXEC privilegiado na linha de comando.

Para desativar um recurso de depuração específico, adicione **no** a palavra-chave na frente do **debug** comando:
```
Router# no debug ip icmp
```

Como alternativa, você pode inserir o **undebug** formato do comando no modo EXEC privilegiado:
```
Router# undebug ip icmp
```

Para desativar todos os comandos de depuração ativos de uma só vez, use o comando: **undebug all**
```
Router# undebug all
```

Seja cauteloso usando algum comando **debug**. Comandos como **debug all** e **debug ip packet** geram uma quantidade substancial de saída e podem usar uma grande parte dos recursos do sistema. O roteador pode ficar tão ocupado exibindo **debug** mensagens que não teria capacidade de processamento suficiente para executar suas funções de rede ou até ouvir comandos para desativar a depuração. Por esse motivo, o uso dessas opções de comando não é recomendável e deve ser evitado.

### O Comando terminal monitor

As conexões para conceder acesso à interface da linha de comandos do IOS podem ser estabelecidas das seguintes maneiras:

- **Localmente** - As conexões locais (ou seja, a conexão do console) requerem acesso físico à porta do console do roteador ou do switch usando um cabo de sobreposição.
- **Remotamente** - As conexões remotas exigem o uso de Telnet ou SSH para estabelecer uma conexão com um dispositivo configurado por IP.

Determinadas mensagens IOS são exibidas automaticamente em uma conexão de console, mas não em uma conexão remota. Por exemplo, a **debug** saída é exibida por padrão em conexões de console. No entanto, a **debug** saída não é exibida automaticamente em conexões remotas. Isso ocorre porque as **debug** mensagens são mensagens de log que são impedidos de serem exibidas em linhas vty.

Na saída a seguir, por exemplo, o usuário estabeleceu uma conexão remota usando Telnet de R2 para R1. O usuário então emitiu ocomando. **debug ip icmp** . No entanto, o comando falhou ao exibir a **debug** saída.
![[Pasted image 20241129183243.png]]

Para exibir mensagens de log em um terminal (console virtual), use o comando **terminal monitor** no modo EXEC privilegiado. Para parar de registrar mensagens em um terminal, use o comando **terminal no monitor** no modo EXEC privilegiado.

Por exemplo, observe como o **terminal monitor** comando foi inserido e o **ping** comando exibe a **debug** saída.
![[Pasted image 20241129183308.png]]

**Observação:** A intenção do comando **debug** é capturar a saída imediata de um retorno de um processo (comando na memória), por um curto período de tempo (ou seja, alguns segundos a um minuto ou mais). Desative sempre **debug** quando não for necessário.

# Cenários de solução de problemas

### Problemas de operação duplex e incompatibilidade

Muitos problemas comuns de rede podem ser identificados e resolvidos com pouco esforço. Agora que você tem as ferramentas e o processo para solucionar problemas de rede, este tópico analisa alguns problemas comuns de rede que você provavelmente encontrará como administrador de rede.

Nas comunicações de dados, _duplex_ refere-se à direção da transmissão de dados entre dois dispositivos.

Existem dois modos de comunicação duplex:

- **Half-duplex** - A comunicação é restrita à troca de dados em uma direção por vez.
- **Full-duplex** - As comunicações podem ser enviadas e recebidas simultaneamente.

As interfaces Ethernet de interconexão devem operar no mesmo modo duplex para obter melhor desempenho de comunicação e evitar ineficiência e latência no link.

O recurso de negociação automática Ethernet facilita a configuração, minimiza problemas e maximiza o desempenho do link entre dois links Ethernet interconectados. Primeiramente, os dispositivos conectados anunciam seus recursos de compatibilidade e, depois, escolhem o modo de desempenho mais alto, compatível com as duas extremidades.

Se um dos dois dispositivos conectados estiverem operando no modo full-duplex e o outro no modo half-duplex, ocorrerá uma incompatibilidade de duplex. Já que a comunicação de dados ocorre por meio de um link físico, no caso de uma incompatibilidade de duplex o desempenho do link físico seria muito ruim.

As incompatibilidades duplex são normalmente causadas por uma interface mal configurada ou, em casos raros, por uma negociação automática com falha. As incompatibilidades de duplex podem ser difíceis de resolver, visto que a comunicação entre os dispositivos continua ocorrendo.

### Problemas de endereçamento IP em dispositivos IOS

Os problemas relacionados ao endereço IP provavelmente impedirão que os dispositivos de rede remota se comuniquem. Como os endereços IP são hierárquicos, qualquer endereço IP atribuído a um dispositivo de rede deve estar em conformidade com esse intervalo de endereços nessa rede. Endereços IP atribuídos erroneamente geram diversos problemas, inclusive conflitos de endereços IP e problemas de roteamento.

Duas causas comuns de atribuição de IPv4 incorreta são os erros de atribuição manual ou problemas relacionados a DHCP.

Os administradores de rede normalmente precisam atribuir de forma manual os endereços IP aos dispositivos, como servidores e roteadores. Se for cometido um erro durante a atribuição, provavelmente ocorrerão problemas de comunicação com o dispositivo.

Em um dispositivo IOS, use os comandos **show ip interface** ou **show ip interface brief** para verificar quais endereços IPv4 estão atribuídos às interfaces de rede. Por exemplo, emitir o comando **show ip interface** **brief** como mostrado validaria o status da interface em R1.
![[Pasted image 20241129183754.png]]

### Problemas de endereçamento IP em dispositivos finais

Em máquinas com Windows, quando o dispositivo não consegue entrar em contato com um servidor DHCP, o Windows atribui automaticamente um endereço que pertence ao intervalo 169.254.0.0/16. Esse recurso é chamado de endereçamento IP privado automático (APIPA) e foi projetado para facilitar a comunicação dentro da rede local. Pense nisso como o Windows dizendo: "Usarei esse endereço no intervalo 169.254.0.0/16 porque não consegui nenhum outro endereço".

Freqüentemente, um computador com um endereço APIPA não poderá comunicar-se com outros dispositivos na rede, porque esses dispositivos provavelmente não pertencerão à rede 169.254.0.0/16. Essa situação indica um problema de atribuição automática de endereço IPv4 que precisa ser corrigido.

**Observação:** Outros sistemas operacionais, como Linux e OS X, não atribuirão um endereço IPv4 à interface de rede se a comunicação com um servidor DHCP falhar.

A maioria dos dispositivos finais são configurados de forma que dependam de um servidor DHCP para a atribuição automática de endereço IPv4. Se o dispositivo não puder comunicar-se com o servidor DHCP, o servidor não conseguirá atribuir um endereço IPv4 para a rede específica e o dispositivo não será capaz de comunicar-se.

Para verificar os endereços IP atribuídos a um computador com Windows, use o comando **ipconfig**, conforme mostrado na saída.
![[Pasted image 20241129183858.png]]

### Problemas de Gateway padrão

O gateway padrão de um dispositivo final é o dispositivo de rede mais próximo que pode encaminhar o tráfego para outras redes. Se um dispositivo tiver um endereço de gateway padrão errado ou inexistente, ele não conseguirá se comunicar com os dispositivos em redes remotas. Como o gateway padrão é o caminho para as redes remotas, seu endereço precisa pertencer à mesma rede que o dispositivo final.

O endereço do gateway padrão pode ser manualmente definido ou obtido de um servidor DHCP. Semelhantes aos problemas de endereçamento IPv4, os problemas de gateway padrão podem estar relacionados à configuração errada (no caso de atribuição manual) ou a problemas de DHCP (se a atribuição manual estiver em uso).

Para solucionar problemas de gateway padrão configurados incorretamente, certifique-se de que o dispositivo tenha o gateway padrão correto configurado. Se o endereço padrão foi manualmente definido, mas está incorreto, basta substituí-lo pelo endereço correto. Se o endereço de gateway padrão foi definido automaticamente, verifique se o dispositivo pode se comunicar com o servidor DHCP. Também é importante verificar se o endereço IPv4 e a máscara de sub-rede adequados foram configurados na interface do roteador e se a interface está ativa.

Para verificar o gateway padrão em computadores baseados no Windows, use o comando **ipconfig**.


Em um roteador, use o comando **show ip route** para listar a tabela de roteamento e verifique se o gateway padrão, conhecido como rota padrão, foi definido. Essa rota é usada quando o endereço de destino do pacote não corresponde a nenhuma outra rota na tabela de roteamento.

Por exemplo, a saída verifica se R1 tem um gateway padrão (ou seja, Gateway de último recurso) configurado apontando para o endereço IP 209.168.200.226.
![[Pasted image 20241129184040.png]]

A primeira linha destacada basicamente afirma que o gateway para qualquer (ou seja, 0.0.0.0) deve ser enviado para o endereço IP 209.165.200.226. O segundo realçado exibe como R1 aprendeu sobre o gateway padrão. Nesse caso, R1 recebeu as informações de outro roteador habilitado para OSPF.

### Como solucionar problemas de DNS

É comum que os usuários relacionem por engano a operação de um link da Internet com a disponibilidade do DNS. As reclamações de usuários como “a rede está inoperante” ou “a internet está inoperante” geralmente são causadas por um servidor DNS inacessível. Embora o roteamento de pacotes e todos os serviços de rede continuem em operação, as falhas de DNS normalmente levam o usuário à conclusão errada. Se o usuário digitar um domínio, como [www.cisco.com](http://www.cisco.com), em um navegador da Web e o servidor DNS estiver inalcançável, o nome não será convertido em um endereço IP e o site não será exibido.

Os endereços de servidor DNS podem ser atribuídos de forma manual ou automática. Os administradores de rede normalmente são responsáveis por atribuir, de forma manual, os endereços de servidor DNS em servidores e outros dispositivos, enquanto o DHCP é usado para atribuir, de forma automática, endereços de servidor DNS a clientes.

Embora seja comum para as empresas gerenciarem seus próprios servidores DNS, qualquer servidor DNS alcançável pode ser usado para resolver nomes. Os usuários de SOHO (Small office and home office, pequeno escritório e escritório doméstico) normalmente contam com o servidor DNS mantido pelo seu ISP para resolução de nomes. Os servidores DNS são atribuídos aos clientes de SOHO via DHCP. Além disso, o Google mantém um servidor DNS público que pode ser usado por qualquer pessoa e é muito útil para testes. O endereço IPv4 do servidor DNS público do Google é 8.8.8.8 e 2001:4860:4860::8888 para seu endereço DNS IPv6.

A Cisco oferece OpenDNS que fornece serviço DNS seguro filtrando phishing e alguns sites de malware. Você pode alterar seu endereço DNS para 208.67.222.222 e 208.67.220.220 nos campos Servidor DNS preferencial e Servidor DNS alternativo. Recursos avançados, como filtragem de conteúdo da Web e segurança, estão disponíveis para famílias e empresas.

Use o **ipconfig /all** como mostrado para verificar qual servidor DNS está sendo usado pelo computador Windows.
![[Pasted image 20241129184226.png]]

O **nslookup** comando é outra ferramenta útil de solução de problemas de DNS para PCs. Com **nslookup** um usuário pode colocar manualmente as consultas DNS e analisar a resposta DNS. O comando **nslookup** mostra a saída de uma consulta para [www.cisco.com](http://www.cisco.com). Observe que você também pode simplesmente digitar um endereço IP e **nslookup** resolverá o nome.