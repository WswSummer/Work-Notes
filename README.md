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

```yaml
# GateWay配置文件
spring:
  redis:
    host: localhost
    database: 0
    port: 6379
    password:
    timeout: 300ms
  boot:
    admin:
      client:
        # admin 服务端的地址
        url: http://localhost:2001

management:
  endpoints:
    web:
      exposure:
        include: '*'
  endpoint:
    health:
      # 展示详情
      show-details: always
# 过滤不需要认证路径条件
secure:
  ignored:
    urls: #安全路径白名单
      - /swagger-ui.html
      - /swagger-resources/**
      - /swagger/**
      - /**/v2/api-docs
      - /**/*.js
      - /**/*.css
      - /**/*.png
      - /**/*.ico
      - /webjars/springfox-swagger-ui/**
      - /actuator/**
      - /druid/**
      - /admin/login
      - /admin/register
      - /admin/info
      - /admin/logout
      - /minio/upload
jwt:
  tokenHeader: Authorization
  secret: mall-admin-secret
  expiration: 604800
  tokenHead: Bearer
redis:
  database: mall
  key:
    admin: 'ums:admin'
    token: 'ums:token'
    resourceList: 'ums:resourceList'
  expire:
    common: 86400 # 24小时
```

