
# Ameaças à Segurança e Vulnerabilidades

### Tipos de Ameaças

Redes de computadores com e sem fio são essenciais para as atividades diárias. Pessoas e empresas dependem de seus computadores e redes. A intrusão por uma pessoa não autorizada pode resultar em custosas interrupções da rede e perda de trabalhos. Ataques em uma rede podem ser devastadores e resultar em perda de tempo e dinheiro devido a danos ou roubo de informações ou ativos importantes.

Os invasores podem obter acesso a uma rede através de vulnerabilidades de software, ataques de hardware ou adivinhando o nome de usuário e a senha de alguém. Os invasores que obtêm acesso modificando o software ou explorando vulnerabilidades são chamados de agentes de ameaças.

Depois que o agente da ameaça obtém acesso à rede, quatro tipos de ameaças podem surgir.

O **roubo de informações** está invadindo o computador para obter informações confidenciais. Informações podem ser usadas ou vendidas para diversas finalidades. Exemplo: roubar informações proprietárias de uma organização, como dados de pesquisa e desenvolvimento.

**Perda e manipulação de dados** está invadindo um computador para destruir ou alterar registros de dados. Um exemplo de perda de dados é um agente de ameaças que envia um vírus que reformata o disco rígido do computador. Um exemplo de manipulação de dados é invadir um sistema de registros para alterar informações, como o preço de um item.

**Identity Roubo de identidade** é uma forma de roubo de informações em que informações pessoais são roubadas com o objetivo de assumir a identidade de alguém. Usando essas informações, um agente de ameaças pode obter documentos legais, solicitar crédito e fazer compras on-line não autorizadas. Identificar roubo é um problema crescente que custa bilhões de dólares por ano.

A **interrupção do serviço** está impedindo que usuários legítimos acessem serviços aos quais têm direito. Exemplos: ataques de negação de serviço (DoS) em servidores, dispositivos de rede ou links de comunicação de rede.

### Tipos de Vulnerabilidades

Vulnerabilidade é o grau de fraqueza em uma rede ou dispositivo. Algum grau de vulnerabilidade é inerente a roteadores, switches, desktops, servidores e até dispositivos de segurança. Normalmente, os dispositivo de rede sob ataque são os endpoints como servidores e computadores desktop.

Existem três principais vulnerabilidades ou fraquezas: política tecnológica, configuração e segurança. Todas essas três fontes de vulnerabilidades podem deixar uma rede ou dispositivo aberto a vários ataques, incluindo ataques de código malicioso e ataques de rede.

![[Pasted image 20241128212730.png]]

![[Pasted image 20241128212742.png]]

![[Pasted image 20241128212752.png]]

### Segurança Física

Uma área vulnerável da rede igualmente importante a considerar é a segurança física dos dispositivos. Se os recursos de rede puderem ser fisicamente comprometidos, um agente de ameaça poderá negar o uso de recursos de rede.

As quatro classes de ameaças físicas são as seguintes:

- **Ameaças de hardware** - Isso inclui danos físicos a servidores, roteadores, switches, instalações de cabeamento e estações de trabalho.
- **Ameaças ambientais** - Isso inclui extremos de temperatura (muito quente ou muito frio) ou extremos de umidade (muito úmido ou muito seco).
- **Ameaças elétricas** - Isso inclui picos de tensão, tensão de alimentação insuficiente (quedas de energia), energia não condicionada (ruído) e perda total de energia.
- **Ameaças à manutenção** - Isso inclui o uso dos principais componentes elétricos (descarga eletrostática), falta de peças de reposição críticas, cabeamento incorreto e rotulagem inadequada.

Um bom plano de segurança física deve ser criado e implementado para resolver esses problemas. 

# Ataques à Rede

### Tipos de Malware

Malware é a abreviação de software malicioso. É um código ou software projetado especificamente para danificar, interromper, roubar ou infligir ações “ruins” ou ilegítimas em dados, hosts ou redes. Vírus, worms e cavalos de Tróia são tipos de malware.

**Vírus**

