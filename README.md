***如果你有任何疑问，或提交bug: 请发送[Issues](issues/)，或到Q群[`580659670`](https://qm.qq.com/q/gya17AyEyQ)寻求帮助***
# AntiAttackRL插 件 介 绍
![LOGO](https://github.com/AntiAttackMC/AATRL_Public/assets/141195321/a132cebe-2a95-4344-868a-955a4c81a78b)
**AntiAttackRL**是一款免费、可靠、更新频繁、多平台的压测防御插件，可以有效地防御绝大多数的压测攻击，同时也是唯一一款能够**同时**支持几乎所有服务端的反压测插件<br>

**BukkitAPI 系列**<br>
_Spigot_ 及其分支（如 _Paper_、_Purpur_ 等）<br>
_Hybrid_ 混合服务端<br>
新式多线程服务端（如 _Folia_ 、 _ShreddedPaper_）<br>
**Proxy 系列**<br>
_BungeeCord_ 、_Velocity_、_Waterfall_ <br>
**Sponge 系列**<br>
_Sponge7_ 、_Sponge8_ <br>

## 特性
* 防御 MOTD _(集群)_ 压测
* 防御 Ping _(集群)_ 压测
* 防御 假人 _(集群)_ 压测
* 防御 Tab 包高频攻击
* 防御 Move 包高频攻击
* 防御连点器发包崩溃漏洞
* 防御踢人漏洞压测攻击
* 防御频繁握手多连接攻击
* 防御洪水 Book 包攻击
* 防御死亡 Motd / Ping 发包攻击
* 不会阻隔正常玩家进入服务器
* 插件可自动更新 *
* 可高度自定义的配置文件
* 可以自定义发包规则限制
  
## 优势
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

## 首次安装教程（必看）
### 实现BukkitAPI的服务端 _(包括Spigot及其分支、各类Hybrid混合服务端、Folia、ShreddedPaper等)_ 安装方法
1. 确保装有前置: `ProtocoLib`
2. 下载好插件: `AntiAttackRL-[版本号].jar`
3. 将插件置入`plugins`文件夹中
4. 重启时，服务器可能会进行初始化，玩家数据越多，时间越长
5. 若效果不好，请查阅下方的配置文件讲解对配置文件进行修改
### Proxy代理端 _(如BungeeCord、Velocity)_ 及其分支 _(如WaterFall等)_ 安装方法
#### 若你的服务器未处于被攻击时:
1. 下载插件: `AntiAttackRL-[版本号].jar`
2. 将其置入Proxy端中的`plugins`文件夹中
3. 重启服务端即可生效
4. 若效果不好，请查阅下方的配置文件讲解对配置文件进行修改

#### 若你的Proxy服务端正处于被攻击时:
1. 下载插件: `AntiAttackRL-[版本号].jar`
2. 先将其置入你的任一**非登录服**中的`plugins`文件夹中
3. 重启这个子服，等待初始化结束
4. 将位于该子服`plugins`中的`AntiAttackRL.jar`和`AntiAttackRL文件夹`一起挪到**Proxy端**的`plugins`里<br>
   4.1 若**Proxy端**为`Velocity`，则移动过去之后需将文件夹名改为`anti_attack_reload`
6. 重启服务端即可生效
7. 若效果不好，请查阅下方的配置文件讲解对配置文件进行修改
### Sponge安装方法
1. 下载插件: `AntiAttackRL-[版本号].jar`
2. 将其置入服务端的`mods`文件夹中
3. 重启服务端，重启时插件可能会进行初始化，玩家数据越多,时间越长
4. 若效果不好，请查阅下方的配置文件讲解对配置文件进行修改
## 配置文件
本插件在任何**上方明文支持的服务端**运行时<br>
其配置文件格式相同，均为Yaml。在同版本插件下各个选项也完全相同，**但文件位置不同**。<br>
配置文件位置:<br>
- BukkitAPI _(Spigot、Folia、Mohist、Paper等`[按字母顺序排序]`)_: `plugins/AntiAttackRL/config.yml` <br>
- BungeeCord: `plugins/AntiAttackRL/config.yml` <br>
- Sponge7: `config/anti_attack_reload/config.yml` <br>
- Sponge8: `config/AntiAttackRL/config.yml` <br>
- Velocity: `plugins/anti_attack_reload/config.yml` <br>
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
AntiPacketFloodAttack: #防止发包洪水攻击
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
HandShakeLimiter:     #握手次数限制
  PerIPSecondLimit: 3
  enable: true
LoggerFilter:       #防止日志刷屏-将会删除
  enable: true
  exceptions:
  - io.netty.handler.codec.DecoderException
  - io.netty.handler.codec.CorruptedFrameException
RestrictMode:   #反压测模式（戒备模式）
  Timer:             #阈值，超出将会触发反压测
    CountLimit: 1    #计数限制
    CountPeriod: 5    #计数周期
    DenyMessage: §c服务器遭到集群压测,请稍等再登录!§b[RMTR]
  enable: true
ServerInLimitTime:   #大厅踢出
  KickMessage: §c你在大厅服务器里面待太久了，请重新进入服务器
  LobbyServers:     #大厅服务器名称
  - lobby1    
  - lobby2
  StaySeconds: 30   #踢出时间（单位：秒）
  enable: true
Versioning: 425    #插件版本号（请勿修改）
```
## 指令
**/aat** 主命令
- help 查询插件帮助
- reload 重载插件
- rm 戒备模式手动操作
  * add <玩家名字> 填入记录单
  * remove <玩家名字> 移出记录单
  * start 立即开启戒备模式
  * stop 立即关闭戒备模式
- packetTrack (*/玩家) 包追踪所有/限定 _(仅Bukkit/Proxy支持   关闭直接输入/aat packetTrack)_ 

权限只有一个：`AntiAttack.admin`
## 踢出后缀
> [ACSA] 发包异常，如正常情况下被踢出请检查发包限制的设置 <br>
> [AFJ] 登陆频繁，如果误报请尝试调低防止快速加入的阈值<br>
> [AKA] 有同名玩家在线，通常是网络不佳或TPS过低导致的误报<br>
> [APFA] 发包速度太快，通常是R键整理等mod导致<br>
> [RMTR] 服务器正在受到集群压测，误报请检查反压测模式下阈值<br>

## 自定义包规则限制
> [!tip]
> 这部分内容并不是你一定需要理解的，而且也有一定难度。
1. 输入/aat packetTrack (*/玩家) 启动包监听模式
2. 此时你就可以开着 作弊端 | 修改器 | 攻击软件 进入服务器
   此时后台会不断输出包类型，共有以下几种:
   ![QQ图片20240721074833](https://github.com/user-attachments/assets/5ecf013f-a3fd-441c-9802-66cefed64cdd)
   ![QQ图片20240721075845](https://github.com/user-attachments/assets/bfd4b652-0caa-4837-84ca-39d06bf5dcf0)
4. 未完待续

# Download & Issues
请到 [Releases](releases/) 处下载最新版本
<br>
> [!WARNING]
> 如果在更新检测时遇到了类似`javax.net.ssl.SSLHandshakeException`的错误，是你网络不好连不上GitHub <br>
> **不要给我开issue或反馈，一概关闭/拒收！**
