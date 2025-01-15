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


![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/%D1%82%D0%BE%D0%BF%D0%BE%D0%BB%D0%BE%D0%B3%D0%B8%D1%8F.jpg)

Version ID                      : V02
CLEI Code Number                : COM3L00BRA
Hardware Board Revision Number  : 0x01

Switch Ports Model              SW Version            SW Image
------ ----- -----              ----------            ----------
*    1 26    WS-C2960-24TT-L    15.0(2)SE4            C2960-LANBASEK9-M

Cisco IOS Software, C2960 Software (C2960-LANBASEK9-M), Version 15.0(2)SE4, RELEASE SOFTWARE (fc1)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 1986-2013 by Cisco Systems, Inc.
Compiled Wed 26-Jun-13 02:49 by mnguyen



Press RETURN to get started!


%LINK-5-CHANGED: Interface FastEthernet0/6, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/6, changed state to up

%LINK-3-UPDOWN: Interface FastEthernet0/6, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/6, changed state to down

%LINK-5-CHANGED: Interface FastEthernet0/6, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/6, changed state to up__
