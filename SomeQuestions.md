# Java

## Java的向上转型与向下转型

https://zhuanlan.zhihu.com/p/34026164



## 为什么Java可以通过类来创建interface

E.g

* Interface UserService
* class UserServiceImpl implements UserService
* UserService us = new UserServiceImpl()

https://juejin.im/post/5c0cc4975188252bf829e3dc



## Java运行时(Runtime)是什么意思？

https://blog.csdn.net/WangQYoho/article/details/52511573

https://my.oschina.net/u/4322392/blog/3406087

## Java编译生成的class文件有什么用？



## Java反射和Spring IOC的实现原理

### 反射

反射机制的优缺点：

* 优点：可以实现动态创建对象和编译，体现出很大的灵活性
* 缺点：对性能有影响。使用反射基本上是一种解释操作，我们可以告诉JVM，我们希望做什么并且让它满足我们的要求。这类操作总是慢于直接执行相同的操作。

### IOC

可以把IOC容器看作是一个工厂，**这个工厂里要生产的对象都在配置文件中给出定义，然后利用编程语言提供的反射机制，根据配置文件中给出的类名生成相应的对象**。<u>从实现来看，IOC是把以前在工厂方法里写死的对象生成代码，改变为由配置文件来定义，也就是把工厂和对象生成这两者独立分隔开来，目的就是提高灵活性和可维护性。</u>

IoC 不是一种技术，只是一种思想，一个重要的面向对象编程的法则，它能指导我们如何设计出松耦合、更优良的程序。传统应用程序都是由我们在类内部主动创建依赖对象，从而导致类与类之间高耦合，难于测试；有了IoC容器后，把创建和查找依赖对象的控制权交给了容器，由容器进行注入组合对象，所以对象与对象之间是 松散耦合，这样也方便测试，利于功能复用，更重要的是使得程序的整个体系结构变得非常灵活。

其实IoC对编程带来的最大改变不是从代码上，而是从思想上，发生了“主从换位”的变化。应用程序原本是老大，要获取什么资源都是主动出击，但是在IoC/DI思想中，应用程序就变成被动的了，被动的等待IoC容器来创建并注入它所需要的资源了。

IoC很好的体现了面向对象设计法则之一—— 好莱坞法则：“别找我们，我们找你”；即由IoC容器帮对象找相应的依赖对象并注入，而不是由对象主动去找。



### BeanFactory 和 ApplicationContext

* 源码解析IOC：https://www.dazhuanlan.com/2019/10/01/5d92ac96cd87b/

IoC容器主要系列： 一个是实现BeanFactory接口的简单容器系列，这系列之实现了容器的最基本功能； 另一个是ApplicationContext应用上下文，作为容器的高级形态而存在。

BeanDefinition来管理对象以及之间的相互依赖关系：

- 抽象了对Bean的定义，是让容器起作用的主要数据类型；
- 对象依赖关系的数据抽象

BeanDefinition像是容器里的水，BeanFactory是容器。



### IOC和DI

DI—Dependency Injection，即“依赖注入”：组件之间依赖关系由容器在运行期决定，形象的说，即由容器动态的将某个依赖关系注入到组件之中。依赖注入的目的并非为软件系统带来更多功能，而是为了提升组件重用的频率，并为系统搭建一个灵活、可扩展的平台。通过依赖注入机制，我们只需要通过简单的配置，而无需任何代码就可指定目标需要的资源，完成自身的业务逻辑，而不需要关心具体的资源来自何处，由谁实现。

### Reference

* https://blog.csdn.net/fuzhongmin05/article/details/61614873
* https://juejin.im/post/5d78a9f1e51d453b1f37ebb6
* https://blog.csdn.net/GoGleTech/article/details/79557416

## Java动态代理

### Reference

* https://juejin.im/post/5c1ca8df6fb9a049b347f55c



## Spring AOP在Spring框架中的体现

* @Transactional实现原理：https://blog.csdn.net/qq_20597727/article/details/84868035
* AOP实现原理：https://blog.csdn.net/qq_20597727/article/details/84800176



