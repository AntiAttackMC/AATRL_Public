**若果你有任何疑问或提交bug，请发送Issues或到Q群580659670寻求帮助**
# AntiAttackRL插件介绍
![MineBBS -QQ图片20240223073235](https://github.com/AntiAttackMC/AATRL_Public/assets/141195321/a132cebe-2a95-4344-868a-955a4c81a78b)
**AntiAttackRL**是一款免费、可靠、更新频繁、多平台的压测防御插件，可以有效地防御绝大多数的压测攻击，并且服务器被压测时玩家依然能够正常进服，同时也是唯一一款支持 Sponge 和 Folia 的反压测插件。
## Dev-V425更新内容
以下更新标识含义:
+:新增
-:移除
X:Bug修复
*:重要修改
~:代码优化/变动
|+|支持了ShreddedPaper服务端
|X|修复了控制台染色功能
|~|更改了前置插件为PacketEvents
### 特性
* 防御MOTD 压测 / MOTD 集群压测
* 防御Ping 压测 / Ping 集群压测
* 防御假人压测 / 集群假人压测
* 防御Tab 包高频攻击
* 防御Move 包高频攻击
* 防御连点器发包崩溃漏洞
* 防御踢人漏洞压测攻击
* 防御频繁握手多连接攻击
* 防御洪水 Book 包攻击
* 防御死亡 Motd / Ping 发包攻击
* 不会阻隔正常玩家进入服务器
* 插件可自动更新 *
* 可高度自定义的配置文件
* 可以自定义发包规则限制
### 优势
|AntiAttack3 |	AntiAttackRL	|其他同类防御插件|
| -----------|----------------|-----------------|
|老牌，早在集群压测发迹之前便已发布更新，经验丰富。但正因如此，代码累赘|	AAT 重制版，过往的经验使得 AATRL 在抵抗压测的熟练度上更上一层楼	| 很多时候都是第一次写反压测插件，对压测不熟悉，效果不好
戒备模式有很大问题，刚开服的几秒内压测会大量进入，被 EMP (新型压测软件)针对，难以抵抗袭击 |	全新的戒备模式算法,全新的代码,全新的机制，针对集群压测和各种新型攻击手段，具有卓越的防御效果	| 部分插件是上古时期发布的，它们对集群压测没有太大的抵抗力。其余插件对压测攻击具有防御效果，但对很多新型压测攻击几乎没有免疫力。
成群的 Bug ，不人性化的配置文件，公告信息，误报率在配置不正确下惊人，默认配置经常导致各种问题 |	默认配置便可以使用，误报率极低，近无 Bug ，作者即刻在线反馈修复	| 可能有几个月甚至几年没有进行过大更新
### 相对于老版 AntiAttack3 的改动
1. 完全重写，没有半点代码来自于 AntiAttack3 ，也就没有修改一说了，不过为了使得大家容易理解，仍然对此进行解释。
2. 戒备模式的全新算法！杜绝了刚开服成群玩家进不去或者成群压测进得去，解决了压测持续时间长便可以逐步透过戒备模式的墙的能力，支持开服便初始化戒备模式列表,不再需要提前记录和结算。
3. 去掉了大部分逗比的耍小聪明的检测，那些检测对上古有效，但对于新的压测几乎没有什么抵抗力，还会导致误报率奇高。
4. 比原来的算法更加高效，相较于 AAT3 来回补丁来回更新导致的代码一坨，全新写的代码易读，简洁，效果更好，优化更棒。
5. 修复了大部分的 Bug ，包括尽管假人进不来仍然在刷屏的问题，同时修复了几个上古时代就存在的 Bug 。
6. 更强的自定义，几乎所有玩家提示信息都可以自定义了，插件前缀也可以自定义了，所有数值都可以手动调整
7. 针对和高效的更新，几乎可以抵抗最新的压测，并配有一劳永逸的自动更新系统*。
### 首次安装教程（必看）
#### Bukkit / Spigot纯净服安装方法
1. 确保装有前置: Protocolib
2. 下载好插件: AntiAttackRL-[版本号].jar
3. 将插件置入plugins文件夹中
4. 重启时，服务器可能会进行初始化，玩家数据越多，时间越长
5. 若效果不好，请查阅下方的配置文件讲解对配置文件进行修改
#### BungeeCord蹦极服安装方法
**若你的服务器未处于被攻击时:**
1. 下载插件: AntiAttackRL-[版本号].jar
2. 将其置入BC中的plugins文件夹中
3. 重启BC即可生效
4. 若效果不好，请查阅下方的配置文件讲解对配置文件进行修改
**若你的服务器正处于被攻击时:**
1. 下载插件: AntiAttackRL-[版本号].jar
2. 先将其置入你的登录服中的plugins文件夹中
3. 重启你的登录服，等待初始化结束
4. 将位于登录服plugins中的AntiAttackRLjar和AntiAttack文件夹一起挪到BC的plugins里5.重启BC即呵生效
6. 若效果不好，请查阅下方的配置文件讲解对配置文件进行修改
#### Sponge纯净/模组服安装方法
1. 下载插件: AntiAttackRL-[版本号].jar
2. 将其置入服务端的mods或mods\1.12.2或mods\plugins文件夹中
3. 重启服务端，重启时插件可能会进行初始化，玩家数据越多,时间越长
4. 若效果不好，请查阅下方的配置文件讲解对配置文件进行修改
### 配置文件
本插件在任何服务端(Bukkit/Spigot/Paper/KCauldron/CarServer/Mohist/Bungee/Sponge)下运行时，
其配置文件格式均相同，格式为Yaml。在同版本插件下各个选项也完全相同，文件位置可能不同。
配置文件位置:（老版本为AntiAttackRL/AntiAttack文件夹）
Bukkit/Spigot: plugins/anti_attack_reloadL/config.yml
BungeeCord: plugins/anti_attack_reload/config.yml
Sponge: config/anti_attack_reload/config.yml
```yaml
AntiAttack:
  AutoUpdate: false  #自动更新
  Broadcast:
    enable: true    #聊天栏提示
    period: 10       #间隔
  CheckUpdate: true #检查更新
  PluginPrefix: §b§l[AntiAttackRL]   #插件提示前缀
AntiCreativeSlotAttack:   #防止非法发包
  KickMessage: §c非法发包!怀疑你在攻击服务器,请重新登录§b[ACSA]
  enable: true
AntiFastJoin: #防止快速加入
  DenyMessage: §c你加入过于频繁了!请稍等几秒!§b[AFJ]
  Interval: 4000    #检测间隔
  enable: true
AntiKickAttack: #防止把玩家顶掉线
  DenyMessage: §c有一个同名玩家已经在线了!§b[AKA]
  enable: true
AntiMOTDAttack: #防MOTD压测
  PerIP5sLimit: 10     #同一IP5秒最多请求次数
  Total5sLimit: 100      #全服5秒最多请求次数
  enable: true
AntiPacketFloodAttack: #自定义包规则限制
  KickMessage: §c%key_packet%发包量过多,已超出上限踢出值!§b[APFA]
  PacketLimit:
    PluginMessage:MC[|]BEdit:\S*:      #包名
      kick: 1                               
      period: 2000
      share: true
    PluginMessage:MC[|]BSign:\S*:
      kick: 1
      period: 2000
      share: true
    PluginMessage:\S*: ACCEPT
    '[\s\S]*':
      cancel: 25
      period: 500
      share: false
  enable: true
AntiPingAttack:   #ping攻击防御
  PerIPInterval: 500   #阈值
  TotalInterval: 50
  enable: true
AntiTabCompleteAttack:    #防止tab攻击
  PerIPInterval: 1000     #阈值
  TotalInterval: 100
  enable: true
Debug: false     #Debug模式
HandShakeLimiter:     #握手
  PerIPSecondLimit: 3
  enable: true
LoggerFilter:       #防止后台刷屏-将会删除
  enable: true
  exceptions:
  - io.netty.handler.codec.DecoderException
  - io.netty.handler.codec.CorruptedFrameException
RestrictMode:   #反压测模式
  Timer:
    CountLimit: 1    #计数限制
    CountPeriod: 5    #计数周期
    DenyMessage: §c服务器遭到集群压测,请稍等再登录!§b[RMTR]
  enable: true
ServerInLimitTime:   #大厅踢出
  KickMessage: §c你在大厅服务器里面待太久了，请重新进入服务器
  LobbyServers:     #大厅服务器名称
  - lobby1
  - lobby2
  StaySeconds: 30   #踢出时间
  enable: true
Versioning: 425    #插件版本号
```
### 指令
**/aat** 主指令
help 查询插件帮助
reload 重载插件
rm 戒备模式手动操作
* add <玩家名字> 填入记录单
* remove <玩家名字> 移出记录单
* start 立即开启戒备模式
* stop 立即关闭戒备模式
packetTrack (*/玩家) 包追踪所有/限定

权限只有一个：AntiAttack.admin
# Download & Issues
