# 安装Alibaba Cloud SDK for Python {#task_dln_nvy_3hb .task}

本文为您介绍如何在本地搭建可以运行专有网络Python SDK示例的Python开发环境，Alibaba Cloud SDK for Python支持Python 2.7，要运行专有网络的Python SDK示例，您需要安装Alibaba Cloud SDK for Python的核心库和VPC Python SDK。

1.  安装Python。 
    1.  登录[Python下载地址](https://www.python.org/downloads/)。
    2.  下载2.7版本的Python。 

        在下载列表中选择平台安装包，包格式为：python-XYZ.msi 文件 ， XYZ 为您要安装的版本号。

    3.  下载后，双击下载包，进入Python安装向导，使用默认设置即可。
    4.  设置环境变量。 在Path行添加python安装路径和pip命令运行程序所在的目录，目录之间以;分隔。

        ```
        C:\Python27;C:\Python27\Scripts
        ```

    5.  在cmd命令行，执行`python`命令，显示类似如下，进入Python交互式环境，表示Python安装成功。 

        ```
        
        Python 2.7.15 (v2.7.15:ca079a3ea3, Apr 30 2018, 16:30:26) [MSC v.1500 64 bit (AM
        D64)] on win32
        Type "help", "copyright", "credits" or "license" for more information.
        >>>
        							
        ```

2.  执行如下命令，安装Alibaba Cloud SDK for Python核心库。 

    ```
    pip install aliyun-python-sdk-core
    ```

    关于Python及PIP的使用说明，请参见[Python文档](https://docs.python.org/3/)和[PIP文档](https://pip.pypa.io/en/stable/user_guide/)。

3.  执行如下命令，安装VPC SDK。 

    ```
    pip install aliyun-python-sdk-vpc
    ```

4.  执行如下命令，使用--user安装SDK。 

    ```
    pip install --user aliyun-python-sdk-cms
    ```


