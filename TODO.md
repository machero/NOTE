TODO：


Cron:  gennerate name修改为 nam
Event name:  

input parameter 有的不需要的


handler: 



TODO list

(1) shuling 任务：
针对书林任务，新增对应的least 版本做为生产环境的版本，设置时间为凌晨2
(2) 编写对应的移动文件的脚本  利用s3 访问数据的过程中将待发送的文件发送到 需要发送的人对应的文件位置
(3) datapipe 代码结构需要修改
(6)大伟 回溯任务按照每个月作为参数进行回溯主要包括1-30 大致回溯4个月 
(7) 任务改为凌晨5点开始运行

— 
**资信纬度进行拆开，需要进行按照每条资信作为id 进行拆分**



Fed: 订单纬度30天的预期表现
mob: 订单纬度预期30的的逾期表现




2-20
TODOLIST:
(1)S3f3 client ( 疑似冲突nlp , cv)
(2) 升级base (python3.7、python3.9、python3.10.0)







下周完成对应的step 的编写(对应变为支持step 的应用)



****（1）任务中添加一个数据处理方式，判断逻辑即若当前的datagather 数据里有数据不进行操作，若没有数据则进行插入操作。*****


resource  limit.  Cpu、memory限制
nodelselector:   





mlflow recipes 任务中需要进行处理的部分

Stepcard
 Sharp  图片

/model
/pyfunc model
/test
/pre_func
/recipe
	/ingest
	/split
	/transform
	/train
	/steps
	/code
/tmpdir
	/ingest  workflow.yaml
	/transformer workflow.yaml   tml/





目前mlflow任务中对每个step 进行hard_code.  为此需要对每个step都生成对应的_resoved结果


Split中提供对应的文本划分 oot、oov




#### TODO： 

针对资信任务中分批处理数据的问题，这里使用分批跑的方式
使用loop 进行分批任务进行训练



### 使用loop 生成对应的






###表上增加uid、ctime、字段，并找大数据同事进行回溯—   到时候就


### 整理对应的applist embedding 的代码给到林华兴




资信任务中的报错
1、该资信空跑任务跑失败了，原因是Wrong number of items passed 12, placement implies 1
2、该资信空跑任务跑失败了，原因是not writable
3、该资信空跑任务跑失败了，原因是'bad'
4、该资信空跑任务跑失败了，原因是not writable


TODO：
（1）中间的middle 进行资源调度 — 队列调度，在argo 任务上每次的过程中需要修改对应的hook 方法，针对每个任务需要考虑不同情况，主要是看每个cron 任务的结果，并返回对应的文本数据。

在每个任务调用之前需要关注是否需要执行。 调度任务— 判断当前环境是否需要运行。


(2) event git、MR 
触发式的任务执行需要配置对应的github cicd、 配置不同的rule 和不同的job 完成触发任务的更新， 验证、手动、验证、test suit
其中代码更新和requirements更新会自动更新对应的文件。



Issue 1: 用户当前环境是在jupyter notebook 上还是在argo 上运行，一次判断不同的环境执行不同的方法。 tml_env(sit、local、argo、jupyter)



原子表： 前端传递过来对应的sql代码
样本表： 前端传递过来对应的sql代码


TODO：新建point_words 映射表修改对应的时间表


insert OVERWRITE table dwa_model.dwa_model_records_keywords_extract_audio_text_input_df partition (ds = '20230225')
select uid,point_words,call_ids as call_id,cast(call_time,timestamp)as call_time,keywords_list,cast(keywords_cnt as int)as keywords_cnt
from dwa_model.dwa_model_records_keywords_extract_pharse_point_words
where ds ='20230225'




TODO:
Video-embedding-rs 迁移到其他节点
argo-cron-workflow 迁移到其他节点

消息接受为空则 设置为None


TODO：
credictbiz-argo-online-cron-worfkflow- 节点进行迁移

Jiangdehao


TODO:
将提供的dp 表pdm_risk.pdm_risk_daily_e1toe4_applistv3_202302_atmos中特征cat1、cat2、cat3合并为app embedding 的数值，利用风险的y值训练得到对应的uid embedding(用原有的数据进行finetune，之后利用训练后的结果)


- 施压点 从20230225 开始回溯到今天
