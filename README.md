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


| TOKEN             | 释义                                                            |
| :---------------- | :-------------------------------------------------------------- |
| -- EMAIL          | Github用户邮箱                                                  |
| -- RELEASE_TOKEN  | 个人 Settings/Developer settings/Personal access tokens新建获取 |
| -- TMP_LINK_TOKEN | TMP.link命令行上传文件-生成上传命令到剪贴板-token=xxxxxx        |
| -- SCKEY          | Server酱SCKEY                                                   |

## 功能

- 可以支持两种种编译模式
  1. 编译Lean源码(含Lienol Package)
  2. 编译CTCGFW源码(含Lean & Lienol & CTCGFW & Ntlf9t & Zxlhhyccc Package)
- 自动上传固件
- 自动发布固件
- 自动创建分支
- 自动上传到TMP.link
- 自动上传到奶牛快传

## 变量

| 变量名                                                  | 释义                                 |
| :------------------------------------------------------ | :----------------------------------- |
| -- REPO_URL: <https://github.com/coolsnowwolf/lede.git> | 定义源码                             |
| -- REPO_BRANCH: master                                  | 定义分支                             |
| -- FEEDS_CONF: feeds.conf.default                       | 自定义 feeds 配置文件                |
| -- CONFIG_FILE: *.config                                | 自定义编译配置                       |
| -- DIY_SH: script.sh                                    | 定义`feeds.conf.default`脚本文件     |
|                                                         | 定义自定义默认IP，登陆密码等脚本文件 |
| -- SSH_ACTION: false                                    | 是否打开 SSH                         |
| -- UPLOAD_BRANCH: true                                  | 是否创建分支来存放编译固件及Package  |
| -- BRANCH: Lean｜Snapshot                               | 分支名称                             |
| -- GITHUB_USER_NAME: LinuxUnion                         | 定义Github用户名                     |
| -- GITHUB_USER_EMAIL: ${{ secrets.EMAIL }}              | 定义Github用户邮箱                   |
| -- GITHUB: github.com/be-engineer/openwrt-autobuild.git | 定义上传分支                         |
| -- UPLOAD_FIRMWARE: true                                | 是否上传固件                         |
| -- UPLOAD_COWTRANSFER: false                            | 是否上传固件到奶牛快传               |
| -- UPLOAD_TMP_LINK: false                               | 上传到TMP.link                       |
| -- CREATE_RELEASE: true                                 | 是否创建发行版本 Release             |
| -- BUILD_USER: LinuxUnion                               | 定义编译者                           |
| -- SEND_WECHAT_MSG: false                               | 是否微信通知                         |
