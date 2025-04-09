 Oracle公司现在作为Java语言的开发和发布者，是当仁不让的标准接口的制定者。Oracle公司不仅制定了Web应用与Web服务器进行协作的一系列标准Java接口（统称为Java Servlet API），还对Web服务器发布以及运行Web应用的一些细节做了规约。
Oracle公司把这一系列标准Java接口和规约统称为 Servlet规范。Servlet规范的官方网址为：
https://www.[oracle](https://so.csdn.net/so/search?q=oracle&spm=1001.2101.3001.7020).com/technetwork/java/javaee/documentation/index.html

Servlet规范把能够发布和运行Java Web应用的Web服务器称为Servlet容器。Servlet容器最主要的特征是：动态执行Java Web应用中Servlet实现类的程序代码。由Apache开源软件组织创建的Tomcat是一个符合Servlet规范的优秀Servlet容器。Tomcat与Java Web应用之间通过Servlet接口来协作。

# Tomcat
Tomcat本身由Java语言编写，是Apache开源软件组织的一个软件项目
# Tomcat作为Servlet容器的基本功能
Tomcat作为运行Servlet的容器，其基本功能是：负责接收和解析来自客户的请求，把客户的请求传送给相应的Servlet，并把Servlet的响应结果返回给客户。

Servlet规范规定，Servlet容器响应客户请求访问特定Servlet的流程如下：
```
（1）客户发出要求访问特定Servlet的请求。
（2）Servlet容器接收到客户请求，对其解析。
（3）Servlet容器创建一个ServletRequest对象，在ServletRequest对象中包含了客户请求信息以及其他关于客户的相关信息，如请求头、请求正文，以及客户机的IP地址等。
（4）Servlet容器创建一个ServletResponse对象。
（5）Servlet容器调用客户所请求的Servlet的service（）服务方法，并且把ServletRequest对象和ServletResponse对象作为参数传给该服务方法。
（6）Servlet从ServletRequest对象中可获得客户的请求信息。
（7）Servlet利用ServletResponse对象来生成响应结果。
（8）Servlet容器把Servlet生成的响应结果发送给客户。

```


![Pasted image 20240206151112](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404090948965.png)

# Tomcat的组成结构
Tomcat本身由一系列可配置的组件构成，其中核心组件是Servlet容器组件，它是所有其他Tomcat组件的顶层容器。

用<CATALINA_HOME>表示Tomcat的安装根目录。Tomcat的各个组件可以在<CATALINA_HOME>/conf/server.xml文件中进行配置，每个Tomcat组件在server.xml文件中对应一种配置元素。以下代码以XML的形式展示了各种Tomcat组件之间的关系：
```java
<Server>
    <Service>
        <Connector />
        <Engine>
        	<Cluster />
        	<Realm>
        	</Realm>
            <Host>
                <Context>
                </Context>
                <Valve>
                </Valve>
            </Host>
        </Engine>
    </Service>
</Server>
```
在以上XML代码中，每个元素都代表一种Tomcat组件。这些元素可分为四类：
	1.顶层类元素
		包括`<Server>`元素和`<Service>`元素，它们位于整个配置文件的顶层。
		`<Server>`元素代表整个Servlet容器组件，它是Tomcat的顶层元素。`<Server>`元素中可包含一个或多个`<Service>`元素
		`<Service>`元素中包含一个`<Engine>`元素，以及一个或多个`<Connector>`元素，这些元素共享同一个元素。
	2.连接器类元素
		为`<Connector>`元素，代表介于客户与服务器之间的通信接口，负责将客户的请求发送给服务器，并将服务器的响应结果发送给客户。
	3.容器类元素
		代表处理客户请求并生成响应结果的组件，有四种容器类元素，分别为`<Engine>`、`<Host>`、`<Context>`和`<Cluster>`元素。
```java
1.Engine组件为特定的Service组件处理所有客户请求。
2.Host组件为特定的虚拟主机处理所有客户请求，每个<Host>元素定义了一个虚拟主机，它可以包含一个或多个Web应用。
3.Context组件为特定的Web应用处理所有客户请求。<Context>元素是使用最频繁的元素。每个<Context>元素代表了运行在虚拟主机上的单个4.Web应用。一个<Host>元素中可以包含多个<Context>元素。
Cluster组件负责为Tomcat集群系统进行会话复制、Context组件的属性的复制，以及集群范围内WAR文件的发布。
```
4.嵌套类元素
	代表可以嵌入到容器中的组件，如`<Valve>`元素和`<Realm>`元素等，例如上面的xml文件中，位置也是不固定的。
	提示，Tomcat的组成结构是由自身的实现决定的，与Servlet规范无关。不同的服务器开发商可以用不同的方式来实现符合Servlet规范的Servlet容器。
	Tomcat安装好以后，在它的server.xml配置文件中已经配置了`<Server>`、`<Service>`、`<Connector>`、`<Engine>`和`<Host>`等组件：
	从server.xml配置文件中可以看出，Tomcat自带了一个名为“Catalina”的Engine组件，它的默认虚拟主机为localhost。
# Tomcat的工作模式
Tomcat作为Servlet容器，有以下三种工作模式。
1.独立的Servlet容器，由Java虚拟机进程来运行
	Tomcat作为独立的Web服务器来单独运行，Servlet容器组件作为Web服务器中的一部分而存在。这是Tomcat的默认工作模式。在这种模式下，Tomcat是一个独立运行的Java程序。和运行其他Java程序一样，运行Tomcat需要启动一个Java虚拟机（JVM，Java Virtual Machine）进程，由该进程来运行Tomcat，如下图：
