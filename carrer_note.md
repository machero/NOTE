（1）使用gensim 中的word2vec 方法训练对应的app 的向量表示==需考虑到applist 中无序==，且==原有的word2vec中将embedding看做一个移动窗口进行预测的过程==
- 如何设置word2vec 的窗口值


### 配置aws中的认证
==以下配置的环境变量都是在home路径下(~/.aws/)==
1. config
	```
	[default]
	region=us-west-2
	output=json
	```
	
	
	
2.  credentials
```
[default]
aws_access_key_id=xxxxxx
aws_secret_access_key=xxxxxxx
```



### aws中s3协议提供了分块读取
`max_concurrent_requests`方法和`max_queue_size`
### 部分概念详解
1. region 
	默认为发送到的服务器所在的AWS区域，例如官网举例`us-west-2`表示为美国西部
	
	
	

	### 配置对应的top_keyphrase
代码路径： (待完成代码任务)
http://gitlab.caijj.net/tml/video_keyphrase_extractor/-/blob/dev/top_keyphrase.py
	
	


### mlflow 中用到的几个关键词 
`step`表示单独的ML操作，包括注入数据、评估筛选等、通俗的说==接受预定义的输入数据并生成定义好的输出数据==

`recipes`表示一个有序的steps用来解决ML的任务

`Template` 表示类似git 中的版本库的概念。包含所有定制化的代码和配置，主要配置代码在recipe.yaml文件夹中

`Profiles`主要包含用户自定义和环境自定义，包含一系列超参调试通过mlflow model regstry uri 

`Step Cards` 用来展示执行每个step之后的结果，包括数据集设置、模型表现、回溯最优的模型参数，这些数据都记录到对应mlflow tracking 过程中

### 需要配置的yaml 文件
针对recipe.yaml 中的文件修改对应的FIXME::REQUIRED



```
# mlflow 中的部署代码
os.chdir("/Users/admin/recipes-examples/regression")

regression_recipe = Recipe(profile = "local") #查看当前目录下的recipe.yaml ,profile 还可配置为dev表示加载文件夹下的

regression.run()

regression_recipe.inspect(step="train")

regression_model_recipe: pyFuncModel = regression_recipe.get_artifact("model")


```

profile中创建对应的local.yaml-->主要是针对exprement 的实验名称、tracking server、database

利用基类_BaseRecipe 展示对应的每一个step 产生的结果




### 一个完整的yaml包含的步骤





shap value 的作用源于automl 中训练的方法，查看每个特征对模型的边际贡献，模型给出预测值可能和某些特征有关，shape 属于模型事后解释的方法。 其中对每个特征会计算一个特征期望

提供单样本特征图



# tips
path.resolve() 中返回对应的绝对路径



1. RDD
RDD(Resilient Distributed Datasets)，弹性分布式数据集，是Spark的基本数据结构。RDD中的每个数据集被划分为逻辑分区，其可以在集群的不同节点上计算。（每个RDD拥有五个主要属性分区列表、其他RDD的依赖关系、计算分片的函数、键值RDD中的分区器Partitioner）
RDD的逻辑执行计划--RDD 运算图符

窄依赖和宽依赖
（1）窄依赖
join、map、filter、union操作中每一个RDD的都是使用子RDD分区中的
（2）宽依赖
groupbykey、join操作每一个分区的RDD元素都依赖于多个子分区的RDD 元素。



## RDD中的task和stage的关系
（1）Task是Spark 中最小的任务执行单元，RDD 上的每个操作都会转化为task上对应的操作并分配到对应的exetutor上对相应的partition进行操作。
（2）


stage 是程序执行时的物理，


### inspect 方法
模型运行的过程中获取运行态的状态，通过inspect 可以直接获取到对应的模块、类、实例、函数和方法

### 上下问管理器的用法
典型用途为open函数，若执行内部函数的过程中报错不能将文件资源释放，为此需要使用


## match 方法
match 方法主要是用来匹配当前表达式中是否存在某个pattern
```
example1
import re
# re.I表示不区分大小写
pattern=re.compile(r'[A-aZ-z]',re.I)
re.match('ssssss',pattern)  ### 若匹配到对应的字符串返回第一次匹配的位置(match对象)

```


