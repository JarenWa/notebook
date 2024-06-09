<p align="center">
   <a style="font-size:30px;"> Java 实现 RPC </a>
</p>

<p align="center">
   <a href="" target="_blank"> Github </a>
</p>


# 如何理解RPC
RPC（Remote Procedure Call），是一种计算机通信协议。RPC 的主要功能目标是**让构建分布式计算（应用）更容易**，在提供强大的远程调用能力时不损失本地调用的语义简洁性。

**RPC 框架需提供一种透明调用机制，让使用者不必显式的区分本地调用和远程调用。**

## 方法调用
先思考一个问题，A系统如何调用B系统的一个方法。

- A系统依赖B系统

  如果直接在A系统引入B系统作为依赖，然后调用相应的方法，那么不就成为一个单体系统了吗。

- 接口方法





RPC 服务方通过 RpcServer 去导出（export）远程接口方法，而客户方通过 RpcClient 去引入（import）远程接口方法。 客户方像调用本地方法一样去调用远程接口方法，RPC 框架提供接口的代理实现，实际的调用将委托给代理 RpcProxy 。