# block-level copy util (blcp) for Linux
Программа предназначена для поблочного копирования (синхронизации) файлов.  
В процессе работы считывается блок исходного файла, вычисляется его контрольная сумма, затем контрольная сумма сверяется с таким же блоком файла назначения.   Если контрольные суммы блоков совпадают, то данные не передаются и не записываются, считывается следующий блок файла.  
Шифрование не применяется т.к. оно повышет нагрузку на CPU и не предполагается использование программы за переделами локальной сети.  

Программа подходит для синхронизации файлов образов виртуальных машин в кластере Proxmox VE.  
Виртуальные машины в кластере могут перемещаться между узлами, поэтому серверная часть должна работать на всех узлах.  

Если в процессе синхронизации произойдет аварийная ситуация, то конечный файл останется неповрежденный.

Предназначение файлов:  
blcpf - для локальной синхронизации файлов, без использования сети  
blcpc - клиентская часть сетевой версии  
blcps - серверная часть сетевой версии  

В сетевой версии размер блока по умолчанию равен 512K.  
