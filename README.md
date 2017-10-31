# Notes of the 图解TCP/IP

## 第1章 网络基础知识

- 计算机网络，根据其规模可分为以下两种：

    - WAN（Wide Area Network，广域网）
    - LAN（Local Area Network，局域网）

- 计算机与网络发展的7个阶段：
    
    年代 | 内容
    --- | ---
    20世纪50年代 | 批处理时代
    20世纪60年代 | 分时系统时代
    20世纪70年代 | 计算机通信时代
    20世纪80年代 | 计算机网络时代
    20世纪90年代 | 互联网普及时代
    2000年 | 以互联网为中心的时代
    2010年 | 无论何时何地一切皆TCP/IP的网络时代

- 互联网中常用的具有代表性的协议有IP、TCP、HTTP等。而LAN（局域网）中常用的协议有IPX/SPX等。“计算机网络体系结构”将这些网络协议进行了系统的归纳。

    网络体系结构 | 协议 | 主要用途
    --- | --- | ---
    TCP/IP | IP，ICMP，TCP，UDP，HTTP，TELNET，SNMP，SMTP... | 互联网、局域网
    IPX/SPX(NetWare) | IPX，SPX，NPC... | 个人电脑局域网
    AppleTalk | DDP，RTMP，AEP，ATP，ZIP... | 苹果公司现有产品的局域网
    DECnet | DPR，NSP，SCP... | 前DEC小型机
    OSI | FTAM，MOTIS，VT，CMIS/CMIP，CLNP，CONP... | -
    XNS(Xerox Network Services) | IDP，SPP, PEP... | 施乐公司网络
    
- 分组交换是指将大数据分割为一个个叫做包（Packet）的较小单位进行传输的方法。

- TCP/IP是由IETF所建议的、致力于推进其标准化作业的一种协议。

- 在OSI参考模型中，每个分层都接收由它下一层所提供的特定服务，并且负责为自己的上一层提供特定的服务。上下层之间进行交互时所遵循的约定叫做“接口”。同一层之间的交互所遵循的约定叫做“协议”。

- OSI参考模型将这样一个复杂的协议整理并分成了易于理解的7个分层：

    - 应用层
    - 表示层
    - 会话层
    - 传输层
    - 网络层
    - 数据链路层
    - 物理层
    
- OSI参考模型Tip：

    - OSI参考模型中定义了每一层的“作用”
    - 定义每一层“作用”的是“协议”
    - “协议”是约定，其具体内容为“规范”
    - 我们日常所使用的就是遵循各种协议具体“规范”的产品和通信手段
    
- OSI参考模型中各个分层的作用

    分层名称 | 功能 | 每层功能概览
    --- | --- | ---
    应用层 | 针对特定应用的协议 | 针对每个应用的协议，如：电子邮件协议，远程登录协议，文件传输协议
    表示层 | 设备固有数据格式和网络标准数据格式的转换 | 接收不同表现形式的信息，如文字流、图像、声音等
    会话层 | 通信管理。负责建立和断开通信连接（数据流动的裸机通路）。管理传输层以下的会话。 | 何时建立连接，何时断开连接以及保持多久的连接？
    传输层 | 管理两个节点之间的数据传输。负责可靠传输（确保数据被可靠地传送到目标地址）。 | 是否有数据丢失？
    网络层 | 地址管理与路由选择 | 经过哪个路由传递到目标地址？
    数据链路层 | 互连设备之间传送和识别数据帧 | 数据帧与比特流之间的转换
    物理层 | 以“0”、“1”代表电压的高低、灯光的闪灭。 | 比特流与电子信号之间的切换
    
