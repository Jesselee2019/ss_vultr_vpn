# Background
build shadow-socks vpn in vultr server

There are so many different instructions on the internet, after many hours work, it finally works. So decided build my own instruction for my-self.

# Start a server
Just use/buy the cheapest one. But for curiousity, I searched that 'what hardware will affect as a VPN server?', the answer is CPU and network.

10/03 update: 
The reason why CPU is essential that depends on how many users using it. Like we have a multi-tasks env, and need a strong core to process every single task.

# TLDR (update 10/03)
```
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/Jesselee2019/ss_vultr_vpn/refs/heads/main/shadowsocks-all.sh

chmod +x shadowsocks-all.sh

./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```

1. Select 'shadowsocks-Go'
2. Password
3. Port (8989)
4. Protocal (#7)

# Install Shadowsocks
Commands:
```
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh

chmod +x shadowsocks-all.sh

./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```

Steps after run commands:
1. server type
2. password
3. port (I picked 8989)

One instresting in thing I was found that:
1. They are using basically the same people's (teddysun) code script
2. The code script have different version, the shadowsocks-python.sh is one of them, the command I pasted here is for -all.
3. -all version have different types inside.
4. The port is wired, somehow I didn't setup firewall or open the port for anyone, but it just works. will leave more thinking path below.

# Important to know
The above script is wrong/outdated, because the python is now fully support python3. So when you install the server, it might show that 'installed fail ptyhon..'
To solve this problem, need to update the script. To save my time, I replaced the keyword `python` to `python3`.
Used commands below:
```
sed -i 's/python-dev/python3-dev/g' shadowsocks.sh
sed -i 's/python-setuptools/python3-setuptools/g' shadowsocks.sh
sed -i 's/python /python-is-python3 /g' shadowsocks.sh
```

I build my own script, it's private, copy the raw link with token should be able to use. Please try in the future see if it works.

# Some useful commands
1. check server status
   `systemctl status shadowsocks-go.service`
2. check ports status
   `ufw status`

# Ref
https://mcl-123.github.io/2019/03/19/Vultr-%E6%90%AD%E5%BB%BA-shadowsocks-%E6%95%99%E7%A8%8B/
https://github.com/moraaah/Vultr-Shadowsocks?tab=readme-ov-file
https://jackmezone.medium.com/%E7%A7%91%E5%AD%A6%E4%B8%8A%E7%BD%91-vultr-vps-%E6%90%AD%E5%BB%BA-shadowsocks-ss-%E6%95%99%E7%A8%8B-%E6%96%B0%E6%89%8B%E5%90%91-968613081aae
