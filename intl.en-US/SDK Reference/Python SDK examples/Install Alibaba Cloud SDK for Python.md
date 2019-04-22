# Install Alibaba Cloud SDK for Python {#task_dln_nvy_3hb .task}

This topic describes how to build a Python development environment on a local PC so you can run VPC Python SDK examples. Alibaba Cloud SDK for Python supports Python 2.7. To run VPC Python SDK examples, you first need to install the core library of Alibaba Cloud SDK for Python and then install VPC Python SDK.

1.  Install Python. 
    1.  [Download Python 2.7](https://www.python.org/downloads/). 

        Select and download the correct installation package from the download list. The package format should be python-XYZ.msi and XYZ represents the version number.

    2.  Double-click the package to enter the Python installation wizard and use the default configurations directly.
    3.  Set environment variables. Add the python installation path and the directories of the pip program in the Path row. Separate the directories with ; 

        ```
        C:\Python27;C:\Python27\Scripts
        ```

    4.  In the cmd command line, run the `python` command. If the following codes are displayed, you have entered the Python interactive environment and Python has been installed. 

        ```
        
        Python 2.7.15 (v2.7.15:ca079a3ea3, Apr 30 2018, 16:30:26) [MSC v.1500 64 bit (AM
        D64)] on win32
        Type "help", "copyright", "credits" or "license" for more information.
        >>>
        							
        ```

2.  Run the following command to install the core library of Alibaba Cloud SDK for Python. 

    ```
    pip install aliyun-python-sdk-core
    ```

    For more information about Python and PIP, see [Python document](https://docs.python.org/3/).

3.  Run the following command to install VPC SDK. 

    ```
    pip install aliyun-python-sdk-vpc
    ```

4.  Run the following command to use --user to install SDK. 

    ```
    pip install --user aliyun-python-sdk-cms
    ```