Um vírus de computador é um tipo de malware que se propaga inserindo uma cópia de si mesmo dentro de outro programa e se tornando parte dele. Ele se dissemina de um computador para outro, deixando infecções por onde passa. Os vírus podem variar em gravidade, causando efeitos levemente irritantes, danificando dados ou software e causando condições de negação de serviço (DoS). Quase todos os vírus estão anexados a um arquivo executável, o que significa que o vírus pode existir em um sistema, mas não estar ativo ou ser capaz de se disseminar até que o usuário execute ou abra o arquivo ou o programa hospedeiro mal-intencionado. Quando o código hospedeiro é executado, o código viral é executado também. Normalmente, o programa host continua funcionando depois que o vírus o infecta. No entanto, alguns vírus sobrescrevem outros programas com cópias deles mesmos, o que destrói todo o programa hospedeiro. Os vírus se espalham quando o software ou documento ao qual estão conectados é transferido de um computador para outro usando a rede, um disco, compartilhamento de arquivos ou anexos de e-mail infectados.

**Worms**

Os worms de computador são similares aos vírus na reprodução de cópias funcionais de si mesmos e podem causar o mesmo tipo de dano. Ao contrário dos vírus, que necessitam que um arquivo infectado se espalhe, worms são softwares independentes e não necessitam de um programa hospedeiro ou ajuda humana para se propagarem. Um worm não precisa estar anexado a um programa para infectar um hospedeiro e entrar em um computador usando uma vulnerabilidade no sistema. Os worms utilizam os recursos do sistema para viajar pela rede sem ajuda.

**Cavalos de Tróia**

Um cavalo de Troia é outro tipo de malware que recebeu o nome do cavalo de madeira usado pelos gregos para invadirem Troia. É uma parte perigosa do software que parece legítima. Os usuários são, em geral, enganados carregando e executando-os em seus sistemas. Depois de ativado, ele pode causar vários ataques ao host, desde irritar o usuário (com janelas pop-up excessivas ou alterar a área de trabalho) até danificá-lo (excluir arquivos, roubar dados ou ativar e espalhar outros malwares, como vírus). Cavalos de Troia também são conhecidos por criarem portas dos fundos (back doors) que permitem o acesso de usuários mal-intencionados ao sistema.

Ao contrário de vírus e worms, os cavalos de Tróia não se reproduzem infectando outros arquivos. Eles se auto-replicam. Os cavalos de Tróia devem se espalhar pela interação do usuário, como abrir um anexo de e-mail ou fazer o download e executar um arquivo da Internet.

### Ataques de Reconhecimento

Além de ataques de códigos mal-intencionados, também é possível que as redes se tornem vítimas de vários ataques à rede. Os ataques à rede podem ser classificados em três categorias principais:

- **Ataques de reconhecimento** - A descoberta e o mapeamento de sistemas, serviços ou vulnerabilidades.
- **Ataques de acesso** - A manipulação não autorizada de dados, acesso ao sistema ou privilégios do usuário.
- **Negação de serviço** - A desativação ou corrupção de redes, sistemas ou serviços.

Para ataques de reconhecimento, os atores externos de ameaças podem usar ferramentas da Internet, como **nslookup** e **whois**, para determinar facilmente o espaço de endereço IP atribuído a uma determinada corporação ou entidade. Após a determinação do espaço de endereço IP, um agente de ameaça pode executar ping nos endereços IP disponíveis ao público para identificar os endereços que estão ativos. Para ajudar a automatizar essa etapa, um agente de ameaça pode usar uma ferramenta de varredura de ping, como **fping** ou **gping**. Isso envia sistematicamente todos os endereços de rede em um determinado intervalo ou sub-rede. Isso se assemelha a telefonar para cada um dos contatos de uma agenda telefônica para ver quem atende.

### Ataques de Acesso

Os ataques de acesso exploram vulnerabilidades conhecidas em serviços de autenticação, serviços de FTP e serviços da Web para obter acesso a contas da Web, bancos de dados confidenciais e outras informações confidenciais. Um ataque de acesso permite que indivíduos obtenham acesso não autorizado a informações que eles não têm o direito de visualizar. Os ataques de acesso podem ser classificados em quatro tipos: ataques de senha, exploração de confiança, redirecionamento de portas e o intermediário (man-in-the-middle).

### Ataques de Negação de Serviços

