# Flash player

Если по какой то причине вы не хотите устанавливать пакет adobe-flashplugin с
Adobe Flash Player, вы можете совершить установку вручную. Для этого загрузите
архив по ссылке (версия .tar.gz) в домашний каталог. После этого распакуйте
содержимое архива в папку с плагинами браузеров. Для этого выполните следующие
команды в терминале:

    sudo tar xvzf install_flash_player_11_linux.i386.tar.gz -C /usr/lib/mozilla/plugins
    sudo rm -r /usr/lib/mozilla/plugins/usr

За работу Adobe Flash Player отвечает файл /usr/lib/mozilla/plugins/libflashplayer.so.
Он будет обнаружен вашим браузером при следующем запуске.
