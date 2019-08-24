# 《大型网站技术架构》读书笔记
 
>所谓 这个词我觉得用的好 所谓业务逻辑
 
>人月神话
 
>性能、可用性、伸缩性、扩展性、安全性几个网站核心架构要素
 
>真正能解决问题的技术一定是简单的。
 
>但事物发展到一定阶段，就会拥有自身的发展冲动，摆脱其初衷，向着使自己更强大的方向发展。
 
>另一方面却是中小网站十几年如一日地使用LAMP技术（Linux+Apache+MySQL+PHP）开发自己的网站，因为LAMP既便宜又简单，而且对付一个中小型网站绰绰有余。
 
>是业务成就了技术，是事业成就了人，而不是相反。
 
>技术是用来解决业务问题的，而业务的问题，也可以通过业务的手段去解决。
 
>在大型网站架构中也采用分层结构，将网站软件系统分为应用层、服务层、数据层
 
>高内聚低耦合
 
>切莫为了分布式而分布式。
 
>通过使用独立域名加快浏览器并发加载的速度
 
>网站高可用的主要手段是冗余，应用部署在多台服务器上同时提供访问，数据存储在多台服务器上互相备份，任何一台服务器宕机都不会影响应用的整体可用，也不会导致数据丢失。
 
>衡量网站安全架构的标准就是针对现存和潜在的各种攻击与窃密手段，是否有可靠的应对策略。
 
>性能测试是性能优化的前提和基础，也是性能优化结果的检查和度量标准
 
>主要的优化手段有使用缓存加速数据读取，使用集群提高吞吐能力，使用异步消息加快请求响应及实现削峰，使用代码优化手段改善程序性能。
 
>一方面，Cookie包含在每次请求和响应中，太大的Cookie会严重影响数据传输，因此哪些数据需要写入Cookie需要慎重考虑，尽量减少Cookie中传输的数据量。另一方面，对于某些静态资源的访问，如CSS、Script等，发送Cookie没有意义，可以考虑静态资源使用独立域名访问，避免请求静态资源时发送Cookie，减少Cookie传输的次数。
 
>对于某些静态资源的访问，如CSS、Script等，发送Cookie没有意义，可以考虑静态资源使用独立域名访问，避免请求静态资源时发送Cookie，减少Cookie传输的次数
 
>除了安全功能，代理服务器也可以通过配置缓存功能加速Web请求
 
>优化手段主要有缓存、集群、异步等
 
>网站性能优化第一定律：优先考虑使用缓存优化性能。
 
>缓存的本质是一个内存Hash表，网站应用中，数据缓存以一对Key、Value的形式存储在内存Hash表中
 
>任何可以晚点做的事情都应该晚点再做。
 
>目前许多NoSQL产品采用LSM树作为主要数据结构
 
>归根结底，技术是为业务服务的，技术选型和架构决策依赖业务规划乃至企业战略规划，离开业务发展的支撑和驱动，技术走不远，甚至还会迷路。
 
>可用性指标是网站架构设计的重要指标，对外是服务承诺，对内是考核指标。
 
>实现上述高可用架构的主要手段是数据和服务的冗余备份及失效转移，一旦某些服务器宕机，就将服务切换到其他可用的服务器上，如果磁盘损坏，则从备份的磁盘读取数据。
 
>所谓无状态的应用是指应用服务器不保存业务的上下文信息，而仅根据每次请求提交的数据进行相应的业务逻辑处理，多个服务实例（服务器）之间完全对等，请求提交到任意服务器，处理结果都是完全一样的。
 
>保证数据存储高可用的手段主要是数据备份和失效转移机制
 
>为了保证数据的高可用，网站通常会牺牲另一个也很重要的指标：数据一致性。
 
>数据热备可分为两种：异步热备方式和同步热备方式。
 
>失效转移操作由三部分组成：失效确认、访问转移、数据恢复。
 
 
>系统确认一台服务器是否宕机的手段有两种：心跳检测和应用程序访问失败报告
 
 
 
>其继任者提出了一个火车发布模型：将每个应用的发布过程看作一次火车旅程，火车定点运行，期间有若干站点，每一站都进行例行检查，不通过的项目下车，剩下的项目继续坐着火车旅行，直到火车到达终点（应用发布成功）。
 
 
>“不允许没有监控的系统上线”
 
 
>目前网站使用比较广泛的开源性能监控工具是Ganglia
 