### findall
findall 方法主要是返回所有匹配到的值，若不存在则返回对应的空list
```
example2
import re

pattern = re.compile(r'[A-aZ-z]',re.I)
pattern.findall('sssssss')

```






ack 集群---》通过配置yaml文件生成对应的workflow的包--》
argo中存在event 配置（sensor、bus、trigger、event）


deportment 可以看作对象的检测，


workflow  cronworkflow 
kind 
template   -dag ：A（depence ）、B（ depence A）
task


A-B-C(freecell---pod中的工作流管理)


### 关于现有读取csv方法和pytorch读取csv 方法的对比
1.对比1200000条数据集下的csv文件读取
datapip的csv_read():  0.4627971649 (其中考虑读取之后进行遍历的过程)
pandas中的csv_red(): 6.984879255  （考虑读取之后遍历的过程）


### datapip
datapip的出现是为了简化原有的dataset，提出一个torchdata的数据流方式，其中主要包括两种方式构建datapip，第一种是iterable-style类型（主要通过继承isterwraper方法），第二种则是map-steyle（主要通过）





### 分布式框架自动化结构
![流程图 (1).jpg](:/e2359480b40746f5aaf497e07890d662)

分布式自动化1.0：
需要依赖对应的yaml文件，通过判断生成对应的cpu、GPU、Workflow、oss桶输出、images 对应的名称，自动化的配置yaml生成，并生成对应的ray-cluster-autoscaler.yaml文件。使用kuberate api 生成对应的head、worker节点，使用kuberate api 获取到对应的head节点的ip地址。



分布式自动化2.0：
配置jupyterhub 上的分布式接口，可以通过填写不同的配置项生成对应的yaml，利用衔接分布式1.0使用yaml启动对应的任务并进行运算。




难点：
1、分布式任务中出现crash error 的问题的解决
2、分布式任务中存在的ray.shutdonw()的过程中head和work节点并没有同时关闭。





### ray中主要的五部分

- Ray Data 为Ray中提供的分布式数据集，由一系列Ray对象的blocks组成。
- Ray Train 为Ray中读取的csv文件,提供自定义的dataset类型，ray中dataset的创建支持本地存储，也支持远端s3协议访问。高性能，支持分布式，能进行json、csv等文件格式转换。
- Ray Tune 
- Ray Serve
- Ray RLlib
- Ray Workflows


#### Ray Data
使用ray中特有的dataset类，其中主要是包含map()、filter()、flat_map()等方法转化为对应的并行执行。

==ray.data.read_parquet==方法可以用来直接读取

关于Ray中存储数据的格式==借鉴Apache中的Arrow思想==



![截屏2022-08-16 下午8.13.51.png](:/e5f297c9f95f4b9bb46709d69710567d)

与传统存储方式相比arrow方式的文件存储是以列的形式存储文件，将相同类型的字段聚合到一起，如下图所示，为Arrow进行存储的过程。


![截屏2022-08-16 下午8.27.12.png](:/0b030d5d9f394772a994667f655de49c)
dataset 中的pipline，主要作用是为了重叠输入输出。

读取数据方面，使用ray能够读取远程数据，并创建多个并行的读取任务，产生多个ray中的dataset块(max=2G)==大文件还是建议使用json==


如何提升文件的读写，多机多卡的形式读取文件(尽量提高使用效率)



#### Ray Train

#### Ray Tune

#### Ray Serve

#### Ray RLib

#### Ray Workflows






4. third part
arm：
- 将对应文本的正例和负例样本进行划分，其中按照case_repay_sum_queue中的最后一条进行归因，并等比例生成对应的文本信息。
- 加入对应的备注信息，构建conversion 、session、note之间的数据关系。
```example： conversion:{
"au":[{s_sessions1,q_session1,context_type},{s_session2,q_session2,context_type}],
"note":'',
"label":''
}
```
催收队列id的确认按照case_repay_sum_queue中的状态来做区分。

## 关联关系：







### 



(1) 语速、语气需要自己计算，自己定义对应的





