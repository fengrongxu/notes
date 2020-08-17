### 一、Servlet：服务器端的小应用程序。

​                     作用：处理客户端的请求和相应。###

### 二、Servlet的生命周期

​                     实例化 ---》》初始化--》》 服务 --》》 销毁

​                                            int                   service        destroy

### 三、Servlet的3种创建方式：

​                    实现javax.servlet.Servle接口

​                    继承javax.servlet.GenericServlet类（适配器模式）

​                    继承javax.servlet.http.HttpServlet（魔板方法设计模式）

### 四、线程安全;

​                    不要使用全局变量，要是用局部变量。

### 五、ServleConfig

​                     获取配置文件的信息

​                      获得ServletContext对象



### 六、与servlet相关的对象

​                      Servlet                                                接口javax.servlet.Servlet

​                     GenericServleet                                 抽象类javax.servlet.GenericcSerclet

​                     HttpServlet                                          抽象类javax.servlet.http.HttpServlet

​                     ServletConfig                                       接口  javax.servlet.ServletContext

​                     ServletContext                                     接口 javax.servlet.ServletRequest

​                     ServletRequest                                     接口 javax.servlet.ServletRespons

​                     HttpServletRequest                             接口 javax.servlet ServletResponse

​                    HttpServletResponse                            接口 javax.servlet.http.Http.HttpServletRequest

​                    RequestDispatcher                                接口 java.servlet.RequsetDispatcher

