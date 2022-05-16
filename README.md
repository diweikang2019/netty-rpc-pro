## 说明

### 协议框架
1. 定义消息协议
2. 定义编解码器
3. 定义序列化

### 服务提供者
1. 实现接口
2. 启动netty服务端
3. 收到请求后找到对应的实现，通过反射调用

### 服务消费者
1. 创建代理对象
2. 在代理对象中启动netty客户端，发送请求数据

###
![流程图](flow_chart.png)

### 引入注解
* @RpcService  
  服务提供者启动时会启动netty服务端，并扫描注解类进行注册（保存到本地）。调用时通过名字找到对应的类进行反射调用。

* @RpcReference  
  服务消费者启动时扫描注解，创建代理对象并注册到容器中。代理对象会通过netty客户端发送调用请求。