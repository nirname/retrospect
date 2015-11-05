# Mount

Допустим, образ лежит в домашней директории и называется file.iso.

Создаём место, куда мы будем монтировать (обычно где-нибудь в /media или /mnt)

    sudo mkdir /media/iso

и подключаем:

    sudo modprobe loop
    sudo mount file.iso /media/iso/ -t iso9660 -o loop

Отключаем командой:

    sudo umount /media/iso/
