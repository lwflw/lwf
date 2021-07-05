 Spring
 简介一下Spring框架。

答：Spring框架是一个开源的容器性质的轻量级框架。主要有三大特点：容器、IOC（控制反转）、AOP（面向切面编程）。


2. Spring框架有哪些优点？谈谈你的看法。

答：Spring框架主要有三大优点：

(1) 容器。Spring框架是一个容器，能够管理项目中的所有对象。

(2) IOC（控制反转）。Spring将创建对象的方式反转了，从程序员自己创建反转给了程序。

(3) AOP（面向切面）。面向切面编程，简而言之，就是将纵向重复的代码横向抽取出来。Spring框架应用了面向切面的思想，主要体现在为容器中管理的对象生成动态代理对象。

 
3. 什么是IOC？

答：IOC：控制反转，指得是将对象的创建权反转给Spring。作用是实现了程序的解耦合。、

4. 什么是DI？

答：DI：依赖注入，需要有IOC环境，在Spring创建Bean对象时，动态的将依赖对象注入到Bean对象中去。依赖注入最大的好处就是解耦合。

5. 你对Spring框架中的BeanFactory接口和ApplicationContext接口有什么理解？二者有什么区别？

答：BeanFactory接口是Spring框架的顶层接口，是最原始的接口，通过new （BeanFactory的实现类）来启动Spring容器时，并不会创建Spring容器里面的对象，只有在每次通过getBean()获得对象时才会创建。

ApplicationContext接口是用来替代BeanFactory接口的，通过new （ApplicationContext接口的实现类）ClassPathXmlApplicationContext来启动Spring容器时，就会创建容器中配置的所有对象。


6. Spring中的工厂容器有哪两个，它们的区别是什么？

答：BeanFactory和ApplicationContext。

BeanFactory接口是Spring框架的顶层接口，是最原始的接口，ApplicationContext是对BeanFactory扩展，BeanFactory在第一次getBean时才会初始化Bean, ApplicationContext是会在加载配置文件时初始化Bean

spring MVC
测试准备工作：
1、搭建测试Web环境
@RunWith(UnitilsJUnit4TestClassRunner.class)
@SpringApplicationContext({
"classpath:*.xml","file:src/main/webapp/WEB-INF/spring-configuration/*.xml",
"file:src/main/webapp/WEB-INF/*.xml"
})
2、注入Controller 类
@Controller
BeanController controller;
3、编写测试数据
测试数据的文件名一定要与测试类的文件名相同，比如测试数据BeanControllerTest.xml ，测试类 BeanControllerTest。
4、注入测试数据
@Test
@DataSet
public void testBean(){}





<!-- 指定GetPersonList处理的代码，和注入实现业务的代码 -->
<bean name="/GetPersonList" class="cn.base.GetPersonListAction">
<property name="getPersonList" ref=" getPersonListServices"></property>
</bean>



mybatis知识点

1、 概念：Java当中的一个持久层框架。
2、 特点、优势：
（1）把java代码和SQL代码做了一个完全分离。
（2）良好支持复杂对象的映射（输入映射、输出映射）
（3）使用动态SQL，可以预防SQL注入。
3、 原理：
（1）创建mybatis-config.xml配置文件
（2）创建sqlSessionFactory
（3）编写数据库表对应的实体类
（4）创建mybatis的sql映射文件，在这个文件中，把实体类的属性和数据库表的列联系起来，并且可以编写sql语句
（5）从sqlSessionFactory的实例获取session
（6）session内部通过Executor执行器执行操作。Executor会用到mapped statement对象，这个对象是对数据库存储的封装，包括：sql语句、输入参数、输出结果类型
（7）关闭session
3、sql标签：用来封装sql语句或者sql片段


MyBatis的DAO开发方法：
1、 使用mapper代理方法：
（1） 编写mapper.java 的接口类
（2） 编写mapper.xml
2、 编写接口类，需要遵守一些规范，MyBatis可以自动生成接口类的DAO实现类。规范有：
（1） mapper.xml中namespace需要等于mapper接口类的地址
（2） mapper接口类的方法的名称等于mapper.xml中statement（对应sql语句）的id
（3） mapper接口类的输入参数类型等于mapper.xml中statement的parameterType指定的类型
（4） mapper接口类的返回参数类型等于mapper.xml中statement的resultType指定的类型
3、

MyBatis和Hibernate的本质区别：
1、 Hibernate不需要写sql，通过hql或者Hibernate直接生成sql。Mybatis需要写sql。
2、 Mybatis适合于需求经常改动的项目，因为它的sql由程序员生成，容易改动。Hibernate适合于需求改动较少的项目。

MyBatis和Ibatis的本质区别：
1、MyBatis简化了编码过程，不需要写DAO的实现类。直接写一个DAO的接口和一个配置文件。MyBatis自动生成DAO实现类。

嵌套查询 及 嵌套结果查询：
嵌套查询：使用2次查询，然后在MyBatis（内存）中进行拼装。可能引起N+1问题。
嵌套结果查询：使用1次查询，然后将结果进行拼装。
