# tongda_udp_2397_sqli

通达OA OfficeTask udp 2397 端口[SQL注入](https://mrxn.net/tag/SQL%E6%B3%A8%E5%85%A5)检测工具

tongda_udp_2397_[sqli](https://mrxn.net/tag/SQL%E6%B3%A8%E5%85%A5) 工具使用说明如下图所示

![](https://img.mrxn.net/539085aec47a4ad6930c1ca2a3b7f2fa.webp)

# 影响版本

影响目前最新版本 13.3.25.416

![](https://img.mrxn.net/4a0ff497b04e4c01a38d943b847bef28.webp)

# 漏洞简述

这个洞已经出来了一段时间了，相关详细分析可以看参考部分的文章，很详细。这里仅仅记录复现并开发工具过程中的部分要点，
工具仅供甲方或蓝方自查检测（获取管理员密码，但是大部分都解不开 -__- 默认md5(salt)加密），因此叫检测工具，而不是利用工具，当然也有利用方法：获取其他表中可登录的用户，获取他们的密码，总有一个可以解密，进入后台可操作的姿势就多了，那个利用工具就不能放出来了！基本上跟过漏洞的都已经写好了利用工具，公开的此工具仅供检测，证明漏洞危害即可！

总体流程就是向特定端口2397 发送特制UDP报文执行update语句，而其中的set 部分与 where 部分均可控，因此可利用[时间盲注](https://mrxn.net/tag/SQL%E6%B3%A8%E5%85%A5)来获取数据库内容（因为协议端口特殊，大部分[WAF](https://mrxn.net/tag/waf)都是没有拦截的）。

![](https://img.mrxn.net/5bbe5ce2560c4086acec980dd6538bf7.webp)

系统安装默认的管理员密码可解密！`$1$ov4.WF0.$a7ZXmHTHNuEmHcYI8ZCgu.` 解密为 `9595701`


# 参考

- https://mp.weixin.qq.com/s/SkUghnlVQNd6Z65Ubc-KwA
- https://mrxn.net/hacktools/tongda-OfficeTask-sqli-tools.html
