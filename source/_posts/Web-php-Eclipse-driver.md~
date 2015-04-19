title: "Web + php + Eclipse + linux driver"
date: 2015-04-20 00:12:12
tags:
categories: 工作
---
這篇是給自己看的工作紀錄，主要是要透過 Web 來選取資訊並傳輸到 linux driver 處

#1. Pre-Work#

安裝必要套件
```{bash}
$ sudo apt-get install ssh vim openjdk-7-jdk g++ libjsoncpp-dev libncurses5 libncurses5-dev fakeroot build-essential kernel-package
```
建立使用 debugfs 的 folder
```{bash}
$ mkdir ~/debugfs
```

#2. Build kernel image#
下載好後，以 linux-4.0 為例，進到 linux-4.0 資料夾內
調整所需要的 build in or module 選項
```{bash}
$ make menuconfig
```

清除後，利用 fakeroot 建立 image 與 header file
也可在最後加入 -j4表示有4個核心來加快編譯速度
```{bash}
$ make-kpkg clean
$ fakeroot make-kpkg --initrd kernel_image kernel_headers -j4
```

Build完後，會在上層目錄中產生出 image 與 header file
接著進行安裝
```{bash}
$ sudo dpkg -i linux-image-4.0.0_4.0.0-10.00.Custom_amd64.deb
$ sudo dpkg -i linux-headers-4.0.0_4.0.0-10.00.Custom_amd64.deb
```

Problem: Unable to lock the administration directory (/var/lib/dpkg/) is another process using it?

```{bash}
$ sudo rm /var/lib/apt/lists/lock
$ sudo rm /var/cache/apt/archives/lock
```

Problem: Cannot create /etc/apt/apt.conf.d//01autoremove-kernels.dpkg-new: Permission denied
```{bash}
Download kernel-package_13.003_all.deb
$ sudo dpkg -i kernel-package_13.003_all.deb
```

#3. Web#
架 apache server
```{bash}
$ sudo apt-get install lamp-server^
$ sudo apt-get install libapache2-mod-auth-mysql
```

為了讓 www-data 這個 user 可以擁有 root 權限
增加一行
```{bash}
$ sudo vim /etc/sudoers
www-data        ALL=(ALL) NOPASSWD: ALL
```

更改 php 設定值
```{bash}
$ sudo vim /etc/php5/apache2/php.ini
upload_max_filesize = 20M
max_file_uploads = 30
```
複製原本資料 + www資料夾權限設定(不確定)
```{bash}
$ sudo cp -R ~/Desktop/backup/kgcTester/html/nnc .
$ sudo chown -R vli:vli nnc
$ chmod 751 emmc/
$ cd emmc/
$ chmod 754 bjaxSend.html
$ cd statusFiles/
$ chmod 772 CMD.json
$ chmod 770 nncTester
$ chmod 753 uploadFiles/
```

#4. Eclipse CDT#

Download Eclipse CDT from eclipse web site

Instal JSON package
C/C++ Build->Settings->GCC C++  Compile->include加入/usr/include/jsoncpp/，/opt/local/include/
C/C++ Build->Settings->GCC C++  Compile->Dialect->Language standard 選   ISO C++11(-std=c++0x) PS:因為這個測試函數用到C++11的語法。






