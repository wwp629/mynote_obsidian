### 1.下载安装

软件名称：Mihomo

[https://clashparty.org/docs/handson](https://clashparty.org/docs/handson)

[https://github.com/mihomo-party-org/clash-party](https://github.com/mihomo-party-org/clash-party)

  

### 2.首次打开软件

安装完成后，该软件首次打开，必须右键管理员打开，否则无法打开，第一次管理员打开后续就正常鼠标双击打开。

### 3.配置

3.1软件设置

不用修改，默认即可

3.2订阅配置

Sub-Store中配置订阅地址（注意使用支持Clash的订阅地址）

![[image 15.png|image 15.png]]

3.3加载订阅

完成订阅配置后，（因为订阅配置可以配置多个订阅）还需要加载对应的订阅，才能生效

![[image 1 6.png|image 1 6.png]]

3.4编辑覆写

覆写规则仓库

[https://github.com/mihomo-party-org/override-hub](https://github.com/mihomo-party-org/override-hub)

打开“[ACL4SSR_Online_Full_WithIcon.yaml](https://raw.githubusercontent.com/mihomo-party-org/override-hub/main/yaml/ACL4SSR_Online_Full_WithIcon.yaml)”对应的网址，在覆写中设置覆写规则

![[image 2 6.png|image 2 6.png]]

进一步的，修改覆写规则，添加个人需要修改的规则，如下，该规则主要针对cursor屏蔽国内ip无法使用其https2的快速访问功能的设置，注意需要配合Proxifier将代理协议进行强制转化才行，参考“Proxifier配合mihomo，代理cursor”

![[image 3 5.png|image 3 5.png]]

```YAML
+rules:
  - DOMAIN-SUFFIX,api2.cursor.sh,OpenAi
  - DOMAIN-SUFFIX,api3.cursor.sh,OpenAi
  - DOMAIN-SUFFIX,repo42.cursor.sh,OpenAi
  - DOMAIN-SUFFIX,api4.cursor.sh,OpenAi
  - DOMAIN-SUFFIX,marketplace.cursorapi.com,OpenAi
  - DOMAIN-SUFFIX,cursor-cdn.com,OpenAi
  - DOMAIN-SUFFIX,downloads.cursor.com,OpenAi
  - DOMAIN-SUFFIX,anysphere-binaries.s3.us-east-1.amazonaws.com,OpenAi
  - DOMAIN-SUFFIX,release-assets.githubusercontent.com,OpenAi
  - DOMAIN-SUFFIX,github.com,OpenAi
```

另外一种，覆写修改方式，不通过链接导入，而是新建YAML规模代码，将“Mihomo覆写规则完整YAML代码”复制到新建的规则中即可，对于个人使用，每次更新了YAML规则后，复制规则代码到“Mihomo覆写规则完整YAML代码”进行备份，这样如果重装软件或者在其他电脑上使用，可以用这个备份文件快速设置。

![[image 4 3.png|image 4 3.png]]

3.5代理组设置

节点选择：手动

手动切换：Large 香港01（此处选择最常用、最稳定的节点）

自动选择：Large新加坡01（随便，此处不会使用，因为节点选择中使用的是“手动”）

其他节点的配置如图

![[image 5 3.png|image 5 3.png]]

![[image 6 3.png|image 6 3.png]]

![[image 7 3.png|image 7 3.png]]

这些节点配置，配合覆写规则，关乎对应的流量是走那个节点通道。如下图，是自己额外使用的cursor流量代理规则，规则中跟cursor相关的链接代理全部走“OpenAi”，而OpenAi节点选择的是“美国节点”，而美国节点选择的是“Large 美国01”，所以cursor代理最终走的都是美国节点，这种层层递进的规则配置，可以方便的一次配置好后，无需在使用过程中频繁的切换节点（传统的代理软件，一般只能选择一个节点，当需要走不同的流量时，就要手动切换节点，比较麻烦）

![[image 8 3.png|image 8 3.png]]

3.6订阅更新设置

设置订阅更新，这样订阅节点如果更新了，会自动更新。但是需要注意的是，机场

![[image 9 2.png|image 9 2.png]]

![[image 10 2.png|image 10 2.png]]

3.7设置外部资源更新

这是根据数据库，实时更新的一些常见规则，设置好自动更新后

![[image 11 2.png|image 11 2.png]]

### 4.使用

完成设置后，检查左侧面板“DNS覆写”、“嗅探覆写”是否开启。然后规则、系统代理开启，就可以开始使用。要关注网络流量走的是那个节点，点击“连接”进行查看（一般对于要进行个性化覆写规则的连接，也经常会用到查看连接的功能，先确认流量是否正确，然后到覆写规则中配置要走的节点）。

![[image 12 2.png|image 12 2.png]]