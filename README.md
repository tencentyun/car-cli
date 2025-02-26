# 应用命令行工具

- zh [中文](README.md)
- en [English](README.en.md)

# 命令及参数

- `car help` : 求助说明命令，含有命令的语法与参数等相关信息

      car help

- `car create-application` : 新建应用，需填写应用的名称name，只支持中文、字母、数字或连接符"-"（16字符以内），样例：

      $ car create-application --name xxx
      ...

- `car create-application-version` : 创建应用新版本，同一应用下版本创建数量上限为5个，需填写应用app-id，版本命名和应用格式(zip/rar/7z), 若有"创建中/待发布/创建失败"的版本，则操作会被拒绝。应用版本分发地区以及应用版本更新方式为可选项，地区请参考文档中分发地区列表，更新方式支持全量更新(FULL)和增量更新(INCREMENT)，融合区不支持增量更新，样例：

      $ car create-application-version --app-id app-xxx --name xxx --type zip --regions ap-chinese-mainland,ap-tokyo --update-mode FULL
      ...

- `car upload-application-version-file` : 上传应用版本文件，需填写应用app-id、本地路径(注意windows和linux路径格式)和应用版本version-id，请确保app-id和version-id正确，上传成功后，版本名称和包格式会被替换为所上传文件的名字和格式，样例：

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

# 版本分发地区
- ap-chinese-mainland     // 中国大陆 （大陆默认）
- ap-tokyo                // 东京标准区 （国际默认）
- ap-tokyo-fusion         // 东京融合区
- ap-seoul                // 首尔标准区
- ap-seoul-fusion         // 首尔融合区
- ap-singapore            // 新加坡标准区
- ap-singapore-fusion     // 新加坡融合区
- eu-frankfurt            // 法兰克福标准区
- eu-frankfurt-fusion     // 法兰克福融合区
- na-north-america        // 北美标准区
- na-north-america-fusion // 北美融合区
- me-middle-east-fusion   // 中东融合区
- sa-south-america-fusion // 南美融合区