![](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404090948917.png)
2.其他Web服务器进程内的Servlet容器
	在这种模式下，Tomcat分为Web服务器插件和Servlet容器组件两部分。如下图所示，Web服务器插件在其他Web服务器进程的内部地址空间启动一个Java虚拟机，Servlet容器组件在此Java虚拟机中运行。如有客户端发出调用Servlet的请求，Web服务器插件获得对此请求的控制并将它转发（使用JNI通信机制）给Servlet容器组件。
	提示，JNI（Java Native Interface）指的是Java本地调用接口，通过这一接口，Java程序可以和采用其他语言编写的本地程序进行通信。
![Pasted image 20240206154126](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404090950954.png)
进程内的Servlet容器对于单进程、多线程的Web服务器非常合适，可以提供较高的运行速度，但缺乏伸缩性。
3.其他Web服务器进程外的Servlet容器
	在这种模式下，Tomcat分为Web服务器插件和Servlet容器组件两部分。如下图所示，Web服务器插件在其他Web服务器的外部地址空间启动一个Java虚拟机进程，Servlet容器组件在此Java虚拟机中运行。如有客户端发出调用Servlet的请求，Web服务器插件获得对此请求的控制并将它转发（采用IPC通信机制）给Servlet容器。
![Pasted image 20240206154255](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404091000821.png)
进程外Servlet容器对客户请求的响应速度不如进程内Servlet容器，但进程外容器具有更好的伸缩性和稳定性。  
提示，IPC（Inter-Process Communication，进程间通信)是两个进程之间进行通信的一种机制。

从Tomcat的三种工作模式可以看出，当Tomcat作为独立的Servlet容器来运行时，此时Tomcat是能运行Java Servlet的独立Web服务器。
此外，Tomcat还可作为其他Web服务器进程内或者进程外的Servlet容器，从而与其他Web服务器集成（如Apache和IIS服务器等）。
集成的意义在于：对于不支持运行Java Servlet的其他Web服务器，可通过集成Tomcat来提供运行Servlet的功能。

# Tomcat版本
Tomcat和Servlet/JSP规范以及JDK版本的对应关系
![Pasted image 20240206154557](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404090948917.png)

# Tomcat安装和配置
以下安装和配置，默认是在**Windows**系统中进行：
## 安装
从Tomcat官网，下载压缩文件或者EXE文件，来安装
## 配置
Tomcat配置需要配置的环境变量：

JAVA_HOME: JDK安装路径 例如：C:\Program Files (x86)\Java\jdk1.8.0_131
JRE_HOME: JRE 安装路径 例如：C:\Program Files (x86)\Java\jdk1.8.0_131\jre
以上两个环境变量，只需要配置一个就可以

下面这个环境变量不是必须的：
CATALINA_HOME = Tomcat安装路径

## 启动和关闭
| 操作系统  | 启动脚本 | 关闭脚本 |
| ---- | ---- | ---- |
| Windows | <CATALINA_HOME>\bin\startup.bat | <CATALINA_HOME>\bin\shutdown.bat |
| Linux | <CATALINA_HOME>/bin/startup.sh | <CATALINA_HOME>/bin/shutdown.sh |

注意：  
可以在Tomcat安装路径的地址栏输入cmd, 然后按回车键，就是到当前路径下执行cmd命令，  
可以输入startup，或者shutdown 来启停Tomcat，用完后一定要记得shutdown, 不然下次就会出现8080端口被占用的情况；

Tomcat服务器启动后，在浏览器中访问下面的URL：
http://localhost:8080

如果出现如下的网页，则表示Tomcat安装成功：
![Pasted image 20240206162344](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404090951237.png)

## Tomcat的运行脚本
如果仔细研究一下Tomcat启动和关闭脚本（以Windows操作系统为例），会发现startup.bat和shutdown.bat都执行同一目录下的catalina.bat脚本。catalina.bat脚本允许输入命令行参数，catalina.bat的使用方法参见下表：
![Pasted image 20240206162426](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202404090951830.png)
执行startup.bat脚本，相当于执行了catalina start命令；  
执行shutdown.bat脚本，相当于执行了catalina stop命令；  
在开发和调试阶段，运行`catalina run`命令更有利于查看Tomcat服务器启动时的出错信息。

在某些情况下，如果Tomcat的server.xml文件的配置有错误（最常见的是语法错误，导致org.xml.sax.SAXParseException异常），可能会导致Tomcat服务器启动失败，而且没有在文件系统中留下任何日志信息。如果运行catalina start命令，Tomcat服务器在一个独立的DOS窗口中启动，一旦启动失败，这个DOS窗口就立刻自动关闭，程序运行中输出的出错信息也随之消失；如果运行catalina run命令，Tomcat服务器在当前DOS窗口中启动，一旦启动失败，仅仅是Tomcat启动程序异常终止，在当前DOS窗口中仍保留了运行时的出错信息，便于查找启动失败原因。

注意，Tomcat安装软件中附带了详细的使用说明文档，在安装好Tomcat以后，该文档以Web应用的形式存放在：<CATALINA_HOME>/webapps/docs目录下.