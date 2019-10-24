vim中进行程序跳转
===
环境安装
---
* 在Ubuntu中安装安装ctags  
>sudo apt-get install exuberant-ctags
* 生成tags文件  
>方法1：进入工程的根目录，在命令行执行ctags -R，就在工程的根目录下生成了tags文件  
>方法2：vim打开工程的根目录，输入冒号（：）后，输入!ctags -R，并回车，就在根目录的同级目录生成了tags文件
* 配置vim的config文件
>在用户的HOME目录下创建.vimrc,输入下列内容
```
set tags+=tags文件的绝对路径
```
* 代码跳转
>把光标停在代码的函数上，按Ctrl-]就可以跳转到代码的实现处<br>
>按Ctrl-t就可以跳回去
* 参考文档
>[Vim技能修炼教程(10) - 代码跳转](https://yq.aliyun.com/articles/124415)