## Session和Cookie

https://blog.csdn.net/guoweimelon/article/details/50886092

### cookie

Cookie是由服务端生成的，发送给客户端（通常是浏览器）的。Cookie总是保存在客户端中，按在客户端中的存储位置，可分为内存Cookie和硬盘Cookie：

* 内存Cookie由浏览器维护，保存在内存中，浏览器关闭后就消失了，其存在时间是短暂的。
* 硬盘Cookie保存在硬盘里，有一个过期时间，除非用户手工清理或到了过期时间，硬盘Cookie不会被删除，其存在时间是长期的。所以，按存在时间，可分为非持久Cookie和持久Cookie。

### session

Session由服务端生成，保存在服务器的内存、缓存、硬盘或数据库中。

创建session：

当用户访问到一个服务器，如果服务器启用Session，服务器就要为该用户创建一个SESSION，在创建这个SESSION的时候，服务器首先检查这个用户发来的请求里是否包含了一个SESSION ID，如果包含了一个SESSION ID则说明之前该用户已经登陆过并为此用户创建过SESSION，那服务器就按照这个SESSION ID把这个SESSION在服务器的内存中查找出来（如果查找不到，就有可能为他新创建一个），如果客户端请求里不包含有SESSION ID，则为该客户端创建一个SESSION并生成一个与此SESSION相关的SESSION ID。这个SESSION ID是唯一的、不重复的、不容易找到规律的字符串，这个SESSION ID将被在本次响应中返回到客户端保存，而保存这个SESSION ID的正是COOKIE，这样在交互过程中浏览器可以自动的按照规则把这个标识发送给服务器。 

---------------------

使用session：

我们知道在IE中，我们可以在工具的Internet选项中把Cookie禁止，那么会不会出现把客户端的Cookie禁止了，那么SESSIONID就无法再用了呢？找了一些资料说明，可以有其他机制在COOKIE被禁止时仍然能够把Session id传递回服务器。

经常被使用的一种技术叫做URL重写，就是把Session id直接附加在URL路径的后面一种是作为URL路径的附加信息,表现形式为： 

http://…./xxx;jSession=ByOK3vjFD75aPnrF7C2HmdnV6QZcEbzWoWiBYEnLerjQ99zWpBng!-145788764； 

另一种是作为查询字符串附加在URL后面，表现形式为： 

http://…../xxx?jSession=ByOK3vjFD75aPnrF7C2HmdnV6QZcEbzWoWiBYEnLerjQ99zWpBng!-145788764 

还有一种就是表单隐藏字段。就是服务器会自动修改表单，添加一个隐藏字段，以便在表单提交时能够把Session id传递回服务器。

### Cookie和Session的区别

1. 存放位置：
   1. Cookie保存在客户端，
   2. Session保存在服务端
2. 存取方式不同'
   1. Cookie中只能保管ASCII字符串，假如需求存取Unicode字符或者二进制数据，需求先进行编码。Cookie中也不能直接存取Java对象。若要存储略微复杂的信息，运用Cookie是比拟艰难的。 
   2. Session中能够存取任何类型的数据，包括而不限于String、Integer、List、Map等。Session中也能够直接保管Java Bean乃至任何Java类，对象等，运用起来十分便当。能够把Session看做是一个Java容器类。 
3. 安全性（隐私策略）的不同 
   1. Cookie存储在浏览器中，对客户端是可见的，客户端的一些程序可能会窥探、复制以至修正Cookie中的内容
   2. Session存储在服务器上，对客户端是透明的，不存在敏感信息泄露的风险
   3. 假如选用Cookie，比较好的方法是，敏感的信息如账号密码等尽量不要写到Cookie中。最好是像Google、Baidu那样将Cookie信息加密，提交到服务器后再进行解密，保证Cookie中的信息只要本人能读得懂。而假如选择Session就省事多了，反正是放在服务器上，Session里任何隐私都能够有效的保护。 
