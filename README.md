# Langkah-Instal-DNS-SERVER
root@smkmanusa:~# apt-cdrom add
root@smkmanusa:~# apt update
Masukkan cd 3
root@smkmanusa:~# apt-cdrom add
root@smkmanusa:~# apt update

Instalasi aplikasi dhcp dan squid

root@smkmanusa:~# apt install net-tools isc-dhcp-server squid squid-common 
klo ada tulisan seperti bawah
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@smkmanusa:~# apt --fix-broken install ➔minta masukan cd tergantun permitaan
root@smkmanusa:~# apt --fix-broken install ➔minta masukan cd tergantun permitaan
klo ada tulisan seperti bawah
Processing triggers for systemd (241-7~deb10u7) ...sudah berasil
root@smkmanusa:~# apt install net-tools isc-dhcp-server squid squid-common ➔ mintamasukan cd 1 .APT had planned for dpkg to do more than it reported back (24 vs 26).
Affected packages:
root@smkmanusa:~# nano /etc/default/isc-dhcp-server

Tambakan INTERFACESv4="ens33"

root@smkmanusa:~# nano /etc/dhcp/dhcpd.conf

Hilangkan tanda #(Pagar) pada baris:
subnet 172.30.1.0 netmask 255.255.255.224 {
range 172.30.1.2 172.30.1.14;
option domain-name-servers 172.30.1.1;
option domain-name "smkmanusa.sch.id";
option routers 172.30.1.1;
option broadcast-address 172.30.1.15;
default-lease-time 600;
max-lease-time 7200;}

Keluar dan simpan. (tekan ctrl + x) y
Restart service dhcp-nya
# service isc-dhcp-server restart

Pengujian koneksi dari sisi PC Client
Pasan kabel UTP dari server ke client windows.
PC client di set IP address ke DHCP (Obtain IP address# automatically) kemudian pilih OK
Pastikan PC client mendapatkan IP address 172.30.1.2 danseterusnya.
Jika tidak ulangi langkah di atas.
Buka aplikasi CMD, dan ping ke IP address server(172.30.1.1)
C:/>ping 172.30.1.2
(pastikan reply di semua hasil ping)
