# proj234-linux-upgrade-system

# Linux 升级系统

### 项目描述


在工业控制、机器人控制领域中越来越多使用Linux嵌入式操作系统，但嵌入式linux系统在终端设备上部署之后，在更新和升级系统镜像的时候， 还需要重新物理部署，不能确保最佳的操作体验和系统正常的运行时间。 为了改善linux的升级体验， 可以参考ostree, 改造linux的升级系统, 以能够执行安全的远程OTA升级,执行安全的离线升级。



### 所属赛道

2023全国大学生操作系统比赛的“OS功能设计”赛道

### 参赛要求

- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生/研究生
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
- 请遵循“2023全国大学生操作系统比赛”的章程和技术方案要求

### 项目导师

- gitee @r2018, @tao12345
- email: liyulei@kylinos.cn, taoshusong@kylinos.cn

### 难度

中

### 特征

- 需要了解ota升级的概念及原理
- 需要了解grub/uboot的原理及启动过程
- 需要了解linux内核启动及initrd启动过程
- 需要了解linux的rootfs结构


### 参考文档

https://ostreedev.github.io/ostree/introduction/
https://www.kernel.org/doc/html/latest/filesystems/ramfs-rootfs-initramfs.html
https://uapi-group.org/specifications/specs/boot_loader_specification/


### License

GPL-3.0

### 预期目标

**注意：下面的内容是建议内容，不要求必须全部完成。选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标**

**第一题：升级模块基础框架实现**
1.  使用ostree 创建repo仓库
2.	脚本能将编译出来的rootfs和内核等发布到ostree repo仓库
3.	linux系统能够使用受ostree管理的rootfs启动正常(grub方式)


**第二题：升级模块更新功能实现**

以题目一为基础，工具需要追加下列功能：

1. linux系统正常启动后, 可以获取远程repo仓库最新版本,执行ostree升级
2. linux系统升级失败时,能回退到升级前的系统中
3.	三次启动失败, 能够自动回退到升级前版本
4.  支持A/B分区,启动失败时可以从B分区启动

**（可选）第三题：升级模块扩展功能实现**

以题目二为基础，工具需要追加下列功能：
1.	ostree客户端从ostree repo仓库获取最新版本时, 要有安全认证,要能够支持并发测试
2.	只有持有指定密钥才能够向ostree repo仓库提交系统
3.  ostree repoo仓库可以接管多个操作系统
4.  ostree repoo仓库提供webUI进行管理
5.	支持uboot方式启动的linux系统
