1. 动态链接路径错误
	`错误原因现有的动态库中GLIBCXX版本过低，查看当前conda版本是否存在GLIBCXX_3.4.21，设置LD_LIBRARY_PATH为当前环境中conda的位置并修改当前用户的环境变量`
	`step1 vim ~/.bashrc`
	`step2 export LD_LIBRARY_PATH = ${conda}/lib:$LD_LIBRARY_PATH`
	`step3 source ~/.bashrc`
	
2. su - username
切换到对应的username上并使用对应的用户环境


3、关于安装jupyter 上的stander-preview环境
其中主要问题有(1)使用conda 安装fbprophet会出现model not found 的报错，(2)
https://blog.51cto.com/u_15677788/5368619
当前数据中存在报错问题，需要使用

