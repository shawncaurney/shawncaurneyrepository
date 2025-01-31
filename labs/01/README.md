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

Далее выставляем базовые параметры согласно заданию: 

![Image alt](https://github.com/shawncaurney/shawncaurneyrepository/blob/main/labs/issue/%D1%81%D0%B2%D0%B8%D1%82%D1%87%20%D0%B1%D0%B0%D0%B7%D0%B0.jpg)

!