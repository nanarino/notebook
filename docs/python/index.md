# HelloWorld

## 常识

熟悉 Windows 操作系统的基本使用：

- 压缩/解压文件
- 安装/卸载软件
- 添加环境变量/服务
- 修改后缀/注册表

熟悉搜索引擎的使用：

- 谷歌
- 必应
- 哔哩哔哩

## 安装环境

传统安装方式: `choco install python` 或安装包

更推荐使用 `uv` 或者 `rye` 来管理python版本

我使用的是：[astral-sh/uv](https://github.com/astral-sh/uv)

## 虚拟环境

如果你使用传统方式安装python，需要激活虚拟环境（以 Windows 例）：

```powershell
PS C:\Users\Administrator>py -m venv .venv

PS C:\Users\Administrator>.\.venv\Scripts\activate

```

在虚拟环境中 `pip` 和 `python` 可以直接使用

## 常见问题

- windows 下安装后:

  ::: warning C:\\Users\\Administrator>python -V
  'python' 不是内部或外部命令，也不是可运行的程序或批处理文件。
  :::

  对于传统安装方式，这是没有设置环境变量，但可以使用 `py` 命令

  对于 `uv` 安装的python这是正常的，可以使用 `uv python list` 获取python路径

  ::: warning C:\\Users\\Administrator>pip -V
  'pip' 不是内部或外部命令，也不是可运行的程序或批处理文件。
  :::

  问题同上，但你也可以使用 `python -m pip` 命令或进入虚拟环境

  ::: warning C:\\Users\\Administrator>pip -V
  You are using pip version 10.0.3, however version 19.1.1 is available.\
  You should consider upgrading via the 'python -m pip install --upgrade pip' command.
  :::

  按照上述命令进行升级 pip

- pip 下载非标准库/第三方模块速度过慢\
  可以使用清华大学镜像

  ```bash
  pip install 第三方模块名字 -i https://pypi.tuna.tsinghua.edu.cn/simple
  ```

______________________________________________________________________

- **多版本**问题

传统方式安装的python，可透过 `py` 命令列出安装过的 python 以及路径：

```powershell
C:\Users\Administrator>py --list-paths
 -V:3.11 *        C:\Users\Administrator\AppData\Local\Programs\Python\Python311\python.exe
 -V:3.9           C:\Users\Administrator\AppData\Local\Programs\Python\Python39\python.exe

```

在项目中直接指定虚拟环境来解决。因为在虚拟环境中原 python 和 pip 的环境变量都无效化了。

`uv` 项目里运行python脚本则相当于每次运行前自动进入虚拟环境，执行完毕自动退出虚拟环境。
