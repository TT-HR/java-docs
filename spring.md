springboot自动装配
  - 在@springbootApplication注解中有@enableAutoconfiguration负责自动装配
  - 是在meta-info/spring.configuration中存储了配置，需要在pom中使用相关starter注解即可使相关自动装配生效
事务
- 分为编程式事务和声明式事务
- 编程式事务指硬编码的方式在业务中使用事务
- 声明式事务建立在aop之上的，本质是对方法前后进行拦截
