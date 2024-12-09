
Configurar o nome do dispositivo.

```
Router(config)# hostname hostname
```

Proteger o modo EXEC privilegiado.

```
Router(config)# enable secret password
```

Proteger o modo EXEC usuário.

```
  Router(config)# line console 0    
  Router(config-line)# password password    
  Router(config-line)# login
```

Proteger o acesso remoto Telnet/SSH.

```
  Router(config-line)# line vty 0 4    
  Router(config-line)# password   password    
  Router(config-line)# login    
  Router(config-line)# transport input {    ssh   | telnet}
```

Proteger todas as senhas do arquivo de configuração.

```
  Router(config-line)# exit    
  Router(config)# service password-encryption
```

Apresentar a notificação legal.

```
Router(config)# banner motd delimiter message delimiter
```

Salvar a configuração.

```
  Router(config)# end    
  Router# copy running-config startup-config
```

Para configurar o nome do dispositivo para R1, use os seguintes comandos.

```
Router> enable Router# configure terminal
Enter configuration commands, one per line.End with CNTL/Z.
Router(config)# hostname R1 
R1(config)#
```

Todo o acesso ao roteador deve ser protegido. O modo EXEC privilegiado fornece ao usuário acesso completo ao dispositivo e sua configuração. Portanto, é o modo mais importante para proteger.

Os comandos a seguir protegem o modo EXEC privilegiado e o modo EXEC do usuário, habilitam o acesso remoto Telnet e SSH e criptografam todas as senhas de texto simples (ou seja, EXEC do usuário e linha VTY).

```
R1(config)# enable secret class 
R1(config)#
R1(config)# line console 0 
R1(config-line)# password cisco 
R1(config-line)# Login 
R1(config-line)# exit 
R1(config)#
R1(config)# line vty 0 4 
R1(config-line)# password cisco 
R1(config-line)# Login 
R1(config-line)# transport input ssh telnet 
R1(config-line)# exit 
R1(config)#
R1(config)# service password-encryption 
R1(config)#
```

A notificação legal avisa os usuários de que o dispositivo só deve ser acessado por usuários permitidos. A notificação legal é configurada da seguinte forma.

```
R1(config)# banner motd #
Digite a mensagem de texto. Termine com uma nova linha e o #*********************************************** AVISO: O acesso não autorizado é proibido!***********************************************#
R1(config)#
```

Se os comandos anteriores foram configurados e o roteador perdeu energia acidentalmente, todos os comandos configurados seriam perdidos. Por esse motivo, é importante salvar a configuração quando as alterações são implementadas. O comando a seguir salva a configuração na NVRAM.

```
R1# copy running-config startup-config
Destination filename [startup-config]? 
Building configuration...[OK]
R1#
```

### Configurar Interfaces do Roteador

Neste ponto, seus roteadores têm suas configurações básicas. O próximo passo é configurar suas interfaces. Isso ocorre porque os roteadores não podem ser acessados por dispositivos finais até que as interfaces estejam configuradas. Há muitos tipos diferentes de interfaces disponíveis em roteadores Cisco. Por exemplo, o roteador Cisco ISR 4321 está equipado com duas interfaces Gigabit Ethernet:

- **GigabitEthernet 0/0/0 (G0/0/0)**
- **GigabitEthernet 0/0/1 (G0/0/1)**

A tarefa para configurar uma interface de roteador é muito semelhante a um SVI de gerenciamento em um switch. Especificamente, ele inclui a emissão dos seguintes comandos:

```
  Router(config)# interface type-and-number    
  Router(config-if)# description description-text    
  Router(config-if)# ip address  ipv4-address subnet-mask    
  Router(config-if)# ipv6 address  ipv6-address/prefix-length    
  Router(config-if)# no shutdown
```

**Observação:** Quando uma interface de roteador está habilitada, mensagens de informações devem ser exibidas confirmando o link habilitado.

