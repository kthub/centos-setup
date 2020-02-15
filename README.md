# CentOS環境の構築手順
Windows 10のVirtualBox上にCentOSを導入して初期設定する際の手順です。  
手順が確立したらVagrantとansibleを使用して自動的にプロビジョニングできるようにする予定です。

### 前提バージョン
手順を作成した際のバージョンは下記の通り。  
2020/2/15時点の最新版  
|  Software  |  Version  |  Description  |    
| ---- | ---- |  ----  |  
|  CentOS  |  7  |  CentOS-7-x86_64-DVD-1908.iso  |  




### 事前準備
- CentOSのISOイメージのダウンロード  

### VM作成（VirtualBox）
- VirtualBox Managerから新規で作成  

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


### ネットワーク設定
/etc/sysconfig/network-scripts/ifcfg-enp0s3  
/etc/sysconfig/network  
/etc/resolve.conf  

### ソフトウェア導入
- Docker
- 
