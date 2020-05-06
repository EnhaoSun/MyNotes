# 思考问题

## 为什么Java可以通过类来创建interface

E.g

* Interface UserService

* class UserServiceImpl implements UserService
* UserService us = new UserServiceImpl()



## Java运行时(Runtime)是什么意思？



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





## Session和Cookie



## Servlet > Spring MVC > Spring Boot的演变

### Servlet > Spring MVC

* https://juejin.im/post/5a9f3ddb5188255585071151



### Spring MVC > Spring Boot

* https://juejin.im/post/5aa22d1f51882555677e2492

