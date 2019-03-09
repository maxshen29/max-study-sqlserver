# AKS创建SQL Server大数据群集

使用AKS创建SQL Server大数据群集有几种方法，由于产品不断的更新，SQL 2019也还没有正式发布，文档也会发生很多错误，在测试SQL Big Data遇到了很多的问题，终于经过几次尝试搞清楚了怎么来创建。 写下来给大家

1、首先必须申请使用，申请链接 https://sqlservervnexteap.azurewebsites.net/ 

2、申请成功后会收到微软SQL 产品组发的一封邮件，邮件会给你类似下面的信息：

```
DOCKER_USERNAME=微软申请的用户名   //这里是从微软的官方试用申请提供的用户名
DOCKER_PASSWORD=密码			   //这是从微软官方试用申请的试用提供的密码
DOCKER_EMAIL=申请的信息中的mail     //这是从微软官方试用申请的试用提供的mail
```

3、在进行创建的过程中需要使用到此信息。

4、第一种方法直接创建aks时候就创建一个SQL Bigdata群集，可以使用一个脚本， [部署脚本](/Demo/bigdata/deployment-aks-sqlbigdata.py)

 ![01](image\01.jpg)

```CMD
SET ACCEPT_EULA=yes
SET CLUSTER_PLATFORM=aks

SET CONTROLLER_USERNAME=max
SET CONTROLLER_PASSWORD=abc@1234
SET KNOX_PASSWORD=abc@1234
SET MSSQL_SA_PASSWORD=abc@1234

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=微软申请的用户名   //这里是从微软的官方试用申请提供的用户名
SET DOCKER_PASSWORD=密码			   //这是从微软官方试用申请的试用提供的密码
SET DOCKER_PRIVATE_REGISTRY="1" 
SET DOCKER_EMAIL=申请的信息中的mail     //这是从微软官方试用申请的试用提供的mail

mssqlctl create cluster sqlbigdata
```



  