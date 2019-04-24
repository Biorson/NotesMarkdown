[TOC]

### Servlet的一生

* 同期启动时，寻找已经部署的web应用，开始搜索servlet类文件，容器找servlet类文件时，servlet的生命开始

* 加载类，可能发生在容器启动时，也可能在第一个客户使用使用时加载

* 初始化servlet（构造函数运行）不要在servlet的构造函数放任何东西，构造函数开始，使之成为一个普通对象

* init() ，容器为此生成一个ServletConfig，调用init()，此时，才是真正的servlet对象，init() 在servlet一生中只运行一次，总是在第一个service()方法调用之前完成

* service() 容器调用，此方法再根据客户发出的HTTP方法(Get)，确定要调用哪个servlet方法（doGet()）

* destroy() 线程结束后，可以被回收


### API

```mermaid
graph BT
	MyServlet --> HttpServlet
	HttpServlet --> GenericServlet
	GenericServlet -.-> Servlet
```



#### Servlet（interface）

```
service(ServletRequest,ServletResponse)
init(ServletConfig)
destroy()
getServletConfig()
getServletInfo()
```

#### GenericServlet（抽象类）

```
service(ServletRequest,ServletResponse)
init(ServletConfig)
init()
destroy()
getServletConfig()
getServletInfo()
getInitParameter(String)
getInitParameterNames()
getServletContext()
log(String)
log(String,Throwable)
```

#### HttpServlet（抽象类）

```
service(HttpServletRequest,HttpServletResponse)
service(ServletRequest,ServletResponse)
doGet(HttpServletRequest,HttpServletResponse)
doPost(HttpServletRequest,HttpServletResponse)
doHead(HttpServletRequest,HttpServletResponse)
doOptions(HttpServletRequest,HttpServletResponse)
doPut(HttpServletRequest,HttpServletResponse)
doTrace(HttpServletRequest,HttpServletResponse)
doDelete(HttpServletRequest,HttpServletResponse)
getLastModified(HttpServletRequest)
```

