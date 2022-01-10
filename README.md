# navicat15-patch
# Navicat15破解

环境：Ubuntu 20.04.3 LTS 64 位

​			Navicat15.0.30 Premium cs

参考教程：https://gitee.com/andisolo/navicat-keygen

#### 1. 下载navicat

下载一个AppImage文件。例如 `navicat15-premium-en.AppImage`。

假定这个AppImage文件在 `~/Desktop` 文件夹下。

#### 2. 提取AppImage文件里的所有文件到一个文件夹。例如：

```shell
mkdir ~/Desktop/navicat15-premium-en
sudo mount -o loop ~/Desktop/navicat15-premium-en.AppImage ~/Desktop/navicat15-premium-en
cp -r ~/Desktop/navicat15-premium-en ~/Desktop/navicat15-premium-en-patched
sudo umount ~/Desktop/navicat15-premium-en
rm -rf ~/Desktop/navicat15-premium-en
```

#### 3. 编译patcher和keygen。

1. 确保你的gcc支持C++17特性

2. 确保你安装了下面几个库：

- `capstone`
- `keystone`
- `rapidjson`
- openssl

你可以通过下面的命令来安装它们：

```shell
# install capstone
$ sudo apt-get install libcapstone-dev

# install keystone
$ sudo apt-get install cmake
$ git clone https://github.com/keystone-engine/keystone.git
$ cd keystone
$ mkdir build
$ cd build
$ ../make-share.sh
$ sudo make install
$ sudo ldconfig

# install rapidjson
$ sudo apt-get install rapidjson-dev

# install openssl
$ sudo apt-get install openssl
```

#### 编译

```shell
$ git clone -b linux --single-branch https://gitee.com/andisolo/navicat-keygen.git 
$ cd navicat-keygen
$ make all
```

生成完成后，你会在 `bin/` 文件夹下看到编译后的keygen/patcher。

#### 4.使用 `navicat-patcher` 替换官方公钥。

```shell
$ ./bin/navicat-patcher ~/Desktop/navicat15-premium-en-patched
```

下面是一份样例输出：

```shell
**********************************************************
*       Navicat Patcher (Linux) by @DoubleLabyrinth      *
*                  Version: 1.0                          *
**********************************************************

Press ENTER to continue or Ctrl + C to abort.

[+] Try to open libcc.so ... Ok!

[+] PatchSolution0 ...... Ready to apply
   RefSegment      =  1
   MachineCodeRva  =  0x0000000001413e10
   PatchMarkOffset = +0x00000000029ecf40

[*] Generating new RSA private key, it may take a long time...
[*] Your RSA private key:
   -----BEGIN RSA PRIVATE KEY-----
   MIIEowIBAAKCAQEArRsg1+6JZxZNMhGyuM8d+Ue/ky9LSv/XyKh+wppQMS5wx7QE
   XFcdDgaByNZeLMenh8sgungahWbPo/5jmkDuuHHrVMU748q2JLL1E3nFraPZqoRD
   ...
   ...
   B1Z5AoGBAK8cWMvNYf1pfQ9w6nD4gc3NgRVYLctxFLmkGylqrzs8faoLLBkFq3iI
   s2vdYwF//wuN2aq8JHldGriyb6xkDjdqiEk+0c98LmyKNmEVt8XghjrZuUrn8dA0
   0hfInLdRpaB7b+UeIQavw9yLH0ilijAcMkGzzom7vdqDPizoLpXQ
   -----END RSA PRIVATE KEY-----
[*] Your RSA public key:
   -----BEGIN PUBLIC KEY-----
   MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArRsg1+6JZxZNMhGyuM8d
   +Ue/ky9LSv/XyKh+wppQMS5wx7QEXFcdDgaByNZeLMenh8sgungahWbPo/5jmkDu
   ...
   ...
   GrVJ3o8aDm35EzGymp4ON+A0fdAkweqKV6FqxEJqLWIDRYh+Z01JXUZIrKmnCkgf
   QQIDAQAB
   -----END PUBLIC KEY-----

*******************************************************
*                   PatchSolution0                    *
*******************************************************
[*] Previous:
+0x0000000000000070                          01 00 00 00 05 00 00 00          ........
+0x0000000000000080  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
+0x0000000000000090  00 00 00 00 00 00 00 00 40 cf 9e 02 00 00 00 00  ........@.......
+0x00000000000000a0  40 cf 9e 02 00 00 00 00 00 10 00 00 00 00 00 00  @...............
[*] After:
+0x0000000000000070                          01 00 00 00 05 00 00 00          ........
+0x0000000000000080  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
+0x0000000000000090  00 00 00 00 00 00 00 00 d0 d0 9e 02 00 00 00 00  ................
+0x00000000000000a0  d0 d0 9e 02 00 00 00 00 00 10 00 00 00 00 00 00  ................

[*] Previous:
+0x00000000029ecf40  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
+0x00000000029ecf50  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
+0x00000000029ecf60  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
...
...
+0x00000000029ed0c0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[*] After:
+0x00000000029ecf40  ef be ad de 4d 49 49 42 49 6a 41 4e 42 67 6b 71  ....MIIBIjANBgkq
+0x00000000029ecf50  68 6b 69 47 39 77 30 42 41 51 45 46 41 41 4f 43  hkiG9w0BAQEFAAOC
+0x00000000029ecf60  41 51 38 41 4d 49 49 42 43 67 4b 43 41 51 45 41  AQ8AMIIBCgKCAQEA
...
...
...
+0x00000000029ed0c0  43 6b 67 66 51 51 49 44 41 51 41 42 ad de ef be  CkgfQQIDAQAB....

[*] Previous:
+0x0000000001413e10  44 0f b6 24 18 48 8b 44 24 28 8b 50 f8 85 d2 79  D..$.H.D$(.P...y
+0x0000000001413e20  6f                                               o               
[*] After:
+0x0000000001413e10  45 31 e4 48 8d 05 2a 91 5d 01 90 90 90 90 90 90  E1.H..*.].......
+0x0000000001413e20  90                                               .               

[*] New RSA-2048 private key has been saved to
   /home/doublesine/github.com/navicat-keygen/RegPrivateKey.pem

*******************************************************
*           PATCH HAS BEEN DONE SUCCESSFULLY!         *
*                  HAVE FUN AND ENJOY~                *
*******************************************************
```