>一般说来，网站的伸缩性设计可分成两类，一类是根据功能进行物理分离实现伸缩，一类是单一功能通过集群实现伸缩。前者是不同的服务器部署不同的服务，提供不同的功能；后者是集群内的多台服务器部署相同的服务，提供相同的功能。
 
 
>由于反向代理服务器转发请求在HTTP协议层面，因此也叫应用层负载均衡。其优点是和反向代理服务器功能集成在一起，部署简单。缺点是反向代理服务器是所有请求和响应的中转站，其性能可能会成为瓶颈。
 
 
>使用三角传输模式的链路层负载均衡是目前大型网站使用最广的一种负载均衡手段。在Linux平台上最好的链路层负载均衡开源产品是LVS（Linux Virtual Server）。
 
 
>会话黏滞
 
 
>二叉查找树
 
 
>计算机的任何问题都可以通过增加一个虚拟层来解决。
 
 
>糟糕的海量数据处理能力及僵硬的设计约束
 
 
>一般而言，NoSQL数据库产品都放弃了关系数据库的两大重要基础：以关系代数为基础的结构化查询语言（SQL）和事务一致性保证（ACID）。而强化其他一些大型网站更关注的特性：高可用性和可伸缩性。
 
 
>救世主定律：遇到问题，分析问题，最后总能解决问题。如果遇到问题就急匆匆地从外面挖一个高手，然后指望高手如探囊取物般轻松搞定，最后怕是只有彼此抱怨和伤害。许多问题只是看起来一样，具体问题总是要具体对待的，没有银弹，没有救世主。所以这个定律准确地说应该是“没有救世主定律”。
 
>降低软件系统耦合性
 
 
>笔者认为，软件架构师最大的价值不在于掌握多少先进的技术，而在于具有将一个大系统切分成N个低耦合的子模块的能力，这些子模块包含横向的业务模块，也包含纵向的基础技术模块。这种能力一部分源自专业的技术和经验，还有一部分源自架构师对业务场景的理解、对人性的把握、甚至对世界的认知。
 
>信息加密技术可分为三类：单项散列加密、对称加密和非对称加密。
 
 
>常用的单向散列算法有MD5、SHA等。单向散列算法还有一个特点就是输入的任何微小变化都会导致输出的完全不同，这个特性有时也会被用来生成信息摘要、计算具有高离散程度的随机数等用途。
 
 
>另一种方案是将加解密算法放在应用系统中，密钥则放在独立服务器中，为了提高密钥的安全性，实际存储时，密钥被切分成数片，加密后分别保存在不同存储介质中，兼顾密钥安全性的同时又改善了性能，
 
>笨重。淘宝后来甚至用更轻量级的Jetty替代了JBoss，对淘宝而言，应用服务器只需要一个Servlet容器，越简单越快越好。在合适的场景下使用合适的产品，而不是最好的产品，所谓小脚穿大鞋，不但跑不快，还可能会摔跤。
 
>为了避免用户直接访问下单页面URL，需要将该URL动态化，即使秒杀系统的开发者也无法在秒杀开始前访问下单页面的URL。办法是在下单页面URL加入由服务器端生成的随机数作为参数，在秒杀开始的时候才能得到。
 
>首页不应该访问数据库，首页需要的数据可以从缓存服务器或者搜索引擎服务器获取。●首页最好是静态的。
 
 
>一个缺乏经验的工程师关闭了缓存服务器集群中全部的十几台Memcached服务器，导致了网站全部瘫痪的重大事故。
 
 
>存储的使用需要根据不同文件类型和用途进行管理，图片都是小文件，应该使用专用的存储服务器，不能和大文件共用存储。批处理用的大文件可以使用其他类型的分布式文件系统。
 
>寻找一个值得共同奋斗的目标，营造一个让大家都能最大限度发挥自我价值的工作氛围。
 
 
>没有懒惰的员工，只有没被激发出来的激情。所有强迫员工加班的管理者都应该为自己的无能而羞愧。
 
 
>大多数人，包括我们自己，都比自己以为的更优秀，有些优秀需要在合适的环境中才会被激发出来，比如做一些有挑战的事，和更优秀的人合作，抑或拥有了超越自我的勇气
 
 
>发掘人的优秀远比发掘优秀的人更有意义。
 
 
>架构师要和项目组全体成员共同描绘一个蓝图，这个蓝图是整个团队能够认同的，是团队共同奋斗的目标。
>- 蓝图应该是表述清楚的
>- 蓝图应该是形象的
>- 蓝图应该是简单的
 
 
>不要企图在项目中证明自己是正确的，一定要记住，你是来做软件的，不是来当老大的。所以不要企图去证明自己了不起，永远也别干这种浪费时间、伤害感情的事。
 
 
>有个小故事：猎人进山里打猎，反而被一头黑熊抓住了，黑熊说“如果你给我XX我就放你走”，猎人无奈只好给黑熊XX。回去后苦练打猎本领，再次进山，结果又被黑熊抓住，再次要求给了XX。第三次他又来了，黑熊看到他就乐了“你是来打猎的还是来给我XX的？”
 
>鱼是最后一个看见水的
 
 
>所谓问题，就是体验—期望，当体验不能满足期望，就会觉得出了问题。消除问题有两种手段：改善体验或者降低期望。降低期望只是回避了问题，而如果直面期望和体验之间的差距，就会发现问题所在，找到突破点。
点评
 
>最后一段我自己对此书浅薄的平价：
>可以说是本不错的书，从中学习到以前根本没了解过的和想要了解的知识