4. 有效期上的不同
   1. 只需要设置Cookie的过期时间属性为一个很大很大的数字，Cookie就可以在浏览器保存很长时间
   2. Session依赖于名为JSESSIONID的Cookie，而Cookie JSESSIONID的过期时间默许为–1，只需关闭了浏览器（一次会话结束），该Session就会失效。
5. 对服务器造成的压力不同
   1. Session是保管在服务器端的，每个用户都会产生一个Session。假如并发访问的用户十分多，会产生十分多的Session，耗费大量的内存。而Cookie保管在客户端，不占用服务器资源。假如并发阅读的用户十分多，Cookie是很好的选择。
6. Cookie支持跨域名访问，例如将domain属性设置为“.baidu.com”，则以“.baidu.com”为后缀的一切域名均能够访问该Cookie。跨域名Cookie如今被普遍用在网络中。而Session则不会支持跨域名访问。Session仅在他所在的域名内有效。 



## Servlet > Spring MVC > Spring Boot的演变

### Servlet > Spring MVC

* https://juejin.im/post/5a9f3ddb5188255585071151

### Spring MVC执行流程

* https://cloud.tencent.com/developer/article/1526271
* [https://huzb.me/2019/03/22/Spring-MVC%E6%BA%90%E7%A0%81%E6%B5%85%E6%9E%90%E2%80%94%E2%80%94%E8%AF%B7%E6%B1%82%E5%A4%84%E7%90%86%E6%B5%81%E7%A8%8B/](https://huzb.me/2019/03/22/Spring-MVC源码浅析——请求处理流程/)

### Spring MVC > Spring Boot

* https://juejin.im/post/5aa22d1f51882555677e2492

# 加密与安全

## 数字证书原理

### 创建数字证书

我们手里有一个私钥和一个公钥

1. 先生成一个文件，文件内容（明文内容P)大概是这样的：
   公钥内容
   签发者ID----谁签发的证书
   Subject----也就是这个证书签发给谁。这里subject和签发者ID相同。
   有效期
   其他信息
2. Hash算法，对P进行hash计算，得到hash值H
3. 使用我们（签发机构）的私钥对H进行RSA加密，得到签名信息S。这个步骤称为签名，就是用私钥对某公开内容的hash值进行加密
4. 然后将P和S连城一个文件，这个文件就是所谓的数字证书。所以数字证书里，包括证书持有者的身份信息，证书信息，证书持有人的公钥，以及签名信息。

### 验证数字证书

现在假设某人得到了这个证书，如何确认这个证书属于谁的呢？

1. 用同样的hash算法对P进行hash计算，可以得到一个hash值H1

2. P里有公钥，签发者ID，Subject，有效期，及其他信息。我们用公钥解密S，得到了一个值H’。
   这个H‘，正常情况，或者说期望正常的话，应该就是制作数字证书的时候，用私钥对S加密的H。是否真如期望一样呢？比较一番就知道了。
   现在对比H’和H1是否相等，如果相等，那么就证明这个证书是有签发者签发给subject的证书，就是符合期望了，也就是正常情况。否则就说明：

   1. 内容P被篡改过，或者
   2. 证书不是由CA签发的。
      这个是对自签发证书的验证过程。需要说明的是，这种自签发证书的验证不常使用，但如何验证证书的原理类似。

   作者：三一斜狩
   链接：https://www.zhihu.com/question/24294477/answer/74783418

3. 

# 数据库

原理：[https://github.com/CyC2018/CS-Notes/blob/master/notes/%E6%95%B0%E6%8D%AE%E5%BA%93%E7%B3%BB%E7%BB%9F%E5%8E%9F%E7%90%86.md](https://github.com/CyC2018/CS-Notes/blob/master/notes/数据库系统原理.md)

## 意向锁的作用

* https://juejin.im/post/5b85124f5188253010326360



# HTTP

## Message (报文)和Entity(实体)

* https://stackoverflow.com/questions/2273837/which-one-is-the-message-and-which-one-the-entity-in-http-terminology

A message is the whole HTTP request or response. And the entity is the message’s body (if there is any) and its corresponding [entity header fields](http://www.w3.org/Protocols/rfc2616/rfc2616-sec7.html#sec7.1).
