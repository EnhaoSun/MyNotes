@SpringBootApplication
* a meta-annotation that pulls in component scanning, autoconfiguration, and property support.
* it will fire up a servlet container and serve up our service.

@Entity
* a JPA annotation to make this object ready for storage in a JPA-based data store  

@Modifying & @Transactional
* 首先需要了解@Modifying和@Transactional的作用，@Modifying的主要作用是声明执行的SQL语句是更新（增删改）操作， @Transactional的主要作用是提供事务支持（提供例如隔离性等事务特性，JPA默认会依赖JDBC默认隔离级别）。
* 为什么@Modifying和@Transactional配合才能使用？
  * 默认情况下JPA的每个操作都是事务的，在默认情况下，JPA的事务会设置为只读，
  * 实质上@Modifying只是声明了这个操作是一个修改操作，但却没有修改这个方法的事务等级，因此这个方法依然不能进行修改操作。
  * 只有声明了@Transactional，本质上是声明了@Transactional(readOnly=false)，这样覆盖了默认的@Transactional配置便可以执行修改操作了。
  

@RestController
* indicates that the data returned by each method will be written straight into the response body instead of rendering a template.

