# Konfigurasi SSH

## SSH
Buka file konfigurasi SSH dengan perintah berikut:
```
sudo nano /etc/ssh/sshd_config
```
Cari baris yang berisi:
```
Port 10000
```
Ubah menjadi:
```
Port 2222
```

# Firewalld
remove port 10000
```
sudo firewall-cmd --remove-port=10000/tcp --permanent
```
allow port 2222
```
sudo firewall-cmd --permanent --add-port=2222/tcp
```
reload firewalld
```
sudo firewall-cmd --reload
```
check firewalld
```
sudo firewall-cmd --list-all
```

## SELinux
menampilkan daftar port yang dikonfigurasi dalam SELinux
```
sudo semanage port -l | grep ssh
```
Menambah port 2222 ke kebijakan SELinux:
```
sudo semanage port -a -t ssh_port_t -p tcp 2222
```

## SSH
restart SSH
```
sudo systemctl restart sshd
```
uji coba login SSH
```
ssh username@<IP Your SSH> -p <Port your SSH>
```

