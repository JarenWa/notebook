
记录一些公共操作

# thymeleaf
### 1 启动模板引擎
在HTML文档中添加xmlns:th="http://www.thymeleaf.org"属性是为了启用Thymeleaf模板引擎的功能。Thymeleaf是一个用于服务器端和客户端渲染的模板引擎，它可以在服务器端生成动态的HTML页面，也可以在客户端通过JavaScript进行处理。

这个属性告诉浏览器，或者在服务器端的Thymeleaf引擎，要识别并处理带有Thymeleaf属性的标记。Thymeleaf属性通常以"th:"开头，用于在模板中插入动态数据、条件渲染、循环、事件处理等功能。

例如，您可以使用Thymeleaf属性来插入动态数据到HTML页面中：
```
<p>Welcome, <span th:text="${username}">User</span>!</p>
```
在上面的示例中，${username}是一个Thymeleaf表达式，它将在服务器端被解析并替换为相应的数据，然后发送到浏览器。
### 2 处理一些相对路径
```
<!doctype html>

<!--<html lang="en">-->
<html lang="en" xmlns:th="http://www.thymeleaf.org">

<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
	<link rel="icon" href="https://static.nowcoder.com/images/logo_87_87.png"/>
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" crossorigin="anonymous">

    <!-- <link rel="stylesheet" href="../css/global.css" />-->
    <!-- <link rel="stylesheet" href="../css/login.css" />-->

	<link rel="stylesheet" href="../css/global.css" />
	<link rel="stylesheet" href="../css/login.css" />
    <link rel="stylesheet" th:href="@{/css/global.css}" />
	<link rel="stylesheet" th:href="@{/css/login.css}" />

	<title>牛客网-注册</title>
</head>
<body>


</body>
</html>

```

复用

index.html中

	<header class="bg-dark sticky-top" th:fragment="header">

其他
    
    <header class="bg-dark sticky-top" th:replace="~{index::header}">


