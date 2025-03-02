# WolfiWSL
Tutorial for installing Wolfi WSL images + calling Windows applications without any hassle.

Open the WSL Manager application (download it first from [bostrot/wsl2-distro-manager](https://github.com/bostrot/wsl2-distro-manager) if you don't have it yet), click "<b>Add new instance</b>", then enter the required data.

![](https://raw.githubusercontent.com/cdhtlr/WolfiWSL/main/WSL_Manager.png "WSL Manager")

Open Wolfi from <b>Windows Terminal</b> then enter the following command

    apk update && apk upgrade
    apk add mount libstdc++ bash curl sudo make git --no-cache
    git clone https://github.com/wslutilities/wslu ~/wslu && cd ~/wslu
    bash configure.sh
    make
    sudo make install && sudo install -m755 extras/scripts/wslu-uninstall /usr/bin
    apk del --purge sudo make git && apk cache clean
    echo "echo 'Welcome to WolfiWSL :D'" > /etc/motd
    echo "alias a=wslact" > .profile
    echo "alias s=wslusc" >> .profile
    echo "alias o=wslview" >> .profile
    echo "clear" >> .profile
    echo "/etc/motd" >> .profile
    chmod +x /etc/motd .profile
    rm -rf .ash_history ~/wslu

If you haven't set <i>WSL auto shutdown when idle</i>, shutdown WSL with the following command

    wsl --shutdown

Close Windows Terminal then reopen it.


Open Windows application you need, for example <b>notepad</b>.

    o notepad.exe

Open Microsoft Word file easily.

    o example.docx

## No GUI (WSLg) support because it's Wolfi :)
