## set up your personal vpn (v2ray -> vmess)

* requirements: *

- bridge server (ubuntu)
- main server (ubuntu)

# step1: setup main server
ssh to your server and follow this steps
1. ```sudo su```
2. ``` apt update ```
3. ```apt install v2ray ```
4. ```vim /usr/local/etc/v2ray/config.json```
5. copy and paste the attached file " main_server_config.josn "
6. modify this lines 3,12,32 (more info is in the file)
7. save and quit  ( press `:` and type `wq` press `return` )
8. ```v2ray run --config=/usr/local/etc/v2ray/config.json```
9. if there is no error **well down** your main seerver is ready
>now you can make v2ray as a service 
>  ```systemctl enable v2ray.service```
>  ```systemctl start v2ray.service```
>  ```systemctl status v2ray.service```
> check if there is error in v2ray status

# step2: setup bridge sever
ssh to your server and follow this steps
1. ```sudo su```
2. ``` apt update ```
3. ```apt install v2ray ```
4. ```vim /usr/local/etc/v2ray/config.json```
5. copy and paste the attached file " bridge_server_config.josn "
6. modify this lines 9,10,13,47,95,96,99,121 (more info is in the file)
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
##### vmess:
- mac: use v2ray core  (for more info read [this](#) )
- windows: use v2ray aplication 
- ios: use napsternetv
- android: use V2reyNg or oneclick
##### shadowsocks: 
- mac(apple siclicon): use oneclick
- mac(intell): use shadowsocks
- windows: use shadowsocks
- ios: use oneclick
- android: use one click or V2reyNg


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


