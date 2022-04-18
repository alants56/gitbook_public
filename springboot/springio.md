# spring.io 官方教程笔记



### 1.Building a RESTful Web Service



@SpringBootApplication 该注解等价于如下几个注解

* @Configuation：Tags the class as a source of bean definitions for the application context
* @EnableAutoConfiguration：start adding beans based on classpath settings, other beans, and various property settings.
* @ComponentScan：当前包下扫描其他组件，配置



@RestController 表示RESTful Controller

@GetMapping  HTTP GET映射等价于：

* @RequestMapping(method=GET)



### 2.Scheduling Tasks

@EnableScheduling 确保后台时间调度进程执行



@Scheduled

* (fixedRate = 5000) 每隔5000ms执行一次
* (fixedDelay = 5000) 执行完后5000ms执行一次
* (cron=)  更加严格的时间调度





