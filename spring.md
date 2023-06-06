注入的几种方式
- set注入
- 构造器注入
- 注解的注入

@Autowired和@Resource
- @Autowired使用byType注入，如果@Resource使用name属性，则使用byName的自动注入策略，而使用type属性时则使用byType自动注入策略

springboot自动装配
  - 在@springbootApplication注解中有@enableAutoconfiguration负责自动装配
  - 是在meta-info/spring.configuration中存储了配置，需要在pom中使用相关starter注解即可使相关自动装配生效
  
事务
- @Transactional开启事务
- 分为编程式事务和声明式事务
- 编程式事务指硬编码的方式在业务中使用事务
- 声明式事务建立在aop之上的，本质是对方法前后进行拦截

beanFactory
- beanFactory是spring中比较原始的factory
- 负责管理和产生bean的一个工厂，所有bean都是由beanfactory来进行管理，是ioc容器的核心接口，职责包括实例化、定位、配置应用程序中的对象以及建立对象间的依赖
- 原始的beanFactory无法支持很多插件比如aop，web
- beanFactory在bean调用时进行bean的实例化，懒加载模式
- applcationContext由beanFactory派生而来，拥有beanFactory所有功能，比beanFactory更优先
- applcationContext在容器启动时实例化

spring bean的生命周期
- 实例化
- 属性赋值
- 初始化（Aware接口的依赖注入，BeanPostProcessor在初始化前后的处理，以及初始化操作）
- 销毁（通过disposableBean和destory——method销毁）

spring启动流程
- spring容器初始化
  - 实例化beanFactory，实例化注解配置读取器，实例化路径扫描器 
- 将springConfig注册进容器当中
- refresh()容器的刷新
- beanFactory预处理
- beanFactory后置处理
- 。。。

springboot启动流程

详细https://juejin.cn/post/7035910505810100255
- 启动入口包含@springbootAppliaction注解内多个注解（配置，自动装配，扫描）
- 构造方法
  - 判断当前程序类型（是否web程序）
  - 创建初始化构造器
  - 创建应用监听器
  - 定位mian方法
 - run方法
    - 主要创建了配置环境，事件监听，启动应用上下文
    - refresh方法贯穿bean的生命周期。执行bean生命周期前后置方法
    - 处理了spring注解标注的类
    - onRefresh通过java代码构建出tomcat容器并启动

springsecurity动态权限
- 在数据查找你访问的url需要什么角色，判断是否与自己登录的角色相同
- 请求时找到登录账号的角色，security拿到请求的路径去寻找包含这个url的角色，然后对比

