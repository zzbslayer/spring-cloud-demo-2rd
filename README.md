# Spring Cloud Component

- Eureka
- Ribbon
- Feign
- Hystrix
- Zuul
- Zipkin

## service-eureka

使用Eureka作为服务注册中心，运行于端口8761。

## service-hi

简单的say-hi服务。
通过取消单例设置以及修改配置端口，运行两个service-hi服务，分别运行于端口8762、8763

## service-ribbon

使用Ribbon做负载均衡，将对于say-hi服务的访问分散于两个service-hi。
并且使用Hystrix熔断机制，对于service-hi访问失败时，触发fallback method。

## service-feign

同理Ribbon，使用Feign负载均衡。
并且使用Hystrix熔断机制，对于service-hi访问失败时，触发fallback method。

## service-zuul

使用Zuul做路由、过滤等功能。
将/api-a前缀的请求转发至service-ribbon；将/api-b前缀转发至service-feign。
并且要求请求中带有token参数，如果没有token则被zuul过滤。

## service-zipkin

使用zipkin做服务链追踪。
不过项目中两个hi服务之间并没有依赖。