Os ataques de negação de serviço (DoS) são a forma de ataque mais divulgada e uma das mais difíceis de eliminar. No entanto, devido à facilidade de implementação e danos potencialmente significativos, os ataques de negação de serviço merecem atenção especial dos administradores de segurança.

Os ataques DoS assumem muitas formas. E, por fim, impedem que pessoas autorizadas usem um serviço ao consumir recursos do sistema. Para prevenir ataques (DoS) é importante manter em dia as mais recentes atualizações de segurança para sistemas operacionais e aplicações.

# Mitigações de ataque à rede

### A abordagem de defesa em camadas

Para atenuar os ataques de rede, primeiro você deve proteger dispositivos, incluindo roteadores, switches, servidores e hosts. A maioria das organizações emprega uma abordagem de defesa profunda (também conhecida como abordagem em camadas) à segurança. Isso requer uma combinação de dispositivos e serviços de rede trabalhando em conjunto.

Todos os dispositivos de rede, incluindo o roteador e switches, também são configurados de forma robusta conforme indicado pelos bloqueios de combinação em seus respectivos ícones. Isso indica que eles foram protegidos para impedir que os atores de ameaças obtenham acesso e violem os dispositivos.

Vários dispositivos e serviços de segurança são implementados para proteger os usuários e ativos de uma organização contra ameaças TCP / IP.

- **VPN**- Um roteador é usado para fornecer serviços VPN seguros com sites corporativos e suporte a acesso remoto para usuários remotos usando túneis criptografados seguros.
- **ASA Firewall**- Este dispositivo dedicado fornece serviços de firewall com estado. Ele garante que o tráfego interno possa sair e voltar, mas o tráfego externo não pode iniciar conexões com hosts internos.
- **IPS** - Um sistema de prevenção contra intrusões (IPS) monitora o tráfego de entrada e saída procurando malware, assinaturas de ataques à rede e muito mais. Se reconhecer uma ameaça, ela poderá imediatamente pará-la.
- **ESA/WSA** - O dispositivo de segurança de e-mail (ESA) filtra spam e e-mails suspeitos. O WSA (Web Security Appliance) filtra sites de malware conhecidos e suspeitos na Internet.
- **servidor AAA** - Este servidor contém um banco de dados seguro de quem está autorizado a acessar e gerenciar dispositivos de rede. Os dispositivos de rede autenticam usuários administrativos usando esse banco de dados.

### Manter Backups

Fazer backup de configurações e dados do dispositivo é uma das maneiras mais eficazes de se proteger contra a perda de dados. O backup de dados armazena uma cópia das informações de um computador em uma mídia removível de backup que pode ser guardada em um local seguro. Os dispositivos de infraestrutura devem ter backups de arquivos de configuração e imagens IOS em um servidor de arquivos FTP ou similar. Se o computador ou um hardware de roteador falhar, os dados ou a configuração podem ser restaurados usando a cópia de backup.

Os backups devem ser realizados regularmente, conforme identificado na política de segurança. Os backups de dados são, normalmente, armazenados em outro local, para proteger a mídia de backup, se algo acontecer com a instalação principal. Hosts Windows têm um utilitário de backup e restauração. É importante que os usuários façam backup de seus dados em outra unidade ou em um provedor de armazenamento baseado em nuvem.
![[Pasted image 20241128213650.png]]

### Atualização, atualização e patch

Manter-se atualizado com os desenvolvimentos mais recentes pode levar a uma defesa mais eficaz contra ataques à rede. Quando um novo malware é lançado, as empresas precisam manter as suas atuais versões de software antivírus atualizadas.

O meio mais eficaz de reduzir um ataque de worm é baixar as atualizações de segurança do sistema operacional do fornecedor e corrigir todos os sistemas vulneráveis. A administração de vários sistemas envolve a criação de uma imagem de software padrão (sistema operacional e aplicações com autorização para uso nos sistemas do cliente) que é implantada em sistemas novos ou atualizados. No entanto, os requisitos de segurança são alterados e os sistemas já implantados podem precisar ter patches de segurança atualizados instalados.

Uma solução para o gerenciamento de patches críticos de segurança é garantir que todos os sistemas finais baixem atualizações automaticamente

