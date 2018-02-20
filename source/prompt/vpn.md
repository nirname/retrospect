# VPN

Установить `PPTP`:

    sudo apt-get install pptp-linux

Создать файл `/etc/ppp/peers/provider` с содержанием:

    pty "pptp vpn.provider.ru --nolaunchpppd"
    user "username"
    password "password"
    unit 0
    nodeflate
    nobsdcomp
    noauth
    replacedefaultroute
    defaultroute
    persist
    maxfail 0


    /etc/network/insterfaces

Включить VPN

    pon provider

Настроить проброс

    sudo route add -host 1.2.3.4                       ppp1
    sudo route add -net  1.2.0.0 netmask 255.255.255.0 ppp1
