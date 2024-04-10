<p style="font-size:30px;">SpringMVC</p>
<p style="font-size:20px;">目录</p>
<!-- TOC -->

- [概览](#概览)
    - [服务端三层架构](#服务端三层架构)
- [MVC --用于解决表现层的问题](#mvc---用于解决表现层的问题)
        - [Thymeleaf](#thymeleaf)
- [Controller](#controller)
    - [如何在一个 Spring 控制器中处理 HTTP 请求和响应，包括读取请求数据和返回简单的 HTML 响应。](#如何在一个-spring-控制器中处理-http-请求和响应包括读取请求数据和返回简单的-html-响应)
    - [GET  请求](#get--请求)
    - [POST 请求](#post-请求)

<!-- /TOC -->

# 概览
## 服务端三层架构
（分包  解耦

表现层 

业务层 

数据访问层（持久层Dao）

![Alt text](%7BE5F93F10-388F-438a-8E35-31B31152E8DA%7D.png)


# MVC --用于解决表现层的问题

Model:模型层-数据
View：视图层
Controller:控制层

Controller：当浏览器请求访问服务器，访问的是Controller，接受请求的数据、调用业务层处理

Model:封装处理后的数据

View:根据Model，渲染生成HTML 返回浏览器


核心组件：前端控制器 DispatcherServlet


### Thymeleaf
更通用，以HTML文件为模板
https://www.thymeleaf.org/

其他：JSP...



# Controller
## 如何在一个 Spring 控制器中处理 HTTP 请求和响应，包括读取请求数据和返回简单的 HTML 响应。

```
    @RequestMapping("/http")
    /**定义了一个名为http的方法，并使用@RequestMapping注解将该方法映射到路径/http。该方法接受两个参数，HttpServletRequest和HttpServletResponse，用于获取HTTP请求和发送HTTP响应。*/
    public void http(HttpServletRequest request, HttpServletResponse response) {
        // 获取请求数据
        // 请求行（第一行
        System.out.println(request.getMethod());
        System.out.println(request.getServletPath());
        // 请求消息头
        Enumeration<String> enumeration = request.getHeaderNames();
        while (enumeration.hasMoreElements()) {
            String name = enumeration.nextElement();
            String value = request.getHeader(name);
            System.out.println(name + ": " + value);
        }
        System.out.println(request.getParameter("code"));
        // 返回相应数据
        response.setContentType("text/html;charset=utf-8");
        try(
                PrintWriter writer = response.getWriter();
                ) {
            writer.write("<h1>牛客网</h1>");
        }catch (IOException e) {
            e.printStackTrace();
        }
    }
```
##  GET  请求

##  POST 请求


浏览器向服务器提交数据   如何处理

浏览器打开带有表单的网页

resources下创建一个静态网页

POST 请求