<h1>appjishu.com开源项目-开发计划</h1>

## jseckill开发计划

| 序号 | 项目 | 任务 | 紧急程度 | 难易程度 | 开发者 |
| :------: | :------: | :------ | ------ | ------ | :------: |
| 1 | jseckill | [保存秒杀成功的订单到MySQL](#保存秒杀成功的订单到MySQL) | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 待领取 |
| 2 | jseckill | [用户登录、注册](#用户登录注册) | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | [ErCargo](https://github.com/ErCargo) |
| 3 | distarch | [分布式、高并发代码](#分布式高并发代码) | ⭐ | ⭐⭐⭐⭐ | 待领取 |
| 4 | microsvc | [Spring Cloud 2.x构建微服务系统](#SpringCloud2_x构建微服务系统) | ⭐⭐⭐ | ⭐⭐⭐ | [liushaoming](https://github.com/liushaoming) |


### 保存秒杀成功的订单到MySQL
GitHub [liushaoming/jseckill](https://github.com/liushaoming/jseckill)

简介：Redis里用户秒杀成功后， 立即把秒杀的信息（phone+seckillId）写入RabbitMQ的名为""pre_order"的queue中. <br/>
另外新建一个maven module "jseckill-order". 这个程序监听queue "pre_order"里面的消息. 收到消息后。 逐一的写入MySQL <br/>
的数据库"pre_order"中。 

注意： RabbitMQ采用生产端confirm并消费端手动应答的方式来确保不丢消息。

### 用户登录注册
GitHub [liushaoming/jseckill](https://github.com/liushaoming/jseckill)

认证机制: userId+token认证.     
注册的时候，只需要提供任意11位数字的手机号和符合格式的密码即可，无需用短信验证码和邮箱认证. 
目的是为了降低部署难度（短信服务和邮箱服务不是我们的关注点，也可以避免使用网友的真实手机号）.

技术上采用[fpassport](https://github.com/liushaoming/fpassport) 框架来实现.

### 分布式高并发代码
GitHub [liushaoming/distarch](https://github.com/liushaoming/distarch)

简介:
从自己工作中总结出来的高并发、高可用的技术积累，提炼出针对分布式场景的实现代码， 比如分布式锁的实现，比如ThreadLocal在各种中间件Connector
上的应用代码等。

### SpringCloud2_x构建微服务系统
GitHub [liushaoming/servicesvc](https://github.com/liushaoming/servicesvc)

简介:
由于Spring Cloud 2.X比1.X更新了很多地方。 比如弃用Eureka, 用Spring Cloud Consul代替它。 用Spring Cloud Gateway取代ZUUL。
(Netflix也在边缘化Hystrix等).  目前看到网上代码大多基于Spring Cloud 1.X。  我们需要紧跟Spring Cloud官方的步伐。于是，我启动
了<code>servicesvc</code>项目。
