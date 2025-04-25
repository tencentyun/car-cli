# CAR Command Line Tool

- zh [中文](README.md)
- en [English](README.en.md)

# Commands and Parameters

- `car help` : Get help information about the command, including syntax and related parameters.

      car help

- `car create-application` : Create a new application, you need to fill in the application name, which only supports Chinese, letters, numbers, or the connector "-" (within 16 characters), example:

      $ car create-application --name xxx
      ...

- `car create-application-version` : Create a new version of the application, the limit for creating versions under the same application is 5, you need to fill in the application app-id, version name, and application type (zip/rar/7z). If there is a version of "Creating/Normal/CreateFailed", the operation will be rejected. The application version distribution regions and application version update mode are optional. For the regions, please refer to the distribution regions list in the document. The update mode supports full update (FULL), example:

      $ car create-application-version --app-id app-xxx --name xxx --type zip --regions ap-chinese-mainland,ap-tokyo --update-mode FULL
      ...

-- `car upload-application-version-file` : Upload application version file, you need to fill in the application app-id, local path (note the format of windows and linux paths) and application version version-id, please ensure that the app-id and version-id are correct. After the upload is successful, the version name and version package format will be replaced with the name and format of the uploaded file. If you use a URL to upload an application, you only need to enter the app-id and url，example:

      $ car upload-application-version-file --app-id app-xxx --path C:\\data\\xxx.zip --version-id ver-xxx
      $ car upload-application-version-file --app-id app-xxx --path /data/xxx.zip --version-id ver-xxx
      $ car upload-application-version-file --app-id app-xxx --url xxx
      ...

- `car set-version-online` : Publish application version, you need to fill in the application app-id and application version version-id, example:

      $ car set-version-online --app-id app-xxx --version-id ver-xxx
      ...

- `car delete-application-version` : Delete application version, you need to fill in the application app-id and application version version-id. The deletion is asynchronous, and you can check whether the deletion is successful by using "describe-application-version", example:

      $ car delete-application-version --app-id app-xxx --version-id ver-xxx
      ...

- `car describe-application-version` : Display application version list, you need to fill in the application app-id. The command outputs the version id and version status, and the oldest version can be obtained through grep and awk commands, example:

      $ car describe-application-version --app-id app-xxx
      $ car describe-application-version --app-id app-xxx | grep -v "Inuse" | awk '{print $1}' | head -n 1
      ...

# Configuration File

- Replace the SecretId, SecretKey, and AppId of your Tencent Cloud account, **ensure that the executable file and the configuration file are in the same directory when using this tool**

# Application version distribution region
- ap-chinese-mainland     // 中国大陆(mainland default) 
- ap-tokyo                // 东京标准区(international default)
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