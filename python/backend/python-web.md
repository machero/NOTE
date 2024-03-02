### python-web应用框架使用文档



1. fast-api 创建对应的应用框架

   整个项目中的文件结构可以包含如下几部分，分别是app(应用层)、config部署配置、deploy 集群部署脚本、requirement项目依赖的安装包、src项目中需要用到的静态资源(schema、datamodel define、common function等)

   查看简易版demo 参考地址http://gitlab.caijj.net/tml/pokedexapi.git ，全量版demo http://gitlab.caijj.net/tml/omnibot 。模版框架后期整理后发出...

   <img src="/Users/admin/Library/Application Support/typora-user-images/image-20231115220104286.png" alt="image-20231115220104286" style="zoom:33%;" />



#### BCDS 上线python 应用

<font color='red'>第一次上线sit、pred、prod都可能会报错</font>，如果第二次运行报错联系BCDS 魏文哲

（1）数字产品目录--产品--应用管理界面 选择新增用户，创建对应的应用产品

![image-20231117095641309](/Users/admin/Library/Application Support/typora-user-images/image-20231117095641309.png)

(2)微服务平台--应用中心--应用列表 创建对应的应用（可以通过直接点击<font color='red'>点击跳转</font>）

![image-20231117100112198](/Users/admin/Library/Application Support/typora-user-images/image-20231117100112198.png)

创建应用的相关配置如下表所示

![image-20231117095850377](/Users/admin/Library/Application Support/typora-user-images/image-20231117095850377.png)

（3）创建应用成功后，点击关联应用。

（4）应用创建成功后的截图

![image-20231117100455711](/Users/admin/Library/Application Support/typora-user-images/image-20231117100455711.png)

（5）应用中的具体配置信息

- 代码配置

![image-20231117100549841](/Users/admin/Library/Application Support/typora-user-images/image-20231117100549841.png)

新建应用需要手动添加到代码仓库，可以返回应用管理界面--代码仓库--添加，添加对应的代码仓库信息

![image-20231117100631992](/Users/admin/Library/Application Support/typora-user-images/image-20231117100631992.png)

![image-20231117100849218](/Users/admin/Library/Application Support/typora-user-images/image-20231117100849218.png)

- 镜像文件地址配置

  ![image-20231117101055840](/Users/admin/Library/Application Support/typora-user-images/image-20231117101055840.png)

  - 代码评审配置

    

  ![image-20231117102658594](/Users/admin/Library/Application Support/typora-user-images/image-20231117102658594.png)

- 初次部署，或每次修改代码后都需要打一个新的tag（初次创建需要在项目目录下创建feature/bcds、develop两个分支，并加入member）

  ![image-20231117102843147](/Users/admin/Library/Application Support/typora-user-images/image-20231117102843147.png)

  先创建feature tag 之后再创建对应的release tag

  ![image-20231117103409531](/Users/admin/Library/Application Support/typora-user-images/image-20231117103409531.png)

  新增tag 中的代码评审人员第一次为项目组长(可由项目组长在配置界面进行修改)

  ![image-20231117103156823](/Users/admin/Library/Application Support/typora-user-images/image-20231117103156823.png)

  



- 上线生产

  ![image-20231117103919862](/Users/admin/Library/Application Support/typora-user-images/image-20231117103919862.png)

 选择对应的当天日期，并创建对应的发布计划，首次发布需要再环境信息中配置对应的pre、prod集群信息

![image-20231117104137375](/Users/admin/Library/Application Support/typora-user-images/image-20231117104137375.png)