- 传输方式的分类：
    
    网络与通信中可以根据其数据发送方法进行多种分类。分类方法也有很多。

    - 面向有连接型与面向无连接型
        
        1. 面向有连接型中，在发送数据之前，需要在收发主机之间连接一条通信线路。好比人们平常打电话。
        2. 面向无连接型则不要求建立和断开连接。发送端可于任何时候自由发送数据。反之，接收端也永远不知道自己会在何时从哪里收到数据。因此，在面向无连接的情况下，接收端需要时常确认是否收到了数据。好比人们去邮局寄包裹一样。
        
    - 电路交换与分组交换（分组交换又叫蓄积交换）
        
        目前，网络通信方式大致分为两种---电路交换和分组交换。电路交换的历史相对久远，主要用于过去的电话网。而分组交换技术则是一种较新的通信方式，从20世纪60年代后半叶菜开始逐渐被人们认可。TCP/IP，正是采用了分组交换技术。
        
    - 单播、广播、多播及任播
    
        网络通信中，也可以根据目标地址的个数及其后续的行为对通信进行分类。如广播、多播等就是这种分类的产物。
        
        1. 单播（Unicast）
            字面上，“Uni”表示“1”，“Cast”意为“投掷”。组合起来就是指1对1通信。早先的固定电话就是单播通信的一个典型例子。
            
        2. 广播（Broadcast）
            字面上具有“播放”之意。因此他指的是将消息从1台主机发送给与之相连的所有其他主机。广播通信的一个典型例子就是电视播放，他将电视信号一齐发送给非特定的多个接收对象。
            
        3. 多播（Multicast）
            多播与广播类似，也是讲消息发送给多个接受主机。不同之处在于多播要限定某一组主机作为接收端。多播通信最典型的例子就是电视会议，这是由多组人在不同的地方参加的一种远程会议。
            
        4. 任播（Anycast）
            任播是指在特定的多台主机中选出一台作为接收端的一种通信方式。虽然，这种方式与多播有相似之处，都是面向特定的一群主机，但是他的行为却与多播不同。任播通信从目标主机群中选择一台最符合网络条件的主机作为目标主机发送消息。任播在实际网络中的应用有DNS根域名解析服务器。
            
- 地址

    现实生活中的“地址”比较容易理解，然而在计算机通信中，这种地址的概念显得要复杂一些。因为在实际的网络通信中，每一层的协议所使用的地址都不尽相同。例如，TCP/IP通信中使用MAC地址、IP地址、端口号等信息作为地址标识。甚至在应用层中，可以将电子邮件地址作为网络通信的地址。
    
    - 地址的唯一性
    
    - 地址的层次性
    
    MAC地址和IP地址在标识一个通信主体时虽然都具有唯一性，但是他们当中只有IP地址具有层次性。
    
    MAC地址由设备的制造厂商针对每块网卡进行分别指定。虽然MAC地址中的制造商识别号、产品编号以及通用编号等信息在某种程度上也具有一定的层次性，但是对于寻找地址并没有起到任何作用，所以不能算作有层次的地址。正因如此，虽然MAC地址是真正负责最终通信的地址，但是在实际寻址过程中，IP地址却必不可少。
    
    那么IP地址又是怎样实现分层的呢？一方面，IP地址由网络号和主机号两部分组成。即使通信主体的IP地址不同，若主机号不同，网络号相同，说明他们处于同一个网段。通常，同出一个网段的主机也都属于同一个部门或集团组织。另一方面，网络号相同的主机在组织结构、提供商类型和地狱分布上都比较集中，也为IP寻址带来了极大的方便。这也是为什么说IP地址具有层次性的原因。
    
    网络传输中，每个节点会根据分组数据的地址信息，来判断该报文应该由哪个网卡发送出去。为此，各个地址会参考一个发出接口列表。在这一点上MAC寻址和IP寻址是一样的。只不过MAC寻址中所参考的这张表叫做地址转发表，而IP地址中所参考的叫做路由控制表。MAC地址转发表中所记录的是实际的MAC地址本身，而路由表中记录的IP地址则是集中了之后的网络号。
    
- 网络的构成要素

    设备 | 作用
    --- | ---
    网卡 | 使计算机连网的设备（Network Interface）
    中继器（Repeater）| 从物理层上延长网络的设备
    网桥（Beidge）/2层交换机 | 从数据链路层上延长网络的设备
    路由器（Router）/3层交换机 | 通过网络层转发分组数据的设备
    4-7层交换机 | 处理传输层以上各层网络传输的设备
    网关（Gateway）| 转换协议的设备
    
    

