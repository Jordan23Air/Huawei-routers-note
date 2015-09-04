# OSPF配置与管理
OSPF（open shortest path protocol）是一个基于链路状态进行路有计算的动态路由协议。是一种IGP路由协议，OSPF只用于一个AS内部。OSPF是通过LSA（链路状态通告）报文进行路由信息交互，通过5种报文（Hello、DBD、LSR、LSU、LSAck）进行邻居和邻居关系的建立以及同一区域内部各路由器间的LSDB（链路状态数据库）信息的同步，最终形成同一的区域内拓扑数据库。
## OSPF基础
OSPF（open shortest path protocol，开放式最短路径有限）协议是IETF组织开发的一个基于链路状态的AS内部的IGP（内部网管协议）。
RIP因为存在收敛慢、路由环路、可扩展性差等问题逐渐被OSPF取代。IPv4协议使用OSPFv2（RFC2328），IPv6协议使用OSPFv3（RFC2740）版本。
## OSPF的几个个重要概念
一台运行OSPF协议路由器中的每个OSPF进程必须制定一个用于标识本地路由器的Router ID。Router ID是一个32bits无符号整数。**在一个AS中每个Router ID必须唯一，但同一路由器的不同进程中的Router ID可以相同。**

1. AS 自制系统（通常所说的Routing Domain），是由运行同一种路由协议并且被统一组织机构管理的一组路由器组成。**同一个AS中的所有路由器必须运行相同的路由协议，且必须彼此相互连接（中间不能被其他协议陆游域所间断），分配相同的AS号。**IS-IS、BGP等动态路由协议也可以配置AS，形成特定的路由域。

    **在OSPF网络中能够，只有在同一AS中的路由器才会相互交换链路状态信息；在同一个AS中，所有的OSPF路由器都维护一个相同AS结构描述（就是AS中各区域间的链接关系（的数据库。**该数据库中菜鸟房的是路由域中相应链路的状态信息，然后OSPF通过这个数据库计算出其OSPF路由表。
2. Area
Area区域是OSPF的一个重要特征，就是在一个AS内部uafen的多个不同位置，或者不同角色的一组路由器单元，**每个OSPF路由器只能在所属Area内部学习到完整的链路状态信息。**

![](12-1.png)



图12-1所示为Area与AS之间的关系示意图，即一个AS中可以包括多个区域，不同的协议路由域使用不同的AS。**但只有OSPF和IS-IS协议Routing domain AS可以划分多个区域。**不同Routing Domain要经过BGP协议进行连接。

  OSPF的Area辩解是设备接口，而不是链路。即一个网段（链路）只能整个属于同一个Area，**即路由器间直接链接的链路两端接口必须属于同一个Area。**

  在OSPF中，除了可以划分多个普通Area外，还可以配置多种特殊区域，如骨干区域（固定为Area0）、Stub（末梢）区域、Totally Stub（完全末梢）区域，NSSA（非除末梢）区域和Totally NSSA（完全非纯末梢）区域，

3. 路由器类型
  由于OSPF把一个AS划分成了多个区域，路由器在AS中的不同位置，可以划分为一下4类。
    1. 区域内路由器（Internal Routers，IR）：所有接口都在同一个OSPF区域内。
    2. 区域辩解路由器（Area Border Routers，ABR）：接口可以分别属于不同区域，但其中一个接口必须链接骨干区域。ABR用来链接骨干区域和非骨干区域，它与骨干区域之间既可以是物理连接，也可以是逻辑上的连接（虚连接）。
    3. 骨干路由器（Backbone Routers,BR）：至少有一个接口属于骨干区域，所有的ABR和位于骨干区域内部的设备都似乎骨干路由器。
    4. 自制系统辩解路由器i（AS boundary Routers，ASBR),与其他AS中的设备交换路由信息的设备为ASBR，**虽然ASBR通常是位于AS的编辑额，但也可以是IR，也可以同时是ABR。只要一台OSPF设备引入了外部路由（包括之直连路由、静态路由、RIP、IS-IS、BGP，或者其他OSPF进程路由等（的信息它就成了ASBR。
4. 路由类型
划分区域的目的就是想减少LSA的数量，贾绍路由器上依据
   1. 区域内（Intra Area）路由
   2. 区域间（Inter Area）路由
   3. 第一类外部（Type1 External）路由
   4. 第二类外部（Type2 External）路由

## OSPF网络的设计考虑




# BFD和NQA配置与管理
# IS-IS配置与管理
# BGP路由配置与管理
# 




