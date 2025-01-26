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

Для проверки количества интерфейсов **FastEthernet**, **GigabitEthernet**, а также диапазон **VTY** согласно заданию, используем команду: 

>Switch#show running-config

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/%D1%80%D0%B0%D0%BD%D0%BD%D0%B8%D0%BD%D0%B3%20%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3.jpg)

!
