# PXE
Задание:
Следуя шагам из документа установить и настроить загрузку по сети для дистрибутива CentOS8
https://docs.centos.org/en-US/8-docs/advanced-install/assembly_preparing-for-a-network-install либо репозиторием https://github.com/nixuser/virtlab/tree/main/centos_pxe
настроить установку из репозитория HTTP
настроить автоматическую установку для созданного kickstart файла (*)

Что было сделано.
1. Внесены правки в вагрант файл, в частности увеличено ОЗУ до 4 гб
2. внесены правки в скрипт <code> yum -y install python3-twisted </code>
3. основные правки были сделаны тут:
```ruby
append initrd=images/CentOS-8.2/initrd.img ip=enp0s3:dhcp inst.repo=http://10.0.0.20:8080
LABEL linux-auto
  menu label ^Auto install system
  kernel images/CentOS-8.2/vmlinuz
  append initrd=images/CentOS-8.2/initrd.img ip=enp0s3:dhcp inst.ks=http://10.0.0.20:8080/ks.cfg inst.repo=http://10.0.0.20:8080
  ```
  
