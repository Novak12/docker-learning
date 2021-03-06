## dockerfile

dockerfile是一个文本文件，它可以用来构建docker镜像。

### dockerfile中的命令组合
* From --- 指定base镜像 (required)
* Maintainer --- 设置镜像的作者信息 (optional)
* run --- 在容器中运行指定的命令 (optional)
* add --- 从build context（即当前dockerfile文件所在的目录）中复制文件到到镜像
* copy --- 将文件从build context中复制到镜像中
* expose --- 指定容器中的进程监听某个端口，并将该端口暴露出来
* entrypoint --- 设置容器启动时执行的命令

### dockerfile示例解析
```javascript
# 声明使用的基础镜像
FROM microsoft/dotnet:2.1-aspnetcore-runtime
# 设置工作目录
WORKDIR /dockerapp
# 将本地应用拷贝到 容器 /dockerapp 目录下 
COPY . /dockerapp
# 设置导出端口
EXPOSE 5000/tcp
# 指定应用入口点 NetCore.dll代表的是主程序文件
ENTRYPOINT ["dotnet", "MyDockerApp.dll"]
```