## 第2章 TCP/IP基础知识

- TCP/IP的具体含义
    
    具体来说，IP或ICMP、TCP或UDP、TELNET或FTP、以及HTTP等都属于TCP/IP的协议。他们与TCP或IP的关系紧密，是互联网必不可少的组成部分。TCP/IP一词泛指这些协议，因此，有时也称TCP/IP为网际协议组。

- 互联网基础知识

    - “互联网”指由ARPANET发展而来，互连全世界的计算机网络
    - Internet指网际网，The Internet指互联网
    - 互联网的协议就是TCP/IP，TCP/IP就是互联网的协议
    - 互联网就是众多异构的网络通过IX（Internet Exchange，网络交换中心）互连的一个巨型网络。
    
- TCP/IP协议分层模型
    
    分层名称 | 典例协议 | 应用层面
    --- | --- | ---
    应用层 | DNS，URI，HTML，HTTP，TLS/SSl，SMTP，POP，IMAP，MIME，TELNET，SSH，FTP，SNMP，MIB，SIP，RTP，LDAP | 应用程序
    传输层 | TCP，UDP，UDP-Lite，SCTP，DCCP | 操作系统
    互联网层 | ARP，IP，ICMP | 操作系统
    网卡层 | 略 | 设备驱动程序与网络接口
    物理层 | 略 | 设备驱动程序与网络接口

    - Tip：OSI参考模型注重“通信协议必要的功能”是什么，而TCP/IP则更强调“在计算机上实现协议应该开发哪种程序”。
    
    - 硬件（物理层）
        
        TCP/IP的最底层是负责数据传输的硬件，这种硬件就相当于以太网或电话线路等物理层的设备。
        
    - 网络接口层（数据链路层）
    
        网络接口层利用以太网中的数据链路层进行通信，因此属于接口层。
        
    - 互联网层（网络层）
    
        网络层使用IP协议，他相当于OSI模型中的第3层网络层。IP协议基于IP地址转发分包数据。
        
        1. IP  
            IP是跨越网络传送数据包，使整个互联网都能收到数据的协议。IP协议使数据能够发送到地球的另一端，这期间她使用IP地址作为主机的标识。  
            虽然IP也是分组交换的一种协议，但是它不具有重发机制。即使分组数据包未能到达对端主机也不会重发。因此，属于非可靠性传输协议。
            
        2. ICMP  
            IP数据包在发送途中一旦发生异常导致无法到达对端目标地址时，需要给发送端发送一个发生异常的通知。ICMP就是为这一功能而定制的。他有时也被用来诊断网络的健康状况。
        
        3. ARP  
            从分组数据包的IP地址中解析出物理地址（MAC地址）的一种协议。
            
    - 传输层
    
        1. TCP  
            TCP是一种面向有连接的传输层协议。它可以保证两端通信主机之间的通信可达。TCP能够正确处理在传输过程中丢包、传输顺序乱掉等异常情况。此外，TCP还能够有效利用带宽，缓解网络拥堵。
            
        2. UDP
            UDP有别于TCP，他是一种面向无连接的传输层协议。UDP不会关注对端是否真的收到了传送过去的数据，如果需要检查对端是否收到分组数据包，或者对端是否连接到网络，则需要在应用程序中实现。  
            UDP常用于分组数据较少或多播、广播通信以及视频通信等多媒体领域。
        
    - 应用层（会话层以上的分层）
        
        TCP/IP的分层中，将OSI参考模型中的会话层、表示层和应用层的功能都集中到了应用程序中实现。
        
        
        
## 第4章 IP协议

    IP作为整个TCP/IP中至关重要的协议，主要负责将数据包发送给最终的目标计算机。因此，IP能够让世界上任何两台计算机之间的进行通信。
    