Embora o comando **description** não seja necessário para habilitar uma interface, é recomendável usá-lo. Isso pode ser útil na solução de problemas em redes de produção, fornecendo informações sobre o tipo de rede conectada. Por exemplo, se a interface se conectar a um provedor de serviços de Internet ou provedor de serviços, o comando **description** seria útil para inserir informações de conexão e contato de terceiros.

**Observação:** O texto da descrição está limitado a 240 caracteres.

O uso do comando **no shutdown** ativa a interface e é semelhante a ligar a interface. A interface também deve ser conectada a outro dispositivo, como switch ou roteador, para que a camada física esteja ativa.

**Observação:** Em conexões entre roteadores onde não há switch Ethernet, ambas as interfaces de interconexão devem ser configuradas e habilitadas.

Para configurar as interfaces em R1, use os seguintes comandos.

```
R1> enableR1# configure terminal
Enter configuration commands, one per line.
End with CNTL/Z.
R1(config)# interface gigabitEthernet 0/0/0
R1(config-if)# description Link to LAN
R1(config-if)# ip address 192.168.10.1 255.255.255.0
R1(config-if)# ipv6 address 2001:db8:acad:10::1/64
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config)#
*Aug  1 01:43:53.435: %LINK-3-UPDOWN: Interface GigabitEthernet0/0/0, changed state to down
*Aug  1 01:43:56.447: %LINK-3-UPDOWN: Interface GigabitEthernet0/0/0, changed state to up
*Aug  1 01:43:57.447: %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0, changed state to up
R1(config)#R1(config)#
R1(config)# interface gigabitEthernet 0/0/1
R1(config-if)# description Link to R2
R1(config-if)# ip address 209.165.200.225 255.255.255.252
R1(config-if)# ipv6 address 2001:db8:feed:224::1/64R1(config-if)# no shutdown
R1(config-if)# exit
R1(config)#
*Aug  1 01:46:29.170: %LINK-3-UPDOWN: Interface GigabitEthernet0/0/1, changed state to down
*Aug  1 01:46:32.171: %LINK-3-UPDOWN: Interface GigabitEthernet0/0/1, changed state to up
*Aug  1 01:46:33.171: %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up
R1(config)#
```

**Observação:** Observe as mensagens informativas nos informando que G0/0/0 e G0/0/1 estão ativados.

Há vários comandos que podem ser usados para verificar a configuração de uma interface. O mais útil deles é o comandos **show ip interface brief** e **show ipv6 interface brief**

![[Pasted image 20241118194709.png]]

### Gateway padrão em um host

Para que um dispositivo final se comunique pela rede, ele deve ser configurado com as informações de endereço IP, incluindo o endereço de gateway padrão. O gateway padrão só é usado quando o host deseja enviar um pacote a um dispositivo em outra rede. O endereço do gateway padrão geralmente é o endereço da interface do roteador associado à rede local do host. O endereço IP do dispositivo host e o endereço da interface do roteador devem estar na mesma rede.

### Gateway padrão em um switch

Um comutador que interconecta computadores clientes geralmente é um dispositivo da Camada 2. Como tal, um switch de Camada 2 não precisa de um endereço IP para funcionar corretamente. No entanto, uma configuração IP pode ser configurada em um switch para dar acesso remoto a um administrador ao switch.

Para se conectar e gerenciar um switch em uma rede IP local, ele deve ter uma interface virtual de switch (SVI) configurada. O SVI é configurado com um endereço IPv4 e uma máscara de sub-rede na LAN local. O switch também deve ter um endereço de gateway padrão configurado para gerenciar remotamente o switch de outra rede.

O endereço de gateway padrão geralmente é configurado em todos os dispositivos que se comunicam além da rede local.

Para configurar um gateway padrão IPv4 em um switch, use o comando de configuração global **ip default-gateway** _ip-address_. O _ip-address_ que está configurado é o endereço IPv4 da interface do roteador local conectada ao switch.