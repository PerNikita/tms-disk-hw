# tms-disk-hw
HW disk for tms
<br><br>
0. Добавлены диски по 10ГБ в VM
  - разбиты на разделы с помощью команды `fdisk /dev/sda` и `fdisk /dev/sdb`
<br>
<img width="677" height="317" alt="image" src="https://github.com/user-attachments/assets/844440cf-9cd7-402f-87cf-ff5b244bf5b1" />
<br><br><br>

1. Создана VG `tms-vg` с помощью команды `sudo vgcreate tms-vg /dev/sda1 /dev/sdb2`
  - созданы LV с помощью команды
  - `sudo lvcreate -n data -L +5G tms-vg` - data
  - `sudo lvcreate -n bkp -l +100%FREE tms-vg` - bkp
    
<br>

<img width="556" height="435" alt="image" src="https://github.com/user-attachments/assets/1e90bc23-954b-4fb0-b0d5-28908f5a2b20" />
<br>
<br>
<br>

2. Изменена файловая система - `mkfs.xfs /dev/tms-vg/data`, `mkfs.ext4 /dev/tms-vg/bkp`
<br>
<img width="825" height="507" alt="image" src="https://github.com/user-attachments/assets/81dfffba-90e6-45a7-86bd-c755f44ca876" />
<br>
<br>
<br>

3. Созданы папки `data` и `backaups`
  - выполнено монтирование - `sudo mount`
  - вывод `df -Th`

<br>

<img width="824" height="439" alt="image" src="https://github.com/user-attachments/assets/440f4cc0-d034-4624-9fc4-fa46bfb9e4e2" />

<br>
<br>
<br>

4. Добавлен `/dev/sda2` в LV `tms-vg`
<br>
<img width="775" height="232" alt="image" src="https://github.com/user-attachments/assets/794c86f7-aa75-4c3f-b98b-9773645bc05d" />
<br>
<br>
<br>

5. Расширен LV `data`
<br>
<img width="861" height="278" alt="image" src="https://github.com/user-attachments/assets/739ec3e9-d9ee-4345-af67-eb780605de83" />
<br>
<br>
<br>

6. Создана VG `reserved` с помощью команды `sudo vgcreate reserved /dev/sdb1`
<br>
<img width="829" height="385" alt="image" src="https://github.com/user-attachments/assets/40d9bdc8-d0b6-4c60-8f9c-b7683c3f272c" />
<br>
<br>
<br>

7. Создана LV `other`
<br>
<img width="823" height="278" alt="image" src="https://github.com/user-attachments/assets/1497804d-2b80-4f7a-88a0-52d336c9ffed" />
<br>
<br>
<br>

8. Создана папка и выполнено монтирование в `/opt/tests`
<br>
<img width="823" height="641" alt="image" src="https://github.com/user-attachments/assets/f5c6a85f-f2fe-4fc7-bf7b-1d963ce1ebb0" />
<br>
<br>
<br>

9. Созданы файлы `file1.txt`, `file2.txt`
   - выполнена проверка файлов `ls`
   - выполнено отмонтирование `/opt/tests`
   - создан файл `bigdata.txt`
   - выполнено монтирование при существующем файле `bigdata.txt`
   - файл `bigdata.txt` изчез, после монтировния файлы `file1.txt`, `file2.txt` появились снова
   - данные после отмонтирования не теряются
   - при отмонтировнии повторно `/opt/tests`, файл `bigdata.txt` появился, монтирование не удаляет существкющие файлы
   <br>
<img width="785" height="592" alt="image" src="https://github.com/user-attachments/assets/4b30cf9d-1bfd-4aa4-a382-a7631225f9de" />



