# Jarkom_Modul5_Lapres_A06

## Kelompok A06
- 5111840000124	-	Sandra Agnes Oktaviana
- 5111840000165	-	Muhammad Fikri Rabbani

## Tree
![](Image/tree.JPG)

## Pembagian 
![](Image/vlsm.JPG)

## Topologi
```
# Switch
uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch2 > /dev/null < /dev/null &
uml_switch -unix switch3 > /dev/null < /dev/null &
uml_switch -unix switch4 > /dev/null < /dev/null &
uml_switch -unix switch5 > /dev/null < /dev/null &
uml_switch -unix switch6 > /dev/null < /dev/null &

# Router
xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.72.29 eth1=daemon,,,switch4 eth2=daemon,,,switch3 mem=64M &
xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch3 eth1=daemon,,,switch2 eth2=daemon,,,switch1 mem=64M &
xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch4 eth1=daemon,,,switch6 eth2=daemon,,,switch5 mem=64M &

# Server
xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch1 mem=64M &
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch1 mem=64M &
xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch6 mem=64M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch6 mem=64M &

# Client
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch2 mem=64M &
xterm -T GRESIK -e linux ubd0=GRESIK,jarkom umid=GRESIK eth0=daemon,,,switch5 mem=64M &
```

## Perhitungan Netmask
```
SIDOARJO	: 200		
GRESIK		: 210		

 Subnet		Jumlah IP	Netmask	
A1		201		/24
A2		2		/30
A3		2		/30
A4		211		/24
A5		5		/29

Total		421		/23
```

## Range IP
```
A1 192.168.1.0
Batu 192.168.1.1
Sidoarjo 192.168.1.2

A2 192.168.0.0
Batu 192.168.0.1
Surabaya 192.168.0.2

A3 192.168.0.4
Surabaya 192.168.0.5
Kediri 192.168.0.6

A4 192.168.2.0
Kediri 192.168.2.1
Gresik 192.168.2.2

A5 192.168.0.8
Kediri 192.168.0.9
Probolinggo 192.168.0.10
Madiun 192.168.0.11
```

## Interface
```
[MALANG]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.73.60
netmask 255.255.255.248
gateway 10.151.73.62



[MOJOKERTO]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.73.61
netmask 255.255.255.248
gateway 10.151.73.62



[BATU]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.252
gateway 192.168.0.1

auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 10.151.73.62
netmask 255.255.255.248



[SIDOARJO]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1



[SURABAYA]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.72.30
netmask 255.255.255.252
gateway 10.151.72.29

auto eth1
iface eth1 inet static
address 192.168.0.5
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.168.0.2
netmask 255.255.255.252



[KEDIRI]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.6
netmask 255.255.255.252
gateway 192.168.0.5

auto eth1
iface eth1 inet static
address 192.168.0.9
netmask 255.255.255.248

auto eth2
iface eth2 inet static
address 192.168.2.1
netmask 255.255.255.0



[GRESIK]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1



[PROBOLINGGO]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.248
gateway 192.168.0.9



[MADIUN]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.11
netmask 255.255.255.248
gateway 192.168.0.9
```

