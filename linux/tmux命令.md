# tmux的命令

## 安装命令
` yum install tmux`

## 操作命令

创建tmux
` tmux new -s <name>`

查看当前存在的session
` tmux ls`

进入指定的session
` tmux a -t <name>`

进入最近一个使用的session
` tmux a`

退出session(不杀死)
`方法一:直接关闭窗口`
`方法二: control+b  再按d`