#### 5. 将文件重新打包成AppImage：

```shell
$ wget 'https://github.com/AppImage/AppImageKit/releases/download/continuous/appimagetool-x86_64.AppImage'
# 下载太慢可以更换为https://gitee.com/TestOpsFeng/navicat-backup/blob/master/appimagetool-x86_64.AppImage
$ chmod +x appimagetool-x86_64.AppImage
$ ./appimagetool-x86_64.AppImage ~/Desktop/navicat15-premium-en-patched ~/Desktop/navicat15-premium-en-patched.AppImage
```

#### 6.运行刚生成的AppImage：

```shell
$ chmod +x ~/Desktop/navicat15-premium-en-patched.AppImage
$ ~/Desktop/navicat15-premium-en-patched.AppImage
```

#### 7.使用 `navicat-keygen` 来生成 **序列号** 和 **激活码**。

```shell
$ ./bin/navicat-keygen --text ./RegPrivateKey.pem
# RegPrivateKey.pem为第4步最后输出的路径
```

你会被要求选择Navicat产品类别、Navicat语言版本和填写主版本号。之后一个随机生成的 **序列号** 将会给出。

```shell
$ ./bin/navicat-keygen --text ./RegPrivateKey.pem
**********************************************************
*       Navicat Keygen (Linux) by @DoubleLabyrinth       *
*                   Version: 1.0                         *
**********************************************************

[*] Select Navicat product:
0. DataModeler
1. Premium
2. MySQL
3. PostgreSQL
4. Oracle
5. SQLServer
6. SQLite
7. MariaDB
8. MongoDB
9. ReportViewer

(Input index)> 1

[*] Select product language:
0. English
1. Simplified Chinese
2. Traditional Chinese
3. Japanese
4. Polish
5. Spanish
6. French
7. German
8. Korean
9. Russian
10. Portuguese

(Input index)> 0 # 根据安装的语言选择

[*] Input major version number:
(range: 0 ~ 15, default: 12)> 15

[*] Serial number: #序列号
NAVM-RTVJ-EO42-IODD

[*] Your name:
```

之后你会被要求填写 **用户名** 和 **组织名**。你可以随意填写，但别太长。

```shell
[*] Your name: DoubleLabyrinth
[*] Your organization: DoubleLabyrinth

[*] Input request code in Base64: (Double press ENTER to end)
```

之后你会被要求填写请求码。**注意不要关闭keygen。**

#### 8.**<u>断开网络</u>**. 找到注册窗口，填写keygen给你的 序列号，然后点击 激活。

#### 9. 通常在线激活会失败，所以在弹出的提示中选择 手动激活。

复制 **请求码** 到keygen，连按两次回车结束。

```shell
[*] Input request code in Base64: (Double press ENTER to end) #请求码
OaGPC3MNjJ/pINbajFzLRkrV2OaSXYLr2tNLDW0fIthPOJQFXr84OOroCY1XN8R2xl2j7epZ182PL6q+BRaSC6hnHev/cZwhq/4LFNcLu0T0D/QUhEEBJl4QzFr8TlFSYI1qhWGLIxkGZggA8vMLMb/sLHYn9QebBigvleP9dNCS4sO82bilFrKFUtq3ch8r7V3mbcbXJCfLhXgrHRvT2FV/s1BFuZzuWZUujxlp37U6Y2PFD8fQgsgBUwrxYbF0XxnXKbCmvtgh2yaB3w9YnQLoDiipKp7io1IxEFMYHCpjmfTGk4WU01mSbdi2OS/wm9pq2Y62xvwawsq1WQJoMg==

[*] Request Info:
{"K":"NAVMRTVJEO42IODD", "DI":"4A12F84C6A088104D23E", "P":"linux"}

[*] Response Info:
{"K":"NAVMRTVJEO42IODD","DI":"4A12F84C6A088104D23E","N":"DoubleLabyrinth","O":"DoubleLabyrinth","T":1575543648}

[*] Activation Code: #激活码
i45HIr7T1g69Cm9g3bN1DBpM/Zio8idBw3LOFGXFQjXj0nPfy9yRGuxaUBQkWXSOWa5EAv7S9Z1sljlkZP6cKdfDGYsBb/4N1W5Oj1qogzNtRo5LGwKe9Re3zPY3SO8RXACfpNaKjdjpoOQa9GjQ/igDVH8r1k+Oc7nEnRPZBm0w9aJIM9kS42lbjynVuOJMZIotZbk1NloCodNyRQw3vEEP7kq6bRZsQFp2qF/mr+hIPH8lo/WF3hh+2NivdrzmrKKhPnoqSgSsEttL9a6ueGOP7Io3j2lAFqb9hEj1uC3tPRpYcBpTZX7GAloAENSasFwMdBIdszifDrRW42wzXw==
```

最终你会得到一个base64编码的 **激活码**。

将之复制到 `手动激活` 的窗口，然后点击 `激活`。

如果没有什么意外，应该可以成功激活。