### Autenticação, autorização e auditoria

Todos os dispositivos de rede devem ser configurados de forma segura para fornecer acesso apenas a indivíduos autorizados. Os serviços de segurança de rede de autenticação, autorização e auditoria (AAA ou "triplo A") fornecem a estrutura principal para configurar o controle de acesso nos dispositivos de rede.

O AAA é uma maneira de controlar quem tem permissão para acessar uma rede (autenticar), quais ações eles executam enquanto acessam a rede (autorizar) e fazer um registro do que foi feito enquanto eles estão lá (auditoria).

O conceito do AAA é semelhante ao uso de um cartão de crédito. O cartão de crédito identifica quem pode utilizá-lo, estipula um limite de uso e mantém o controle dos itens comprados pelo usuário

### Firewalls

Um firewall é uma das ferramentas de segurança disponíveis mais eficazes na proteção dos usuários contra ameaças externas. Um firewall protege computadores e redes impedindo que tráfego indesejável entre em redes internas.

Os firewalls de rede estão localizados entre duas ou mais redes, e controlam o tráfego entre elas, além de ajudar a evitar o acesso não autorizado. Por exemplo, a topologia superior na figura ilustra como o firewall permite que o tráfego de um host de rede interno saia da rede e retorne à rede interna. A topologia inferior ilustra como o tráfego iniciado pela rede externa (ou seja, a Internet) tem acesso negado à rede interna.

Um firewall poderia permitir que usuários externos controlassem o acesso a serviços específicos. Por exemplo, os servidores acessíveis a usuários externos geralmente estão localizados em uma rede especial referida como a zona desmilitarizada (DMZ), conforme mostrado na figura. A DMZ permite que um administrador de rede aplique políticas específicas para hosts conectados a essa rede.

### Tipos de Firewalls

Os produtos de firewall são fornecidos de várias formas. Esses produtos usam técnicas diferentes para determinar o que será permitido ou negado o acesso a uma rede. Ela inclui:

- **Filtragem de pacotes** - Impede ou permite o acesso com base em endereços IP ou MAC;
- **Filtragem de aplicativos** - impede ou permite o acesso por tipos de aplicativos específicos com base nos números de porta;
- **Filtragem de URL** - impede ou permite o acesso a sites com base em URLs ou palavras-chave específicas;
- **Inspeção de pacotes com estado (SPI)** - Os pacotes recebidos devem ser respostas legítimas às solicitações dos hosts internos. Os pacotes não solicitados são bloqueados, a menos que especificamente permitidos. O SPI também pode incluir o recurso de reconhecer e filtrar tipos específicos de ataques, como negação de serviço (DoS).

### Segurança de Endpoints

Um endpoint, ou host, é um sistema de computador individual ou um dispositivo que atua como um cliente da rede. Os endpoints comuns são laptops, desktops, servidores, smartphones e tablets. A segurança de dispositivos de endpoint é uma das tarefas mais desafiadoras de um administrador de rede, porque envolve a natureza humana. Uma empresa deve ter obrigatoriamente as políticas em vigor bem documentadas e os funcionários devem conhecer essas regras. Os funcionários devem ser treinados para usarem corretamente a rede. As políticas em geral incluem o uso de software antivírus e prevenção contra invasões. Soluções de segurança de endpoints mais abrangentes baseiam-se no controle de acesso à rede.

# Segurança de dispositivos

### AutoSecure Cisco

As configurações de segurança são definidas com os valores padrão quando um novo sistema operacional é instalado em um dispositivo. Na maioria dos casos, esse nível de segurança é inadequado. Para roteadores Cisco, o recurso Cisco AutoSecure pode ser usado para ajudar a proteger o sistema, conforme mostrado no exemplo.

```
Router# auto secure
--- AutoSecure Configuration ---
*** AutoSecure configuration enhances the security ofthe router but it will not make router absolutely securefrom all security attacks ***
```

Além disso, existem algumas etapas simples que podem ser executadas e que se aplicam à maioria dos sistemas:

