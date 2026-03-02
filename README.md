# shsx
repository to save shsx auto install script. It seems to support for only centos.

### 1. deploy the Vultr server

#### (1) create the vultr server

You first need to create a server by yourself at [Vultr website](https://my.vultr.com/deploy/), and log in the newly created server via ssh (It may take a few minutes for the server to be ready).

```bash
# log in the server via ssh
ssh root@149.28.76.116
# type in the pass (copy and paste from the Vultr instance)
```

### (2) latest method

```bash
bash <(wget -qO- https://raw.githubusercontent.com/yonggekkk/sing-box-yg/main/sb.sh)
```

#### speed up

```
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh"
chmod +x tcp.sh
./tcp.sh
```

**Note:** if you use hiddify to connect the vpn, gdrive cli may have some problem. You should run hiddify with root privilidge in the command line (go to Applications - Hiddify - right click and show pkg contents - MacOS).

```
sudo ./hiddyfy
```

After this, you should **switch to VPN model** (not system vpn) and **turn on the Enable TSL Fragment**. With this, you should be able to use gdrive in your terminal.
  

### (3) install wireguard (more stable connection for gdrive)

Open the ports

```
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F
```

Use the default IPv4 address, port (51820) and name.

```
# install wireguard
wget https://git.io/wireguard -O wireguard-install.sh && bash wireguard-install.sh
```

#### Retired installations for wireguard and shadowsocks: (2) deploy the environment in the server

you can install the wireguard with the `wireguard-install.sh` script. See also this [git repository](https://github.com/angristan/wireguard-install/tree/master), and [short video](https://www.youtube.com/shorts/1likZM_I9oY).
```
curl -O https://raw.githubusercontent.com/angristan/wireguard-install/refs/heads/master/wireguard-install.sh
chmod +x wireguard-install.sh
sudo ./wireguard-install.sh
```

Pls don't use kitty terminal to run the following scripts. Better use WezTerm.

```bash
wget --no-check-certificate -O shadowsocks.sh https://raw.githubusercontent.com/JakeJing/shsx/master/shadowsocks.sh

chmod +x shadowsocks.sh

./shadowsocks.sh 2>&1 | tee shadowsocks.log

# Congratulations, Shadowsocks-python server install completed!
# Your Server IP        :  149.28.76.116 
# Your Server Port      :  123
# Your Password         :  teddysun.com 
# Your Encryption Method:  aes-256-cfb 
```

#### (3) download the shadowsocks and add the info

After that, you will get the necessary info (IP address, port id and pass) for log in the vpn. You just need to add the info to shadowsocks.

### Useful link:

- https://teddysun.com/342.html
- https://gitlab.com/zhifan999/fq/-/wikis/%E8%87%AA%E5%BB%BAv2ray%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%95%99%E7%A8%8B
