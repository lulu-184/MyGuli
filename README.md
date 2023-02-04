# MyGuli
本人学习SpringBoot后写的1个基于SpringBoot、mysql、vue的curd项目
其中前端和后端分别打成了两个压缩包vue-admin-template-master是前端部分、guli-parent是后端部分

# Introduction 

**本人学习SpringBoot后决定自己写1个基于SpringBoot、mysql、vue的curd项目，收获颇丰，不过本人才疏学浅，难免有所疏漏，若有批评和建议请发到邮箱1842352861@qq.com**





启动前后端前需要启动 nginx-1.12.2，用于负载均衡

需要修改 conf/ nginx.conf 文件的server部分，如下：

```
  server {
        #listen  9001;
        listen  7001;
        server_name localhost;
        # 代表客户端最大大小是20M
        client_max_body_size 1024M;
        location ~ /eduservice/ {
        proxy_pass http://localhost:8001;
        }
        location ~ /edu/ {
        proxy_pass http://localhost:8001;
        }
        location ~ /eduoss/ {
        proxy_pass http://localhost:8002;
        }
        location ~ /eduvod/{
        proxy_pass http://localhost:8003;
        }
    }
```





# 前端部分

**需要node v：10.9.0版本**

使用如下命令安装和运行

```
// 安装命令
npm install

//启动命令
npm run dev
```



# 后端部分

一共有5个模块，其中

工具类模块：

* common_utils
* service_base

需要启动的模块：

* service-edu
* service-vod
* service-oss

### 数据库

本项目数据库采用的是mysql8.0

数据库的配置文件在service-edu模块下的配置文件application.properties内，可以自行修改，例如：

```
# mysql数据库连接
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/guli?serverTimezone=GMT%2B8
spring.datasource.username=root
spring.datasource.password=184235
```





登录成功后：

默认账户和密码都是admin，效果图：

![image](https://user-images.githubusercontent.com/104906471/216757275-a15b9af1-d9ba-4349-9950-b9c9b3d581fb.png)


登录成功后：

![image](https://user-images.githubusercontent.com/104906471/216757285-6d45338e-f8ac-4266-a997-274c5ce2230f.png)
![image](https://user-images.githubusercontent.com/104906471/216757292-e816e890-61bb-4c2d-8881-d7c305058952.png)
![image](https://user-images.githubusercontent.com/104906471/216757296-27022a33-5f06-4c8b-9ba9-4f82d7dfa1bf.png)
![image](https://user-images.githubusercontent.com/104906471/216757301-6838bdc2-afd3-4ab9-accf-119db9ff4b96.png)






# 常见错误

* **未修改 nginx 配置文件，或者未启动 nginx，会导致Error错误**





