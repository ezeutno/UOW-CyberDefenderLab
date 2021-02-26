# UOW's CyberDefender Workshop 2021
This is a CyberDefender workshop help by UOW on the 1st of April 2021 09:00 am.

## Setup the environment
1. Install VirtualBox - https://www.virtualbox.org/wiki/Downloads
2. Install VirtualBox Extention Pack
3. Install Vagrant - https://www.vagrantup.com/docs/installation
4. Clone Github Repository

    Via SSH
    ```
    git clone git@github.com:ezeutno/UOW-CyberDefenderLab.git
    ```
    or via Git
    ```
    git clone https://github.com/ezeutno/UOW-CyberDefenderLab.git
    ```
    or Download the Zip file

5. Setup NatNetwork,

    Through CLI
    ```
    vboxmanage natnetwork add --netname NatNetwork --network 10.0.2.0/24 --dhcp off
    ```
    Note: Windows' user need to add `C:/ProgramFiles/Oracle/Virtualbox` to their environment path

    Through Console
    1. Navigate to `File` > `Preferences` > `Network`
    2. Add Network 'usng the [+] icon'
    3. Untick Supports DHCP
    4. Change the Network Name to NatNetwork

6. Execute Vagrant Command
    ```
    vagrant up
    ```

## Clear the environment
1. Execute vagrant down
    ```
    vagrant down
    ```
2. Remove the NatNetwork
    ```
    vboxmanage natnetwork add --netname NatNetwork --network 10.0.2.0/24 --dhcp off
    ```