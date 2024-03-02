#### mlflow 目前提供的权限认证功能



权限包含：

![image-20231122141314243](/Users/admin/Library/Application Support/typora-user-images/image-20231122141314243.png)

针对每一个用户可以设置针对exprement、register_model等的权限。

<font color='red'>basic_auth.db 中存储对应的用户中针对不同的exp、model等信息的权限</font>

目前提供的功能：

(1) 给用户赋予对应的四种资源管理权限

(2)创建对应的用户的信息



```python
import os
from mlflow import MlflowClient
from mlflow.server import get_app_client

## methods1: set the username and password to auth
os.environ['MLFLOW_TRACKING_USERNAME'] = 'admin'
os.environ['MLFLOW_TRACKING_PASSWORD'] = 'password'

## methods2: use the credentials to auth
cat>~/.mlflow/credentials <<EOF
[mlflow]
mlflow_tracking_username = username
mlflow_tracking_password = password



tracking_uri = "http://localhost:5000/"

# 调用mlflow auth client 创建对应的用户
auth_client = get_app_client("basic-auth", tracking_uri=tracking_uri)
auth_client.create_user(username="user1", password="pw1")
auth_client.create_user(username="user2", password="pw2")

client = MlflowClient(tracking_uri=tracking_uri)
experiment_id = client.create_experiment(name="experiment")

# 设置某个experiment 的权限问题
auth_client.create_experiment_permission(
    experiment_id=experiment_id, username="user2", permission="MANAGE"
)


```





##### mlflow 中的默认配置文件

默认文件配置位置在 mlflow/server/auth/basic_auth.ini



对应的默认的db 存储位置为 mlflow server 启动时的地址，存在一个对应的basic_auth.db 文件内主要是包含expriment permission









