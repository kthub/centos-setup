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
Install CentOS 7 を選択  
インストーラが立ち上がる  
日本語を選択  
全てデフォルトでインストールの開始  
rootパスワード`zaq1"wsx`  
user追加`ktsuda` / `qwe234rty`  
再起動して導入完了  

### ネットワーク設定
/etc/sysconfig/network-scripts/ifcfg-enp0s3  
下記を修正または追加
```
BOOTPROTO=static
IPADDR=192.168.1.xxx
NETMASK=255.255.255.0
GATEWAY=192.168.1.1
IPV6INIT=no
IPV6_AUTOCONF=no
IPV6_DEFROUTE=no
ONBOOT=yes
```
/etc/sysconfig/network  
下記を追加
```
NETWORKING=yes
NETWORKING_IPV6=no
GATEWAY=192.168.1.1
```

/etc/resolve.conf  
下記を追加
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

### ソフトウェア導入
- Docker
- 
