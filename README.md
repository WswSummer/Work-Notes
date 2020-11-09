http://localhost:2001/task/create

```json
{
    "taskName":"test1",
    "taskCaption":"测试",
    "createDate":"20201109",
    "taskStatus":"0",
    "recepientId":1,
    "recepientName":"陆子恒",
    "testerId":1,
    "testerName":"王松文",
    "archive":"0",
    "modifyDate":20201109
}
```

***

```yaml
spring:
    datasource:
        type: com.alibaba.druid.pool.DruidDataSource
        url: jdbc:mysql://39.107.80.231:3306/task-system?useUnicode=true&characterEncoding=utf8&serverTimezone=Asia/Shanghai
        username: 
        password: 

mybatis:
    mapper-locations: classpath:mapper/*.xml
    type-aliases-package: com.wsw.fusertaskmanager.domain

management:
    endpoints:
        web:
            exposure:
                include: '*' 
```

***

