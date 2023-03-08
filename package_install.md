关于video_embedding和video_rs项目
1、代码文件位置
ip:10.8.145.169
位置：/home/xiaoshiran/video_embedding_scheduler/argo_workflow_scheduler/
video_embeddding: t2gen-true.yaml
video_rs: workflow_generate.yaml





2、smartbiz项目
ip:10.8.145.169
位置：/home/xiaoshiran/argo_news/argo/events/AMQP
位置2：/home/xiaoshiran/20230203_smartbiz/smartbiz
镜像文件生成地址 /home/jarpath/

3、 video-auto项目
位置：/home/xiaoshiran/newfile_20221024/argo_workflow_scheduler




4、资信数据
/home/xiaoshiran/newfile_20221024/daihou_keywords_analaz


5、custom 
/home/xiaoshiran/customer_insight


#### 关于video_embedding任务的回溯任务
目前代码已经放到对应的notebook上，但是还有几点未配置家在pvc 的位置



### video_key_autolabel yaml(本地电脑)
/20221130/video_keypharse_extractor/workflow_key_autophrase





### 设置pika 中的connectionparamparameter 中的heartbeat 为0



==待完成的工作==
（1）针对现有的argo workflow 上的所有tmlpatch 都需要将版本映射为指定的版本，保证升级版本的过程中不影响已有应用
|workflow名称||
|---|---|
|hot-dp-update|未切换|
|video-autolabel|未切换|
|video-embedding|未切换|
|video-history-keywords-extractor|未切换|
|video-insert-table|未切换|
|video-keywords-extractor|未切换|

（2）tmlpatch 中argo 需要修改的地方
argo_events 中提到的


1、阿里云配置信息
阿里云目录ID：cn-beijing+dir-imr0fuxcozdv4cxkd






### 项目
1、tml-patch
主要是对常用环境的一些包的安装，其中主要对dataphin、jupyter k8s、mlflow等任务的patch，其中针对dataphin中的patch包是handler.py中的函数调用，toPandas、toCsv等等
2、完成链接任务后需要进行argo 任务的编写，其中主要涉及argo/test文件夹中的workflow文件和argo中 的converat文件。

3、关于model server
调用模型的run方法过程中回去拉去conda环境，由于registry.caijj等链接问题导致拉取error，等待网络恢复。team-ml包中的内容


4、script runner 是作为python 的flask应用，主要对接模型的部署，其中主要涉及到server文件，文件中会引入caijj 自定义的包，其中主要是logger、webservive、zipkin（溯源，配置对应的id(分组)和span id（确认链路的合理状态））


如果出现报错查看阿里云日志。





环境依赖
pip install av fvcore opencv-python einops simplejson decord timm==0.4.12 tensorboardX tqdm-pathos moviepy tensorboard 
pip uninstall torchvision
pip install torchvision==0.10.0 --no-dependencies




#### argo events中的部署

已将代码上传到对应的argo文件夹下，明明为ai_lab_exprements_news.yaml 即为对应的amqp的server

修改代码过程中的测试样例
{"trainDataInfo":"{\"dpTable\":\"vdm_ailab_jupyter.vdm_ailab_jupyter_yfp_zkx_qinglan_a\"}","includedFeatures":"","excludedFeatures":"lending_customer_exclude_credit_version_bairong_score","hyperParameters":"{\"max_evals\":\"10\"}","trainDataType":"CUSTOMIZE","taskId":"test99","controlGroupName":"学历仅外呼"}
**注意修改对应的id，不重名**




TODO list：
配置max age 实现保留一周的消息







资信：
相关代码已部署到指定目录

gitlab中每个小标号表示一个任务



### linux中分割和合并压缩包
split xxx.tart.gz -b 1024m -d 原始包

cat xxx.tar.gz* >> arm_file.tar.gz

### linux 中解压tar包

tar zxvf  MY_NAME.tar.gz



TODO：
（1）完成对tmlpatch datapipe的修改







测试用例排序技术(test case prioritization)，计算某一组测试用例集合的排序相较于其他排序有较高的分数。

==衡量TCP问题的效果==
（1）特定评价函数：APFD（Average Percentage of Fault Detection）衡量TCP技术发现bug 的时机。
$$ APDF = 1- \frac{\sum_{i=1}^{m}TF_i}{nm}+\frac{1}{2n}$$

**若APDF的值较高表示较快发现bug**

（2）通用评价函数
召回率：
$$ recall_p = \frac{l}{m} $$
l表示执行测试的过程中发现的bug 数量，p表示执行测试用例占总测试用例的比例。m表示总的bug数量。
**recall 只越高表示，遗漏的bug数量越少**

