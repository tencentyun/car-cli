# 应用命令行工具

- zh [中文](README.md)
- en [English](README.en.md)

# 命令及参数

- `car help` : 求助说明命令，含有命令的语法与参数等相关信息

      car help

- `car create-application` : 新建应用，需填写应用的名称name，只支持中文、字母、数字或连接符"-"（16字符以内），样例：

      $ car create-application --name xxx
      ...

- `car create-application-version` : 创建应用新版本，同一应用下版本创建数量上限为5个，需填写应用app-id，版本命名和应用格式(zip/rar/7z), 若有"创建中/待发布/创建失败"的版本，则操作会被拒绝，样例：

      $ car create-application-version --app-id app-xxx --name xxx --type zip
      ...

- `car upload-application-version-file` : 上传应用版本文件，需填写应用app-id、本地路径(注意windows和linux路径格式)和应用版本version-id，请确保app-id和version-id正确，若创建应用或创建应用新版本中，上传文件任务失败，请执行本命令，同时确保本地文件路径不变，上传成功后，版本名称和包格式会被替换为所上传文件的名字和格式，样例：

      $ car upload-application-version-file --app-id app-xxx --path C:\\data\\xxx.zip --version-id ver-xxx
      $ car upload-application-version-file --app-id app-xxx --path /data/xxx.zip --version-id ver-xxx
      ...

- `car set-version-online` : 发布应用版本，需填写应用app-id和应用版本version-id，样例：

      $ car set-version-online --app-id app-xxx --version-id ver-xxx
      ...

- `car delete-application-version` : 删除应用版本，需填写应用app-id和应用版本version-id，异步删除，可通过查询应用版本列表查看是否删除成功，样例：

      $ car delete-application-version --app-id app-xxx --version-id ver-xxx
      ...

- `car describe-application-version` : 展示应用版本列表，需填写应用app-id，输出版本id和版本状态，可通过grep和awk命令获取最旧的版本，样例：

      $ car describe-application-version --app-id app-xxx
      $ car describe-application-version --app-id app-xxx | grep -v "Inuse" | awk '{print $1}' | head -n 1
      ...

# 配置文件

- 将腾讯云账号的SecretId、ScretKey以及AppId替换，**使用时保证可执行文件和配置文件在相同目录下**
