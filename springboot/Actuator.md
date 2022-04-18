# Actuator

依赖 

```
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```



配置

```yaml
management:
  endpoints:
    web:
      exposure:
        include: "*"
```





使用

| HTTP | 方法路径                 | 描述                                                         |
| ---- | ------------------------ | ------------------------------------------------------------ |
| GET  | /actuator/conditions     | 提供了一份自动配置报告，记录哪些自动配置条件通过了，哪些没通过 |
| GET  | /actuator/configprops    | 描述配置属性(包含默认值)如何注入Bean                         |
| GET  | /actuator/beans          | 描述应用程序上下文里全部的Bean，以及它们的关系               |
| GET  | /actuator/dump           | 获取线程活动的快照                                           |
| GET  | /actuator/env            | 获取全部环境属性                                             |
| GET  | /actuator/env/{name}     | 根据名称获取特定的环境属性值                                 |
| GET  | /actuator/health         | 报告应用程序的健康指标，这些值由HealthIndicator的实现类提供  |
| GET  | /actuator/info           | 获取应用程序的定制信息，这些信息由info打头的属性提供         |
| GET  | /actuator/mappings       | 描述全部的URI路径，以及它们和控制器(包含Actuator端点)的映射关系 |
| GET  | /actuator/metrics        | 报告各种应用程序度量信息，比如内存用量和HTTP请求计数         |
| GET  | /actuator/metrics/{name} | 报告指定名称的应用程序度量值                                 |
| POST | /actuator/shutdown       | 关闭应用程序，要求endpoints.shutdown.enabled设置为true       |
| GET  | /actuator/httptrace      | 提供基本的HTTP请求跟踪信息(时间戳、HTTP头等)                 |
| POST | /actuator/bus-refresh    | 配置更新                                                     |
|      |                          |                                                              |