<p align="center">
   <a style="font-size:30px;"> 登录模块 </a>

</p>



# 优化

![2024-04-16-21-21-22.png](assets/2024-04-16-21-21-22.png)


临时方案验证码使用 session 方案，分布式部署存在 session 共享问题。

临时方案登陆凭证存在 MySQL，访问频次高，性能存在问题。