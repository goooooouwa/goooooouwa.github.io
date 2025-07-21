---
title: How to use shadowsocks
category: coding
tags: shadowsocks
published: true
---
# Server Side
## Install
### Mac
```python
easy_install pip
pip install shadowsocks
```

### Linux
```bash
apt-get install python-pip
pip install shadowsocks
```

## Usage
### command line config
`$ ssserver -p 443 -k password -m aes-256-cfb`

### or with config file
```json
// in config.json
{
"server”:”192.168.31.233”,
"server_port":8000,
"local_address":"127.0.0.1",    // these 2 config are actually for client
"local_port":1080,    // just put it here for convinence
"password":"your-password",
"timeout":600,
"method":"aes-256-cfb"
}
```

`$ ssserver -c ./config.json`

# Client Side
## Install on Linux
```bash
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
```

## Usage
- Open Shadowsocks-Qt5, Add connection based on the config in server-side.
- Open System Settings > Network > Proxy, In Socks Host, fill ‘127.0.0.1’ and ‘1080’ (based on client-side configuration)