# CentOS環境の構築手順
Windows 10のVirtualBox上にCentOSを導入して初期設定する際の手順です。  
手順が確立したらVagrantとansibleを使用して自動的にプロビジョニングできるようにする予定です。

### 前提バージョン
手順を作成した際のバージョンは下記の通り。（2020/2/15時点の最新版）  
|  Software  |  Version  |  Description  |    
| ---- | ---- |  ----  |  
|  CentOS  |  7.7.1908  |  CentOS-7-x86_64-DVD-1908.iso  |  


### VM作成（VirtualBox）
VirtualBox Managerから新規で作成して下記の設定を行う。  

|  設定項目  |  設定値  |  
| ---- | ---- |  
|  メモリ  |  4GB  |  
|  仮想HDD  |  40GB  |  

- ディスプレイ設定  
グラフィックスコントローラを`VBoxSVGA`に設定  
  
- ストレージ設定  
光学ドライブにCentOSのISOを指定  
  
- ネットワーク設定  
アダプター1にブリッジアダプターを割当て  

### OSインストール
VirtualBox Managerから起動  
1. Install CentOS 7 を選択してインストーラを起動  
2. 言語で`日本語`を選択  
3. 全てデフォルトで`インストールの開始`  
4. 下記のユーザーを作成  
root / zaq1"wsx  
ktsuda / qwe234rty  
5. 再起動して導入完了  

### ネットワーク設定
/etc/sysconfig/network-scripts/ifcfg-enp0s3  
```
BOOTPROTO=static
IPADDR=192.168.1.200
NETMASK=255.255.255.0
GATEWAY=192.168.1.1
IPV6INIT=no
IPV6_AUTOCONF=no
IPV6_DEFROUTE=no
ONBOOT=yes
```
/etc/sysconfig/network  
```
NETWORKING=yes
NETWORKING_IPV6=no
GATEWAY=192.168.1.1
HOSTNAME="wasnd01"
```

/etc/resolve.conf  
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

/etc/hosts
```
#127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
#::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
127.0.0.1   wasnd01 localhost localhost.localdomain localhost4 localhost4.localdomain4
192.168.1.200 wasnd01
192.168.1.201 wasnd02
```

### ソフトウェア導入
- yumの更新  
```
yum update
```
- Docker  
TBD
