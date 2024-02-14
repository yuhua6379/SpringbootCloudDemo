# SpringCloudDemo

这是一个五脏俱全的简单SpringCloudDemo，包含了简单的登陆中心和一个示例服务器，还有必备的gateway和eureka，我写来为自己做一些记录，如果有需要可以随意使用

# 集群的工作流程

## 身份验证流程图

```plaintext
+---------+      +--------+      +------+ 
|         | user |        |      |      | 
|  Client +----->+ Gateway+----->+ Auth | 
|         | pass |        |      |      | 
+----+----+      +----^---+      +--+---+ 
     |               |              |
     |               |              |
     |               |              |
     +---------------+              |
        Get Token <-----------------+
```

# 常规访问流程图

```plaintext
+---------+      +--------+      +------+ 
|         |      |        |      |      |
|  Client +----->+ Gateway+----->+ Auth | 
|         |      |        |      |      |
+---------+      +---+----+      +--+---+   
                      |              |        
                      |              |        
                      |              |        
                      |          Token Valid?  
                      |              |         
                      |              v         
                      |         +----+----+   +--+-----------------+   
                      +-------->+ UserName+-->+ Add X-UserName     +---> .....
                                +---------+   +--------------------+
```