- IP即网际协议

    1. TCP/IP的心脏是互联网层。这一层主要由IP（Internet Protocol）和ICMP（Internet Control Message Protocol）两个协议组成。
    
    2. IP相当于OSI参考模型中的第3层---网络层。
    
    3. IP的主要作用就是在复杂的网络环境中将数据包发送给最终的目标地址。
    
    4. 互联网中，将那些配有IP地址的设备叫做“==主机==”；既配有IP地址又具有路由控制能力的设备叫做“==路由器==”；而==节点==则是主机和路由器的统称。
    
    5. 数据链路层提供直连两个设备之间的通信功能，与之相比，作为网络层的IP则负责在没有直连的两个网络之间进行通信传输。
    
- IP基础知识

    IP大致分为三大作用模块，它们是IP寻址、路由以及IP分包与组包。
    
    - IP寻址  
       
        MAC地址是用来标识同一个链路中不同计算机的一种识别码。作为网络层的IP，也有这种地址信息。一般叫做IP地址。IP地址用于在“连接到网络中的所有主机中识别出进行通信的目标地址”。因此，在TCP/IP通信中所有主机或路由器必须设定自己的IP地址。
        
    - 路由  
       
        路由控制（Routing）是指将分组数据发送到最终目标地址的功能。
        
        - Hop  
            Hop译为中文叫“跳”。它是指网络中的一个区间。IP包正是在网络中一个跳间被转发。因此IP陆游也叫多跳路由。在每一个区间内决定者包在下一跳被转发的路径。  
            
            一跳（1 Hop）是指利用数据链路层以下分层的功能传输数据帧的一个区间。
            
        - 路由控制表  
            为了奖数据包发送给目标主机，所有主机都维护着一张路由控制表（Routing Table）。该表记录IP数据在下一步应该应该发给哪个路由器。IP包将根据这个路由表在数据链路上传输。
            
    - IP分包与组包
        
        - 数据链路的抽象化  
            IP是实现多个数据链路之间通信的协议。数据链路根据种类的不同各有特点。对这些不同数据链路的相异特性进行抽象画也是IP的重要作用之一。因此，对IP的上一层来说，不论底层数据链路使用以太网还是无线LAN亦或是PPP，都将被一视同仁。
            
            不同数据链路有个最大的区别，就是它们各自的最大传输单位（MTU：Maximum Transmission Unit）不同。就好像人们在邮寄包裹或行李时有各自的大小限制一样。  
            
            为了解决这个问题，IP进行分片处理（IP Fragmentation）。
            
        - IP属于面向无连接型  
            IP面向无连接。即在发包之前，不需要建立与对端目标地之间的连接。上层如果遇到需要发送给IP的数据，该数据会立即被压缩成IP包发送出去。  
            
            IP采用无连接的两点原因：一是为了==简化==，二是为了==提速==。  
            
