# tms-disk-hw
HW disk for tms
0. Добавлены диски по 10ГБ в VM
  - разбиты на разделы с помощью команды `fdisk /dev/sda` и `fdisk /dev/sdb`

<img width="677" height="317" alt="image" src="https://github.com/user-attachments/assets/844440cf-9cd7-402f-87cf-ff5b244bf5b1" />


1. Создана VG `tms-vg` с помощью команды `sudo vgcreate tms-vg /dev/sda1 /dev/sdb2`
  - созданы LV с помощью команды
  - `sudo lvcreate -n data -L +5G tms-vg` - data
  - `sudo lvcreate -n bkp -l +100%FREE tms-vg` - bkp
     
<img width="556" height="435" alt="image" src="https://github.com/user-attachments/assets/1e90bc23-954b-4fb0-b0d5-28908f5a2b20" />

2. Изменена файловая система - `mkfs.xfs /dev/tms-vg/data`, `mkfs.ext4 /dev/tms-vg/bkp`
3. 
