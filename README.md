# 应用命令行工具

- zh [中文](README.md)
- en [English](README.en.md)

# 命令及参数

- `car help` : 求助说明命令，含有命令的语法与参数等相关信息

      car help

- `car create-application` : 新建应用，需填写应用名称 `name`，只支持中文、字母、数字或连接符 `-`（16 字符以内）。可通过 `--app-type` 指定应用类型；不传时默认创建桌面端 `Application3D`，支持 `Application3D`、`ApplicationXR`、`ApplicationAPK`、`ApplicationWeb`，移动端应用请传 `ApplicationAPK`。注意：`--app-type` 表示应用类型，区别于 `create-application-version --type` 的包文件类型。样例：

      $ car create-application --name xxx
      $ car create-application --name mobile-xxx --app-type ApplicationAPK
      ...

- `car create-application-version` : 创建应用新版本，同一应用下版本创建数量上限为 5 个，需填写应用 `app-id`、版本命名和应用格式。桌面端支持 `zip`/`rar`/`7z`，移动端支持 `apk`/`xapk`/`zip`，最终格式合法性由后端根据应用实际类型校验。若有"创建中/待发布/创建失败"的版本，则操作会被拒绝。`--regions` 和 `--update-mode` 仅桌面端生效：桌面端可按需传入分发地区和更新方式，地区请参考文档中分发地区列表，更新方式支持全量更新 `FULL`；移动端不需要传这两个参数。样例：

      $ car create-application-version --app-id app-xxx --name xxx --type zip --regions ap-chinese-mainland,ap-tokyo --update-mode FULL
      $ car create-application-version --app-id app-xxx --name mobile-v1 --type apk
      ...

- `car upload-application-version-file` : 上传应用版本文件，需填写应用 `app-id`、本地路径（注意 Windows 和 Linux 路径格式）和应用版本 `version-id`，请确保 `app-id` 和 `version-id` 正确，上传成功后，版本名称和包格式会被替换为所上传文件的名字和格式；若使用 URL 上传应用，则只需输入 `app-id` 和 `url`。样例：

      $ car upload-application-version-file --app-id app-xxx --path C:\data\xxx.zip --version-id ver-xxx
      $ car upload-application-version-file --app-id app-xxx --path /data/xxx.apk --version-id ver-xxx
      $ car upload-application-version-file --app-id app-xxx --url xxx
      ...

- `car set-version-online` : 发布应用版本，需填写应用 `app-id` 和应用版本 `version-id`。桌面端发布前会校验启动路径，移动端会自动跳过该校验。样例：

      $ car set-version-online --app-id app-xxx --version-id ver-xxx
      ...

- `car delete-application-version` : 删除应用版本，需填写应用 `app-id` 和应用版本 `version-id`，异步删除，可通过查询应用版本列表查看是否删除成功。样例：

      $ car delete-application-version --app-id app-xxx --version-id ver-xxx
      ...

- `car describe-application-version` : 展示应用版本列表，需填写应用 `app-id`，输出版本 id 和版本状态，可通过 grep 和 awk 命令获取最旧的版本。样例：

      $ car describe-application-version --app-id app-xxx
      $ car describe-application-version --app-id app-xxx | grep -v "Inuse" | awk '{print $1}' | head -n 1
      ...

# 配置文件

- 将腾讯云账号的 `SecretId`、`SecretKey` 以及 `AppId` 替换，**使用时保证可执行文件和配置文件在相同目录下**。

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
