## 修改过去历史记录的commit 

- step1 `git rebase -i HEAD~n` 其中n表示需要修改过去的某个commit
- step2 将对应的commit 的前缀修改为edit ，文件中支持的前缀包括`pick、edit`等
- step3 使用amend 将当前commit 进行更新 `git commit --amend`
- step4 恢复所有的提交记录 `git rebase --continue`











##### 完善对应的jupyter中的配置---修改对应的配置形式

(1)完善对应的jupyter 中的代码配置-----热更新，按照包管理进行python3.10、python3.7、

(2)完成对应的jupyter 中的 各种 包环境的管理

(3)



