# cyber-kozhi T bomb
Cyber kozhi bot 0.1
TBomb.sh           [----]  0 L:[ 29+111 140/140] *(3532/3532b) <EOF>                                                                                                       [*][X]
    if ! [ -x "$(command -v figlet)" ]; then
        echo 'Introducing TBomb'
    else
        figlet TBomb
    fi
    if ! [ -x "$(command -v toilet)" ]; then
        echo -e "\e[4;34m This Bomber Was Created By \e[1;34m cyber kozhi \e[0m"
    else
        echo -e "\e[1;34mCreated By \e[1;34m"
        toilet -f mono12 -F border cyberkozhi
    fi
    echo -e "\e[1;34m For Any Queries massage me!!!\e[0m"
    echo -e "\e[1;32m            instagram pakka_nonsense  \e[0m"
    echo -e "\e[4;32m   I LOVE U KESHU \e[0m"
    echo " "

}

init_environ(){
    declare -A backends; backends=(
        ["arch"]="pacman -S --noconfirm"
        ["debian"]="apt-get -y install"
        ["ubuntu"]="apt -y install"
        ["termux"]="apt -y install"
        ["fedora"]="yum -y install"
        ["redhat"]="yum -y install"
        ["SuSE"]="zypper -n install"
        ["sles"]="zypper -n install"
        ["darwin"]="brew install"
        ["alpine"]="apk add"
    )

    INSTALL="${backends[$distro]}"

    if [ "$distro" == "termux" ]; then
        PYTHON="python"
        SUDO=""
    else
        PYTHON="python3"
        SUDO="sudo"
    fi
    PIP="$PYTHON -m pip"
}

install_deps(){
....
    packages=(openssl git $PYTHON $PYTHON-pip figlet toilet)
    if [ -n "$INSTALL" ];then
        for package in ${packages[@]}; do
            $SUDO $INSTALL $package
        done
        $PIP install -r requirements.txt
    else
        echo "We could not install dependencies."
        echo "Please make sure you have git, python3, pip3 and requirements installed."
        echo "Then you can execute bomber.py ."
        exit
    fi
}

banner
pause
detect_distro
init_environ
if [ -f .update ];then
    echo "All Requirements Found...."
else
    echo 'Installing Requirements....'
    echo .
    echo .
    install_deps
    echo This Script Was Made By SpeedX > .update
    echo 'Requirements Installed....'
    pause
fi
while :
do
    banner
    echo -e "\e[4;31m Please Read Instruction Carefully !!! \e[0m"
    echo " "
    echo "Press 1 To  Start SMS  Bomberð..💬.💣 "
    echo "Press 2 To  Start CALL Bomber📞💣 "
    echo "Press 3 To  Start MAIL Bomber💌💣 (Not Yet Available)"
    echo "Press 4 To  Update (Works On Linux And Linux Emulators) "
    echo "Press 5 To  Exit "
    read ch
    clear
    if [ $ch -eq 1 ];then
        $PYTHON bomber.py --sms
        exit
    elif [ $ch -eq 2 ];then
        $PYTHON bomber.py --call
        exit
    elif [ $ch -eq 3 ];then
        $PYTHON bomber.py --mail
        exit
    elif [ $ch -eq 4 ];then
        echo -e "\e[1;34m Downloading Latest Files..."
        rm -f .update
        $PYTHON bomber.py --update
        echo -e "\e[1;34m RUN TBomb Again..."
        pause
        exit
    elif [ $ch -eq 5 ];then
        banner
        exit
    else
        echo -e "\e[4;32m Invalid Input !!! \e[0m"
        pause
    fi
done