- IP地址的基础知识

    在TCP/IP通信时，用IP地址识别主机和路由器。IP地址就像是TCP/IP通信的一块基石。
    
    - IP地址的定义  
        
        IP地址（IPv4地址）由32位正整数来表示。  
        标记方式：将32位的IP地址以每8位为一组，分成4组，每组以“.”隔开，再将每组数转换为十进制数。例如下图：
        
        - | 2^8 | 2^8 | 2^8 | 2^8
        --- | --- | --- | ---- | ---
        2进制 | 10101100 | 00010100 | 00000001 | 00000001
        2进制 | 10101100. | 00010100. | 00000001. | 00000001
        10进制 | 172. | 20. | 1. | 1

        ==Tip==：通常一块网卡（NIC）只设置一个IP地址，其实一块网卡可以配置多个IP地址。此外，一台路由器通常都会配置两个以上的网卡，因此可以设置两个以上的IP地址。
        
    - IP地址由网络和主机两部分标识组成
    
        IP地址由“网络标识（网络地址）”和“主机标识（主机地址）”两部分组成。即IP地址具有了==唯一性==。
        
    - IP地址的分类  
    
        IP地址分为四个级别，分别为A类、B类、C类、D类。它根据IP地址中从第1位到第4位的比特列对其网络标识和主机标识进行区分。如图：
        
        级别 | 特殊位 | 网络标识 | 十进制网标 | 主机标识 | 网段容纳上限
        --- | --- | --- | --- | --- | ---
        A类 | 首位为“0” | 第1位到第8位 | 0.0.0.0-127.0.0.0 | 后24位 | 16,777,214个个
        B类 | 前两位为“10” | 第1位到第16位 | 128.0.0.0-191.255.0.0 | 后16位 | 65,534个
        C类 | 前三位为“110” | 第1位到第24位 | 192.0.0.0-223.255.255.0 | 后8位 | 254个
        D类 | 前四位为“1110” | 第1位到第32位 | 224.0.0.0-239.255.255.255 | 无 | -
        
        ==Tip==：用比特位表示主机地址时，不可以全部为0或全部为1。因为全部为0只有在表示对应的网络地址或IP地址不可获知的情况下才使用。而全部为1的主机地址通常作为广播地址。
        
    - 广播地址  
    
        广播地址用于在同一个链路中相互连接的主机之间发送数据包。将IP地址中的主机地址部分全部设置为1，就成为了广播地址。
        
        广播分为本地广播和直接广播两种。
        
        - 在本地网络内的广播叫做本地广播。
        - 在不同网络之间的广播叫做直接广播。
        
    - IP多播  
    
        多播用于将包发送给特定组内的所有主机。由于其直接使用IP协议，因此也不存在可靠传输。
        
    - 子网掩码  
    
        解决了分类浪费，灵活指定网络标识长度。由一个叫做“子网掩码”的识别码通过子网网络地址细分出比A类、B类、C类更小粒度的网络。
        
        自从引入了子网以后，一个IP地址就有了两种识别码。一是IP地址本身，另一个是表示网络部的子网掩码。
        
        当然，子网掩码必须是IP地址的首位开始==连续==的“==1==”。
        
    - 全局地址与私有地址
    
        级别 | 私有地址范围
        --- | ---
        A类 | 10.0.0.0 ～ 10.255.255.255（10/8）
        B类 | 172.16.0.0 ～ 172.31.255.255（172.16/12）
        C类 | 192.168.0.0 ～ 192.168.255.255（192.168/16）
        
        包含在这个范围内的IP地址都属于私有IP，而在此之外的IP地址称为全局IP。
        
        ==Tip==：配有私有IP的地址主机连网时，则通过NAT进行通信。
        
- 路由控制

    在数据发送过程中需要类似于“指明路由器或主机”的信息，以便真正发往目标地址。保存这种信息的就是路由控制表（Routing Table）。实现IP通信的主机和路由器都必须持有一张这样的表。
    
    - 该路由控制表的形成方式有==两种==：  
        
        一种是管理员手动设置，另一种是路由器与其他路由器相互交换信息时自动刷新。前者也叫静态路由控制，而后者叫做动态路由控制。为了让动态路由及时刷新路由表，在网络上互连的路由器之间必须设置好路由协议，保证正常读取路由控制信息。
    
    - 路由控制表的聚合  
    
        优势：能缩小路由表的大小
        
- IP分割处理与再构成处理

    - 数据链路不同，MTU则相异
    
    - IP报文的分片与重组  
    
        ==Tip==：经过分片之后的IP数据报在被重组时候，只能由目标主机进行。路由器虽然做分片但不会进行重组。
        
    - 路径MTU发现
    
        分片机制也有它的不足：首先，路由器的处理负荷加重；其次，在分片处理中，一旦某个分片丢失，则会造成整个IP数据报作废。
        
        为了应对以上问题，产生了一种新技术“路径MTU发现”（Path MTU Discovery）。所谓路径MTU（Path MTU）是指发送端主机到接收端主机之间不需要分片时最大MTU的大小。即路径中存在的所有数据链路中最小的MTU。进行路径MTU发现，就可以避免在中途的路由器中进行分片处理，也可以在TCP中发送更大的包。现在，很多操作系统都已经实现了路径MTU发现的功能。
        
- IPv6

    