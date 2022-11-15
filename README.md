# EhViewer

![Icon](art/launcher_icon-web.png)

这是一个 E-Hentai Android 平台的浏览器。

An E-Hentai Application for Android.


# 数据

1. 由于原作者NekoInverter的[EhViewer](https://gitlab.com/NekoInverter/EhViewer/)项目（俗称白E）已不再更新，加上最近官网的接口进行整改，导致无法翻页等问题

2. 原本打算向[Ehviewer-Overhauled](https://github.com/Ehviewer-Overhauled/Ehviewer)学习，将一些更新内容填补上，然后再打包，这样可以不需要迁移数据的情况下更新应用。但发现原作者的签名保存在GitLib上，所以无法拿到签名，也就无法打包出可以更新的应用（签名不同所以是两个应用）

3. 将白E的收藏、历史记录等导入导出，再在另一些版本的EhViewer中导入（如：[Ehviewer_CN_SXJ](https://github.com/xiaojieonly/Ehviewer_CN_SXJ)），这个在应用的**设置**->**高级**中可以操作，这里不在赘述。

## 迁移下载数据

对下载数据进行导出，因为白E存储数据的位置是`/sdcard/Android/data/io.github.nekoinverter.ehviewer/files/download`文件夹内，所以转移出来比较麻烦，这里使用adb工具进行导出。

### 1. 准备Linux环境

> 为什么使用Linux，而不是直接Windows系统？这是因为Windows系统对于路径长度有限制，在复制过程中一些文件夹的名字加上路径会非常的长，导致出错，而Linux的限制长度值比较大，可以避免这种情况。具体原因请[参阅](https://forum.xda-developers.com/t/q-adb-pull-fails-with-cannot-create.3157154/)

下载[VMware](https://www.vmware.com/go/getworkstation-win)虚拟机

下载[Ubuntu](https://releases.ubuntu.com/22.04.1/ubuntu-22.04.1-desktop-amd64.iso)镜像

具体安装方法不再赘述，具体[参考](https://zhuanlan.zhihu.com/p/141033713)

### 2. Ubuntu下安装adb

打开终端，执行

命令

`sudo apt-get install android-tools-adb`

测试一下是否正常

`adb version`

### 3. 共享文件夹

往VMware中增加虚拟机与主机共享的文件夹，增加后会挂载在`/mnt/hgfs/`目录下

### 4. 开始导出

执行命令

`sudo adb pull /sdcard/Android/data/io.github.nekoinverter.ehviewer/files/download /mnt/hgfs/你的共享目录名`

### 5. 最后

你可以执行adb的`push`命令将这些文件放回到你手机的特定位置

例如

`sudo adb push /mnt/hgfs/你的共享目录名/download /sdcard/EhViewer/`

建议使用[Ehviewer_CN_SXJ](https://github.com/xiaojieonly/Ehviewer_CN_SXJ)这一版本，因为这个版本的下载目录在外层`/sdcard/EhViewer`下，以后导出也不需要用到Linux环境

# Thanks

本项目受到了诸多开源项目的帮助

Here is the libraries

- [AOSP](http://source.android.com/)
- [android-advancedrecyclerview](https://github.com/h6ah4i/android-advancedrecyclerview)
- [Apache Commons Lang](https://commons.apache.org/proper/commons-lang/)
- [apng](http://apng.sourceforge.net/)
- [giflib](http://giflib.sourceforge.net)
- [greenDAO](https://github.com/greenrobot/greenDAO)
- [jsoup](https://github.com/jhy/jsoup)
- [libjpeg-turbo](http://libjpeg-turbo.virtualgl.org/)
- [libpng](http://www.libpng.org/pub/png/libpng.html)
- [okhttp](https://github.com/square/okhttp)
- [roaster](https://github.com/forge/roaster)
- [ShowcaseView](https://github.com/amlcurran/ShowcaseView)
- [Slabo](https://github.com/TiroTypeworks/Slabo)
- [TagSoup](http://home.ccil.org/~cowan/tagsoup/)


# License

    Copyright (C) 2014-2019 Hippo Seven

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

ic_launcher 图标为 Hippo Seven 所有，所有权利保留