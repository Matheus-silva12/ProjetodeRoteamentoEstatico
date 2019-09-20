# ProjetodeRoteamentoEstatico 
enable
configure terminal
hostname RT-01
banner motd "ACESSO APENAS PARA PESSOAS AUTORIZADAS"
enable secret SenhadaEnable
ip domain-name peachanddaisy.local
crypto key generate rsa general-keys modulus 1024
line vty 0 15
password SenhadaVTY
login
transport input ssh
exec-timeout 3
exit
username administrador privilege 15 secret SenhaAdm 
username estagiario privilege 1 secret senhaest
line console 0
password SenhadaConsole
login
exit
service password-encryption
interface gigabitEthernet 0/0
ip add 192.168.1.1 255.255.255.224
description REDE 192.168.1.0/27
no shutdown
exit
interface serial 0/0/0
ip address 200.200.100.1 255.255.255.252
description REDE 200.200.100.0/30
no shutdown 
exit
interface serial 0/0/1
ip address 200.200.100.5 255.255.255.252
description REDE 200.200.100.0/30
no shutdown 
exit
ip route 192.168.0.0 255.255.255.128 200.200.100.6
ip route 192.168.0.0 255.255.255.128 200.200.100.2
ip route 10.40.16.0 255.255.240.0 200.200.100.6
ip route 10.40.16.0 255.255.240.0 200.200.100.2
ip route 172.16.42.0 255.255.254.0 200.200.100.6
ip route 172.16.42.0 255.255.254.0 200.200.100.2
ip route 200.200.100.8 255.255.255.252 200.200.100.6
ip route 200.200.100.8 255.255.255.252 200.200.100.2
ip route 200.200.100.12 255.255.255.252 200.200.100.6
ip route 200.200.100.12 255.255.255.252 200.200.100.2
do wr
interface gigabitEthernet 0/0
ip add 192.168.0.1 255.255.255.128
description REDE 192.168.0.0/25
no shutdown
exit
interface serial 0/0/0
ip address 200.200.100.6 255.255.255.252
description REDE 200.200.100.4/30
no shutdown 
exit
interface serial 0/0/1
ip address 200.200.100.9 255.255.255.252
description REDE 200.200.100.8/30
no shutdown 
exit
ip route 192.168.1.0 255.255.255.224 200.200.100.5
ip route 192.168.1.0 255.255.255.224 200.200.100.10
ip route 172.16.42.0 255.255.254.0 200.200.100.5
ip route 172.16.42.0 255.255.254.0 200.200.100.10
ip route 10.40.16.0 255.255.240.0 200.200.100.5
ip route 10.40.16.0 255.255.240.0 200.200.100.10
ip route 200.200.100.0 255.255.255.252 200.200.100.5
ip route 200.200.100.0 255.255.255.252 200.200.100.10
ip route 200.200.100.12 255.255.255.252 200.200.100.5
ip route 200.200.100.12 255.255.255.252 255.255.255.100.10
interface gigabitEthernet 0/0
ip address 172.16.42.1 255.255.254.0
description REDE 4
no shutdown
exit
interface serial 0/0/0
ip address 200.200.100.10 255.255.255.252
description WAN 4-3
no shutdown
exit
interface serial 0/0/1
ip address 200.200.100.13 255.255.255.252
description WAN 4-2
no shutdown
exit
ip route 192.168.1.0 255.255.255.224 200.200.100.9
ip route 192.168.1.0 255.255.255.224 200.200.100.14
ip route 10.40.16.0 255.255.240.0 200.200.100.9
ip route 10.40.16.0 255.255.240.0 200.200.100.14
ip route 192.168.0.0 255.255.255.192 200.200.100.9
ip route 192.168.0.0 255.255.255.192 200.200.100.14
ip route 200.200.100.0 255.255.255.252 200.200.100.9
ip route 200.200.100.0 255.255.255.252 200.200.100.14
ip route 200.200.100.4 255.255.255.252 200.200.100.9
ip route 200.200.100.4 255.255.255.252 200.200.100.14
do wr
interface gigabitEthernet 0/0
ip address 10.40.16.1 255.255.240.0
description REDE 2
no shutdown
exit
interface serial 0/0/0
ip address 200.200.100.2 255.255.255.252
description WAN 2-1
no shutdown
exit
interface serial 0/0/1
ip address 200.200.100.14 255.255.255.252
description WAN 2-4
no shutdown
exit
ip route 192.168.1.0 255.255.255.224 200.200.100.1
ip route 192.168.1.0 255.255.255.224 200.200.100.13
ip route 192.168.0.0 255.255.255.192 200.200.100.1
ip route 192.168.0.0 255.255.255.192 200.200.100.13
ip route 172.16.42.0 255.255.254.0 200.200.100.1
ip route 172.16.42.0 255.255.254.0 200.200.100.13
ip route 200.200.100.8 255.255.255.252 200.200.100.1
ip route 200.200.100.8 255.255.255.252 200.200.100.13
ip route 200.200.100.4 255.255.255.252 200.200.100.1
ip route 200.200.100.4 255.255.255.252 200.200.100.13
do wr


enable
configure terminal
hostname SW-01
banner motd "ACESSO AUTORIZADO APENAS PARA PESSOAS AUTORIZADAS!"
enable secret SenhadaEnable
ip domain-name peachanddaisy.local
crypto key generate rsa general-keys modulus 1024
username administrador privilege 15 secret SenhaAdmin
username estagiario privilege 1 secret SenhaEst
line console 0
password SenhadaConsole
login
exit
service password-encryption
line vty 0 15
password SenhadaVTY
transport input ssh
exec-timeout 5
login local
exit
interface vlan 1
ip address 192.168.1.1 255.255.255.224
description INTERFACE DE GERENCIAMENTO
no shutdown
exit
ip default-gateway 192.168.1.0
do wr
