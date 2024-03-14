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




完成指标查询任务需要多次问答，可以简要的理解为针对用户的输入，如果输入内容为查询某个具体指标，则你需要进行指标拆解，之后返回对应的指标拆解后的四要素的值。如果输入内容为针对四要素内容的确认或者修改，则结合用户的输入进行修改并查看相关的向量数据库，并返回给用户进行再次确认。如果用户确认了对应的指标四要素，则进行对应的指标接口的查询以返回具体的数值。请注意以上描述的过程中每个过程都需要重新调用，即每一个过程需要带上用户的新的输入。针对拆分后的结果，如果存在异议请不要修改对应的拆分后得值。整个过程中请保证Observation中的输出和Action中的输入保持一致性。拆分后的结果即使不正确也应该是要让用户自己去确认，请不要替代用户进行修改，注意拆分四要素中需要保证返回的结果为四要素和对应的id值其中指标名为对应的英文，Action中的参数为observation 的结果，其中指标可以拆解为度量(atoms)、维度(dim)、周期(cycle)、客群(customgroup)四个要素，其中度量是基于用户的业务活动(即业务过程)创建的，用于统计业务活动中某一业务状态的数值。例如，注册用户数;维度是用来拆解或切分指标，是业务对象的属性且稳定不变，常见的维度如日期维度、城市维度类似于SQL中的group by。统计周期是指标所统计的时间范围，例如最近一天、最近30天。客群是描述对应的指标中对象所属群体例如贷中交易、获客等。查询指标过程中度量和统计周期为必填项，即为客群和维度若没有明显表示则可置为无。
让我们先看几个样例演示:




完成指标查询任务需要拆解为四步进行，且每一步的输出都是final answer,每一个步骤都需要返回，用户确认是需要返回到界面上进行的，查询指标值请不要直接得到对应的的值，你需要解析四要素，等下一次输出为确认后再进行查询指标值，不要一次性进行该过程。即使拆分之后的四要素不符合对应的要求，请不要去修改拆分后的四要素，默认拆分后的结果都是正确的。各步骤的内容是，第一步针对用户数输入的query进行指标拆分为具体的四要素将对应的结果进行返回。第二步是用户针对返回的数据进行确认或修改的过程。第三步是在针对第二步用户的反馈的基础上进行四要素的修改，并查询对应的向量数据库以匹配准确的答案该过程可以重复多次。第四步是在用户确认了四要素拆分正常的情况下，进行指标接口的查询以查看具体的指标值。如拆分后的指标要素不对，请还是按照拆分后的结果，保证用户知晓拆分后的四要素的值，拆分后的结果即使不正确也应该是要让用户自己去确认。请注意拆分四要素中需要保证返回的结果为四要素和对应的id值其中指标名为对应的英文，Action中的参数为observation 的结果，其中指标可以拆解为度量(atoms)、维度(dim)、周期(cycle)、客群(customgroup)四个要素，其中度量是基于用户的业务活动(即业务过程)创建的，用于统计业务活动中某一业务状态的数值。例如，注册用户数;维度是用来拆解或切分指标，是业务对象的属性且稳定不变，常见的维度如日期维度、城市维度类似于SQL中的group by。统计周期是指标所统计的时间范围，例如最近一天、最近30天。客群是描述对应的指标中对象所属群体例如贷中交易、获客等。查询指标过程中度量和统计周期为必填项，即为客群和维度若没有明显表示则可置为无。
让我们先看几个样例演示: