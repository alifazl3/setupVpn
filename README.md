# set up your personal vpn 
### (v2ray -> vmess & shadowsocks)


### requirements: *

- bridge server (ubuntu)
- main server (ubuntu)

## step1: setup main server
ssh to your server and follow this steps
1. ```sudo su```
2. ``` apt update ```
3. ```bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh)``` or(if not worked caused by internet restriction) ```apt install v2ray ```  
4. ```vim /usr/local/etc/v2ray/config.json```
5. copy and paste the attached file [main_server_config.josn](/configs/main_server_config.json) 
6. **modify** this lines **3,12,32** (more info is in the file)
7. save and quit  ( press `:` and type `wq` press `return` )
8. ```v2ray run --config=/usr/local/etc/v2ray/config.json```
9. if there is no error **well down** your main seerver is ready
>now you can make v2ray as a service 
>  ```systemctl enable v2ray.service```
>  ```systemctl start v2ray.service```
>  ```systemctl status v2ray.service```
> check if there is error in v2ray status

## step2: setup bridge sever
ssh to your server and follow this steps
1. ```sudo su```
2. ``` apt update ```
3. ```apt install v2ray ```
4. ```vim /usr/local/etc/v2ray/config.json```
5. copy and paste the attached file [bridge_server_config.josn](/configs/bridge_server_config.json)
6. **modify** this lines **9,10,13,47,95,96,99,121** (more info is in the file)
7. save and quit  ( press `:` and type `wq` press `return` )
8. ```v2ray run --config=/usr/local/etc/v2ray/config.json```
9. if there is no error **well down** your main seerver is ready
>now you can make v2ray as a service 
>  ```systemctl enable v2ray.service```
>  ```systemctl start v2ray.service```
>  ```systemctl status v2ray.service```
> check if there is error in v2ray status

#### at this point your servers are ready! 
you can connect your servers through vmess and shadowsocks

<hr>

# client
##### vmess:
- mac: use v2ray core  (for more info read [this](#connect-vmess-on-mac))
- windows: use [v2ray aplication](/client/windows/v2rayN-Core.zip)
- ios: use napsternetv [download](https://apps.apple.com/app/id1629465476)
- android: use [V2reyNg](/client/android/v2rayNG.apk) or [oneclick](/client/android/oneclick.apk)
##### shadowsocks: 
- mac(apple siclicon): use oneclick [download](https://apps.apple.com/us/app/oneclick-safe-easy-fast/id1545555197)
- mac(intell): use [shadowsocks](/client/mac/ShadowsocksX-NG.1.9.4.zip)
- windows: use [shadowsocks](/client/windows/Shadowsocks-4.4.1.0.zip)
- ios: use oneclick [download](https://apps.apple.com/app/id1545555197)
- android: use one click or [V2reyNg](/client/android/v2rayNG.apk)

<hr>


### connect vmess on mac 
make sure you installed homebrew ([install brew](https://brew.sh))
1. open terminal (press `cmd + space` and type `terminal` press `return` or open in utility folder)
2. `brew install v2ray`
3. copy "mac_config.josn"file to your home directory and rename to config.json
4. modify this lines 52,53,59,78 (more info is in the file)
5. `v2ray run --config=config.json` 
6. make new terminal window `cmd`+`n`
7. `networksetup -setsocksfirewallproxy wi-fi 127.0.0.1 10808`
8. to disable vpn use `networksetup -setsocksfirewallproxystate Wi-Fi off` and stop first window using `^`+`c`


<hr>

### need to monitor your server resources??

#### cpu:

use ```top -i``` it is ubuntu built in command

#### network card:

```apt install slurm```

```ip link show```

```slurm -i <ANY-CARD>```

<hr>


### how to share
vmess:

* modfidy this json:

```{"add":"ip","aid":"alertId","host":"hostUrl","id":"USER_ID","net":"tcp","path":"","port":"Port","ps":"PROFILE_DISPLAY_NAME","scy":"auto","sni":"","tls":"","type":"http","v":"2"}```

* make it base 64 [online base64 encoder](https://www.base64encode.org/)
* use this pathern ```vmess://{BASE64}```

shadow socks:
* chacha20-ietf-poly1305:**UUID**
* make it base 64 [online base64 encoder](https://www.base64encode.org/)
* use this pathern ```ss://{BASE64}@ip:port#%remark```

