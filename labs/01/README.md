# Топология     
## Задание:

 1. Проверка конфигурации коммутатора по умолчанию
 2. Создание сети и настройка основных параметров устройства
    *	Настроить базовые параметры коммутатора.
    *	Настроить IP-адрес для ПК.
 3. Проверка сетевых подключений
    *   Отобразить конфигурацию устройства.
    *   Протестировать сквозное соединение, отправив эхо-запрос.
    *   Протестировать возможности удаленного управления с помощью Telnet.
      
## Решение:

С помощью **Cisco Packet Tracer** производим подключение согласно топологии : 

  * кабелем **Console** соединим разъём **Console** коммутатора и **RS232** у ПК ;
  * кабелем **Copper Straight-Through** соединим разъём **FastEthernet0/6** коммутатора и **FastEthernet0** - у ПК.


![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/%D1%82%D0%BE%D0%BF%D0%BE%D0%BB%D0%BE%D0%B3%D0%B8%D1%8F%20cpt.jpg)

Переходим в ПК, заходим в меню **Terminal**, выбираем подменю **Dekstop** и попадаем в меню командной строки.

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/%D1%82%D0%B5%D1%80%D0%BC%D0%B8%D0%BD%D0%B0%D0%BB%20.jpg).

Жмём **Enter/Return** и переходим из пользовательского режима EXEC в привелегированный c помощью команды **enable**:

>Switch>enable 

>Switch#

Для проверки конфигураций на коммутаторе введём команду **show startup-config**:

>Switch#show startup-config

>startup-config is not present

Конфигурация **НЕ ЗАПИСАНА**.

Для проверки количества интерфейсов **FastEthernet**, **GigabitEthernet**, а также диапазон **VTY** согласно заданию, используем команду: 

>Switch#show running-config

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/%D1%80%D0%B0%D0%BD%D0%BD%D0%B8%D0%BD%D0%B3%20%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3.jpg)

По результатам проверки - 24 **FastEthernet**, 2 **GigabitEthernet** и 2 диапазона **VTY** на 16 возможных вариантов удалённого подключения.

Для изучения характеристик SVI для VLAN 1 выходим из привелегированного режима и используем команду **show interfaces vlan 1** , перед нами появляется его конфигурация : 

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/interface%20vlan%201.jpg)

IP-адрес **не назначен**, мак-адрес - напротив, поскольку, несмотря на то, что интерфейс виртуальный, необходимо взаимодействие на физическом уровне. Сам интерфейс **выключен** - привести его в действие возможно, вернувшись в привелегированный режим и используя команду **no shutdown** :

>**Switch#configure t**

>**Switch(config)#interface vlan 1**

>**Switch(config-if)#no shutdown**

Для просмотра IP свойств интерфейса SVI сети VLAN 1,выйдем из привелегированного режима и воспользуемся командой **show ip interface vlan1**:

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/ip%20interface%20vlan%201.jpg)

**ВНЕ ЗАВИСИМОСТИ** от состояния интерфейса (*up/down*) будет присутствовать надпись следующего содержания. Чтобы это исправить, необходимо будет произвести настройку, что мы обязательно проделаем далее.

Рассмотрим интерфейс коммутатора, к которому, согласно заданной топологии, подключён ПК. Используем команду **show interfaces fastEthernet 0/6** :

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/f06.jpg)

Интерфейс **активен**, для включения/отключения его используются аналогичные команды через привелегированный режим **shutdown/no shutdown**, озвученные ранее. В интерфейсе заданы параметры **100 Мбит/c в полном дуплексе**, то есть полноценной заданной скоростью в обе стороны *(входящая/исходящая)*.

Проверим **содержимое флеш-памяти** командой **show flash:**, где нам предстаёт единственная запись :

>1  -rw-     4670455          <no date>  2960-lanbasek9-mz.150-2.SE4.bin

Ранее сохранённые конфигурации отсутствуют, здесь лишь файл прошивки в формате *bin*.

Далее выставляем параметры согласно заданию: 

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/%D1%81%D0%B2%D0%B8%D1%82%D1%87%20%D0%B1%D0%B0%D0%B7%D0%B0.jpg)

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/%D0%B4%D0%BE%D0%BF%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B8%20%D1%82%D0%B5%D1%80%D0%BC%D0%B8%D0%BD%D0%B0%D0%BB%D0%B0.jpg)

Команда **login** задаёт запрос на требование пароля.

Настраиваем **ПК** согласно заданию:

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/%D0%B8%D0%BC%D1%8F%20%D0%BF%D0%BA.jpg)

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/%D0%BF%D0%B0%D1%80%D0%B0%D0%BC%D0%B5%D1%82%D1%80%D1%8B%20%D0%BF%D0%BA.jpg)

Проверяем конфиг и VLAN 1 :

![![S1#show run
Building configuration...

Current configuration : 1349 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname S1
!
enable secret 5 $1$mERr$9cTjUIEqNGurQiFU.ZeCi1
!
!
!
no ip domain-lookup
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 ip address 192.168.1.2 255.255.255.0
!
ip default-gateway 192.168.1.1
!
banner motd ^CUnauthorized access is strictly prohibited. ^C
!
!
!
line con 0
 password 7 0822455D0A16
 logging synchronous
 login
!
line vty 0 4
 password 7 0822404F1A0A
 login
 transport input telnet
line vty 5 15
 login
!
!
!
!
end


S1#sh
S1#show int
S1#show interfaces vlan 1
Vlan1 is up, line protocol is up
  Hardware is CPU Interface, address is 0001.c9ee.3e7d (bia 0001.c9ee.3e7d)
  Internet address is 192.168.1.2/24
  MTU 1500 bytes, BW 100000 Kbit, DLY 1000000 usec,
     reliability 255/255, txload 1/255, rxload 1/255
  Encapsulation ARPA, loopback not set
  ARP type: ARPA, ARP Timeout 04:00:00
  Last input 21:40:21, output never, output hang never
  Last clearing of "show interface" counters never
  Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0
  Queueing strategy: fifo
  Output queue: 0/40 (size/max)
  5 minute input rate 0 bits/sec, 0 packets/sec
  5 minute output rate 0 bits/sec, 0 packets/sec
     1682 packets input, 530955 bytes, 0 no buffer
     Received 0 broadcasts (0 IP multicast)
     0 runts, 0 giants, 0 throttles
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored
     563859 packets output, 0 bytes, 0 underruns
     0 output errors, 23 interface resets
     0 output buffer failures, 0 output buffers swapped out](image-1.png)](image.png)

     