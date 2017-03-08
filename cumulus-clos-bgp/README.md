# CumulusVXを使ってBGPのCLOS Networkを構築する
## 下準備
### Requirements
* Cumulus VX requires Vagrant 1.7 - 1.9.1
** 2017/03/08時点の最新は1.9.2
* Understand these VirtualBox considerations

### Install Vagrant
* https://releases.hashicorp.com/vagrant/1.8.7/ から [vagrant_1.8.7.dmg] (https://releases.hashicorp.com/vagrant/1.8.7/vagrant_1.8.7.dmg)をダウンロード
* 1.9.x だとうまくいかなかったりしたので、過去に使用していたバージョンを使用
```bash
$ vagrant --version
Vagrant 1.8.7
```

### Install Cumulus plugin
```bash
$ vagrant plugin install vagrant-cumulus                                                                                         
Installing the 'vagrant-cumulus' plugin. This can take a few minutes...
Installed the plugin 'vagrant-cumulus (0.1)'!

$ vagrant plugin list  
vagrant-cumulus (0.1)
vagrant-share (1.1.6, system)
```
:exclamation:うまくいかないときに
```bash
$ rm ~/.vagrant.d/plugins.json
```

### Download VX
VAGRANTBOXを選択 (Downloadにはアカウント登録が必要)
![Cumulus VX 3.2.1](https://github.com/kfukai/Images/blob/master/SCREENSHOT-2017-0309-0236.png)

### Add box
```bash                                    
$ vagrant box add cumulus-linux-3.2.1 ~/Downloads/cumulus-linux-3.2.1-vx-amd64-1486153138.ac46c24zd00d13e.box
==> box: Box file was not detected as metadata. Adding it directly...
==> box: Adding box 'cumulus-linux-3.2.1' (v0) for provider:
    box: Unpacking necessary files from: file:///Users/kfukai/Downloads/cumulus-linux-3.2.1-vx-amd64-1486153138.ac46c24zd00d13e.box
==> box: Successfully added box 'cumulus-linux-3.2.1' (v0) for 'virtualbox'!
$ vagrant box list
cumulus-linux-3.2.1 (virtualbox, 0)
```
:exclamation:うまくいかないときに
```bash
$ sudo mv /opt/vagrant/embedded/bin/curl /opt/vagrant/embedded/bin/curl.bk
```

### 参考URL
* https://docs.cumulusnetworks.com/display/VX/Using+Cumulus+VX+with+Vagrant
* https://github.com/CumulusNetworks/cumulus-vx-vagrant/tree/master/vagrant/demos/clos-bgp
