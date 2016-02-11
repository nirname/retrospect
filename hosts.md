# Hosts

Modifying your hosts file allows you to override the DNS for a domain, on that particular machine. This is useful when you want to test your site without the test link, prior to going live with SSL; verify that an alias site works, prior to DNS changes; and for other DNS-related reasons. Modifying your hosts file causes your local machine only to look directly at the IP address specified.

You need to add two entries to your hosts file that contain the IP address that you want the site to resolve to and the address. Adding the following two lines, for example, point www.domain.com and domain.com to our current PHP5-ITK ("Refreshed" PHP5) cluster:

    64.49.219.194 www.domain.com
    64.49.219.194 domain.com

The following sections provide instructions for locating and editing the hosts file on several operating systems. After you add the domain information and save the file, your system begins resolving to the specified IP address. After testing is finished, remove these entries.

    Windows 8, Windows 7, and Windows Vista
    Windows NT, Windows 2000, and Windows XP
    Linux
    Mac OS X 10.0 through 10.1.5
    Mac OS X 10.6 through 10.8

Windows 8, Windows 7, and Windows Vista

Windows 8, Windows 7, and Windows Vista use User Account Control (UAC), so Notepad must be run as Administrator.

For Windows 8

    Press the Windows key.
    Type Notepad in the search field.
    In the search results, right-click Notepad and select Run as administrator.
    In Notepad, open the following file: c:\Windows\System32\Drivers\etc\hosts
    Make the necessary changes to the file.
    Click File > Save to save your changes.

For Windows 7 and Windows Vista

    Click Start > All Programs > Accessories.
    Right-click Notepad and select Run as administrator.
    Click Continue on the Windows needs your permission UAC window.
    When Notepad opens, click File > Open.
    In the File name field, type C:\Windows\System32\Drivers\etc\hosts.
    Click Open.
    Make the necessary changes to the file.
    Click File > Save to save your changes.

Windows NT, Windows 2000, and Windows XP

    Click Start > All Programs > Accessories > Notepad.
    Click File > Open.
    In the File name field, type C:\Windows\System32\Drivers\etc\hosts.
    Click Open.
    Make the necessary changes to the file.
    Click File > Save to save your changes.

Linux

    Open a terminal window.
    Open the hosts file in a text editor (you can use any text editor) by typing the following line:

    sudo nano /etc/hosts

    Enter your domain user password.
    Make the necessary changes to the file.
    Press Control-x.
    When asked if you want to save your changes, answer y.

Mac OS X 10.0 through 10.1.5

    Open /Applications/Utilities/NetInfo Manager.
    To allow editing of the NetInfo database, click the padlock in the lower-left corner of the window.
    Enter your domain user password and click OK.
    In the second column of the browser view, select the node named machines.
    You will see entries for -DHCP-, broadcasthost, and localhost in the third column.
    In the third column, select localhost.
    From the Edit menu, select Duplicate. (The quickest way to create a new entry is to duplicate an existing one.)
    A confirmation alert appears.
    Click Duplicate.
    A new entry called localhost copy appears, and its properties are shown below the browser view.
    Double-click the value of the ip_address property and enter the IP address of the other computer.
    Double-click the value of the name property and enter the hostname you want for the other computer.
    Click the serves property and select Delete from the Edit menu.
    From the File menu, select Save.
    A confirmation alert appears.
    Click Update this copy.
    Repeat steps 6 through 12 for each additional host entry that you want to add.
    From the NetInfo Manager menu, select Quit.
    You do not need to restart the computer.

Mac OS X 10.6 through 10.8

    Open Applications > Utilities > Terminal.
    Open the hosts file by typing the following line in the terminal window:

    sudo nano /private/etc/hosts

    Type your domain user password when prompted.
    Edit the hosts file.
    The file contains some comments (lines starting with the # symbol), and some default hostname mappings (for example, 127.0.0.1 – local host). Add your new mappings after the default mappings.
    Save the hosts file by pressing Control+x and answering y.
    Make your changes take effect by flushing the DNS cache with the following command:

    dscacheutil -flushcache

    The new mappings should now take effect.