- Nomes de usuário e senhas padrão devem ser trocados imediatamente.
- O acesso aos recursos do sistema deve ser restrito apenas aos indivíduos que estão autorizados a usá-los.
- Todos os serviços e aplicações desnecessários devem ser desativados e desinstalados assim que possível.

Em geral, dispositivos vindos de fábrica ficaram estocados em um depósito por um período e não têm os patches mais atuais instalados. É importante atualizar todos os programas e instalar todos os patches de segurança antes da implementação.

### Senhas

É importante usar senhas fortes para proteger dispositivos de rede. Estas são as diretrizes padrão a serem seguidas:

- Use um comprimento de senha de pelo menos oito caracteres, de preferência 10 ou mais caracteres. Uma senha mais longa é uma senha mais segura.
- Use senhas complexas. Inclua uma combinação de letras maiúsculas e minúsculas, números, símbolos e espaços, se permitido.
- Evite as senhas com base em repetição, palavras comuns de dicionário, sequências de letras ou números, nomes de usuário, nomes de parentes ou de animais de estimação, informações biográficas, como datas de nascimento, números de identificação, nomes de antepassados ou outras informações facilmente identificáveis.
- Deliberadamente, soletre errado uma senha. Por exemplo, Smith = Smyth = 5mYth ou Security = 5ecur1ty.
- Altere as senhas periodicamente. Se uma senha for inconscientemente comprometida, a janela de oportunidade para o agente de ameaças usar a senha é limitada.
- Não anote as senhas e muito menos as deixe em locais óbvios, como em sua mesa ou no monitor.

Nos roteadores Cisco, os espaços à esquerda são ignorados em senhas, mas os espaços após o primeiro caractere não são ignorados. Portanto, um método para criar uma senha forte é utilizar a barra de espaço e criar uma frase feita de muitas palavras. Isso se chama. Uma frase secreta geralmente mais fácil de lembrar do que uma senha simples. Também é maior e mais difícil de ser descoberta.
### Segurança de Senha Adicional

Senhas fortes são úteis apenas se forem secretas. Existem várias etapas que podem ser tomadas para ajudar a garantir que as senhas permaneçam secretas em um roteador e switch Cisco, incluindo estes:

- Criptografando todas as senhas de texto sem formatação;
- Definindo um tamanho mínimo aceitável de senha;
- Deterção de ataques de adivinhação de senha de força bruta;
- Desativando um acesso de modo EXEC privilegiado inativo após um período especificado.

Conforme mostrado na configuração de amostra da figura, o comando de configuração global **service password-encryption** impede que indivíduos não autorizados visualizem senhas em texto sem formatação no arquivo de configuração. Este comando criptografa todas as senhas de texto sem formatação. Observe no exemplo, que a senha “cisco” foi criptografada como “03095A0F034F”.

Para garantir que todas as senhas configuradas tenham no mínimo um comprimento especificado, use o comando **security passwords min-length** _length_ no modo de configuração global. Na figura, qualquer nova senha configurada teria que ter um comprimento mínimo de oito caracteres.

Os atores ameaçadores podem usar software de quebra de senha para realizar um ataque de força bruta em um dispositivo de rede. Este ataque tenta continuamente adivinhar as senhas válidas até que uma funcione. Use o comando de configuração global **login block-for _#_ attempts _#_ within _#_** para impedir esse tipo de ataque. Na figura, por exemplo, o comando **login block-for 120 attempts 3 within 60**, bloqueará as tentativas de login por 120 segundos se houver três tentativas de login com falha dentro de 60 segundos.

Os administradores de rede podem se distrair e acidentalmente deixar uma sessão de modo EXEC privilegiada aberta em um terminal. Isso pode permitir que um ator de ameaça interno tenha acesso para alterar ou apagar a configuração do dispositivo.

Por padrão, os roteadores Cisco farão logout de uma sessão EXEC após 10 minutos de inatividade. No entanto, você pode reduzir essa tempo, usando o comando **exec-timeout** [minutos] [segundos] na configuração das linhas de acesso. Esse comando pode ser aplicado on-line console, auxiliares e linhas vty. Na figura, estamos dizendo ao dispositivo Cisco para desconectar automaticamente um usuário inativo em uma linha vty após o usuário ficar ocioso por 5 minutos e 30 segundos.