hanlp进行文本数据提取

(1) 利用分词模型和postag模型对文本进行识别，将文本按照V+N段的形式进行划分（排除其中的无效词）





考虑如何进行应用知识图谱在借贷模型中
落点为知识图谱的推荐(智能分案)


S1 阶段与其他阶段差异较大，抢批


1. 关于上传文件到oss端
	登陆跳板机--->进入conda环境中(tml-emr-pack)--->利于s3命令进行文件访问即上传
	
2. 关于强制删除pod的命令
kubetcl delete pod <pod_name> -n <name-space>--force --grace-period=0	
	
	
==相关命令详解==
(1)awss3 ls/cp/mv s3://lattebank-emr/video/xxx/version





# 贷后数据分析

## 全局的数据格式
 
1. convesation_total 3068211
2. total_result  162837555
3. start_time : 2022-10-1  end_time : 2022-10-12
平均计算下来每个convesation的值为53，即每段对话平均下来都有53条

使用vdm_risk.vdm_risk_collection_case_repay_sum_queue表进行用户信息的关联，其中需要考虑





疑问：
正例样本定义是什么？（当天还款还是）  
表格中的proc 是有什么关联的字段吗？


待确认的问题：

1、催收对话有效性的问题
按照现目前的dp表来看对话信息和催收阶段的关联之处为客户id（在sum_queue中表现为uid?），存在于repay_sum_queue中的is_customer_pay_off表示逾期结清作为最终评价，但若一天内经办拨打三次电话最后一次结清了，对应到sum_queue表中还是只有uid标志结清，那如何衡量这三次电话那次有效，那次无效？


2、队列划分
队列划分只能按照asr_info_df和vdm_risk_sum_queue来进行关联划分对应的不同队列？

3、关于每次催收后经办填写的备注信息是asr_info_df表中有体现的字段吗？




#### 贷前评估任务
(1) 一般任务中会出现4步
分别是样本复制、变量选择、策略生成(DT、RF、GRID)、策略报告生成、策略自动筛选

step1
样本筛选：
按照rules 的规则对数据进行复制





文本情感倾向性分析：对说话人的态度（或称观点、情感）
进行分析，也就是对文本中的主观性信息进
行分析。

==情感倾向分析的研究大致可
以分成词语情感倾向性分析、句子情感倾向
性分析、篇章情感倾向性研究、海量信息的
整体倾向性预测四个研究层次。==

判别方式（针对名词、动词、形容词和副词为主也包括人名、机构名、产品名、事件名）

### 关于配置jupyterhub上pip.conf进行按包
```
[global]
index-url=https://registry.caijj.net/repository/pypi/simple
```



jupyterhub 数据库链接
	username : sit_user_95f3559
	password : sit_user_95f3559_6d9a28
	url : cjjloan.db.ali-bj-sit01.shuheo.net
argo 数据库链接
	username:bdsit_user_a575b1b
	password:bdsit_user_a575b1b_013cb0
	url:bigdata-biz.db.ali-bj-bdsit01.shuheo.net




conda 安装流程
（1）下载并处理索引的头文件
（2）减少对应索引文件数量
（3）将对应的包冲突问题转化为SAT 问题，即包是否满足冲突的问题
（4）将对应问题转化为求解SAT 问题，并生成对应的求解方法(该问题为NP非完全问题)
（5）下载并展开对应的文件
（6）核查包的内容
（7）从包的缓存中




### sensor dependcy
Lua 脚本实现例子
a='video-embedding-rs-1235678'
pattener = "((%a*)-(%a*))*"
print(string.find(a,pattener,0))
if 'video-embeddings-rs-'==string.match('video-embedding-rs-1235678','[%a%-]+')
then
	print("sucess")
end
print(string.match('hello world you have','(%w+%s){1,3}'))




测试用例的推荐 主要是针对现有bcds中story的依赖问题


ali-hb-acr01-registry-vpc.cn-beijing.cr.aliyuncs.com/ailab-jupyter/modelscope:2211281108




（1）videoembedding  配置argo的yaml文件
（2）videoembedding-rs 配置对应的文件