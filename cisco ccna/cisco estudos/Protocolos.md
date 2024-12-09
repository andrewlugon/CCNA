![[Pasted image 20241029192436.png]]

- **Internet Protocol Suite ou TCP/IP** - Este é o conjunto de protocolos mais comum e relevante usado hoje. O conjunto de protocolos TCP/IP é um conjunto de protocolos padrão aberto mantido pela Internet Engineering Task Force (IETF).
- **Protocolos de Interconexão de Sistemas Abertos (OSI)** - Esta é uma família de protocolos desenvolvidos conjuntamente em 1977 pela Organização Internacional de Normalização (ISO) e pela União Internacional de Telecomunicações (UIT). O protocolo OSI também incluiu um modelo de sete camadas chamado modelo de referência OSI. O modelo de referência OSI categoriza as funções de seus protocolos. Hoje OSI é conhecido principalmente por seu modelo em camadas. Os protocolos OSI foram amplamente substituídos por TCP/IP.
- **AppleTalk** - Um conjunto de protocolos proprietário de curta duração lançado pela Apple Inc. em 1985 para dispositivos Apple. Em 1995, a Apple adotou o TCP/IP para substituir o AppleTalk.
- **Novell NetWare** - Um conjunto de protocolos proprietário de curta duração e sistema operacional de rede desenvolvido pela Novell Inc. em 1983 usando o protocolo de rede IPX. Em 1995, a Novell adotou o TCP/IP para substituir o IPX.


Existem dois modelos em camadas que são usados para descrever operações de rede:

- Modelo de referência OSI (Open System Interconnection)
- Modelo de referência TCP / IP

O formato que uma parte de dados assume em qualquer camada é chamado de unidade de dados de protocolo (PDU).
- Dados - O termo genérico para a PDU usada na camada de aplicação;
- Segmento - PDU da camada de transporte;
- Pacote - PDU da camada de rede;
- Quadro - PDU da camada de enlace de dados
- Bits - PDU da camada física usada ao transmitir dados fisicamente pela mídia.


Endereços de origem e destino da camada de rede - Responsável por entregar o pacote IP da origem original ao destino final, que pode estar na mesma rede ou em uma rede remota.

Endereços de origem e destino da camada de enlace de dados - Responsável por fornecer o quadro de enlace de dados de uma placa de interface de rede (NIC) para outra NIC na mesma rede.
![[Pasted image 20241029195605.png]]


O endereço físico da Camada 2 do link de dados tem uma função diferente. A finalidade do endereço de enlace de dados é fornecer o quadro de enlace de dados de uma interface de rede para outra na mesma rede.

Antes que um pacote IP possa ser enviado por uma rede com ou sem fio, ele deve ser encapsulado em um quadro de enlace de dados, para que possa ser transmitido pela mídia física.