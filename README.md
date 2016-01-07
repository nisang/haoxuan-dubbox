## 说明
	这个简单介绍只是方便大家运行了解dubbo以及rest功能

### 步骤如下：

###1 检出代码
	git clone https://github.com/dangdangdotcom/dubbox
	在checkout出来的dubbox目录执行mvn install -Dmaven.test.skip=true来尝试编译一下dubbo（并将dubbo的jar安装到本地maven库）
###2 生成IDE工程
	在checkout出来的dubbox根目录执行mvn idea:idea或者mvn eclipse:eclipse，来创建IDE工程文件
	将项目导入IDE
###3 启用zookeeper注册中心
	下载解压一个zookeeper，编辑其conf/zoo.cfg后启动zookeeper用作dubbo注册中心：bin/zkServer.sh start
###4 启动dubbo服务端
	用IDE运行/dubbo-demo/dubbo-demo-provider/.../test目录下的DemoProvider启动dubbo服务端，
	目前他会分别启动dubbo协议（包括用kryo和FST序列化）和REST协议的服务
###5 启动dubbo客户端
	用IDE运行/dubbo-demo/dubbo-demo-consumer/.../test目录下的DemoConsumer来
	启动dubbo客户端调用上面的服务端，直接看console的输出即可
###6 使用Java客户端访问REST服务
	用IDE运行/dubbo-demo/dubbo-demo-consumer/.../test目录下的RestClient来启动rest客户端
	（模拟非dubbo的rest客户端）调用上面的服务端，直接看console的输出即可
###7 使用浏览器访问REST服务
	可以在浏览器中直接访问http://localhost:8888/services/users/100.xml或者
	http://localhost:8888/services/users/101.json之类来测试REST服务
###8 集成tomcat
	了解tomcat和IDE集成的同事，可以直接在IDE中将/dubbo-demo/dubbo-demo-provider/部署到tomcat上
	，用tomcat的servlet容器来发布REST服务（要同时修改dubbo-demo-provider.xml，
	请看那个文件中的注释），然后用6、7、8中的方式来访问它。（当然也可以在命令行直接mvn package，然后将生成的war部署到外面的tomcat中做测试）
###9 启用监控器
	如果想看服务监控效果，或者避免demo抛出找不到监控的异常警告，用IDE运
	行/dubbo-simple/dubbo-simple-monitor/.../test目录下的SimpleMonitor来启动监控中心即可。
	访问：http://localhost:8080/
