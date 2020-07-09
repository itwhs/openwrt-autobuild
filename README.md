# Openwrt 路由器固件自动编译 [![OpenWrt](https://img.shields.io/badge/From-OpenWrt-blue.svg?style=for-the-badge&logo=appveyor)](https://github.com/openwrt/openwrt) 

>固件来源：
[![Lean](https://img.shields.io/badge/Lede-Lean-red.svg?style=flat&logo=appveyor)](https://github.com/coolsnowwolf/lede)
[![Lienol](https://img.shields.io/badge/Package-Lienol-blueviolet.svg?style=flat&logo=appveyor)](https://github.com/Lienol/openwrt-package)
[![CTCGFW](https://img.shields.io/badge/OpenWrt-CTCGFW-orange.svg?style=flat&logo=appveyor)](https://github.com/project-openwrt/openwrt)


## 简介 (基于Template)

- 通用 OpenWrt 定制项目
- `Build-Openwrt-Lean`是基于[![Lean](https://img.shields.io/badge/Lede-Lean-red.svg?style=flat&logo=appveyor)](https://github.com/coolsnowwolf/lede)编译
- 通过修改`script.sh`文件修改`feeds.conf.default`配置。默认添加`fw876/helloworld`
- 通过修改`script.sh`文件可以自定义默认IP，登陆密码等。按我的需要现在的默认IP为`192.168.50.11`,不需要更改的加`#`注释就可以。
- 自定义编译的方法可以搭配使用，自己需要的服务一般不会随意变化，就可以在 `make menuconfig` 选好（新手参考[OpenWrt MenuConfig设置和LuCI插件选项说明](https://mtom.ml/827.html)）后执行 `./scripts/diffconfig.sh > seed.config` 复制一下这个`seed.config`的文本内容到项目根目录的`.config`文件中，这样就不用每次都SSH连接到 Actions生成编译配置，真正一键编译。
- 另外如果，使用“files 大法”仓库最好设为私有，否则你的配置信息，如宽带账号等会公开在网上。
- 如果需要可以编写多个`workflows`文件对应`###.config`，开启多流程同时编译。