```
R1(config)# service password-encryption 
R1(config)# security passwords min-length 8 
R1(config)# login block-for 120 attempts 3 within 60
R1(config)# line vty 0 4 
R1(config-line)# password cisco123 
R1(config-line)# exec-timeout 5 30 
R1(config-line)# transport input ssh 
R1(config-line)# end 
R1# 
R1# show running-config | section line vty
line vty 0 4 
password 7 094F471A1A0A 
exec-timeout 5 30 
login 
transport input ssh
R1#
```

### Ativação do SSH

O Telnet simplifica o acesso remoto ao dispositivo, mas não é seguro. Os dados contidos em um pacote Telnet são transmitidos sem criptografia. Por esse motivo, é altamente recomendável ativar o Secure Shell (SSH) em dispositivos para acesso remoto seguro.

É possível configurar um dispositivo Cisco para suportar SSH usando as seis etapas a seguir:

**Etapa 1.** **Configurar um nome de host de dispositivo exclusivo**. Um dispositivo deve ter um nome de host exclusivo diferente do padrão.

**Etapa 2. Configure o nome do domínio IP**. Configure o nome de domínio IP da rede usando o comando modo de configuração global **ip-domain name**.

**Etapa 3. Gere uma chave para criptografar o tráfego SSH.**. O SSH criptografa o tráfego entre a origem e o destino. No entanto, para fazer isso, uma chave de autenticação exclusiva deve ser gerada usando o comando de configuração global **crypto key generate rsa general-keys modulus** _bits_. O módulo _bits_ determina o tamanho da chave e pode ser configurado de 360 bits a 2048 bits. Quanto maior o valor de bit, mais segura a chave. No entanto, valores de bits maiores também levam mais tempo para criptografar e descriptografar informações. O tamanho mínimo recomendado do módulo é 1024 bits.

**Etapa 4.** **Verifique ou crie uma entrada de banco de dados local.**. Crie uma entrada de nome de usuário do banco de dados local usando o **username** comando de configuração global. No exemplo, o parâmetro **secret** é usado para que a senha seja criptografada usando MD5.

**Etapa 5.** **Autenticar no banco de dados local.**. Use o comando de configuração de **login local** linha para autenticar a linha vty no banco de dados local.

**Etapa 6. Habilite as sessões SSH de entrada vty.** Por padrão, nenhuma sessão de entrada é permitida em linhas vty. Você pode especificar vários protocolos de entrada, incluindo Telnet e SSH usando o comando **transport input [ssh | telnet]**.

Como mostrado no exemplo, o roteador R1 está configurado no domínio [span.com](http://span.com). Essas informações são usadas juntamente com o valor de bit especificado no **crypto key generate rsa general-keys modulus** comando para criar uma chave de criptografia.

Em seguida, uma entrada de banco de dados local para um usuário chamado Bob é criada. Finalmente, as linhas vty são configuradas para autenticar no banco de dados local e para aceitar somente sessões SSH de entrada.
![[Pasted image 20241128214612.png]]

### Desativar serviços não utilizados

Os roteadores e switches Cisco começam com uma lista de serviços ativos que podem ou não ser necessários em sua rede. Desative todos os serviços não utilizados para preservar os recursos do sistema, como ciclos de CPU e RAM, e impedir que os atores ameaçadores explorem esses serviços. O tipo de serviços que estão ativados por padrão varia dependendo da versão do IOS. Por exemplo, o IOS-XE normalmente terá apenas portas HTTPS e DHCP abertas. Você pode verificar isso com o comando **show ip ports all**, como mostrado no exemplo.
![[Pasted image 20241128214644.png]]
As versões do IOS anteriores ao IOS-XE usam o **show control-plane host open-ports** comando. Mencionamos esse comando porque você pode vê-lo em dispositivos mais antigos. A saída é semelhante. No entanto, observe que este roteador mais antigo tem um servidor HTTP inseguro e Telnet em execução. Ambos os serviços devem ser desativados. Como mostrado no exemplo, desative HTTP com o comando de configuração **no ip http server** global. Desative o Telnet especificando apenas SSH no comando de configuração de linha, **transport input ssh**.
![[Pasted image 20241128214702.png]]

