# CAR Command Line Tool

- zh [中文](README.md)
- en [English](README.en.md)

# Commands and Parameters

- `car help` : Get help information about the command, including syntax and related parameters.

      car help

- `car create-application` : Create a new application, you need to fill in the application name, which only supports Chinese, letters, numbers, or the connector "-" (within 16 characters), example:

      $ car create-application --name xxx
      ...

- `car create-application-version` : Create a new version of the application, the limit for creating versions under the same application is 5, you need to fill in the application app-id, version name, and application type (zip/rar/7z). If there is a version of "Creating/Normal/CreateFailed", the operation will be rejected, example:

      $ car create-application-version --app-id app-xxx --name xxx --type zip
      ...

- `car upload-application-version-file` : Upload application version file, you need to fill in the application app-id, local path (note the format of windows and linux paths) and application version version-id, please ensure that the app-id and version-id are correct. If the file upload task fails during the creation of the application or the creation of a new version of the application, please execute this command and ensure that the local file path remains unchanged. After the upload is successful, the version name and version package format will be replaced with the name and format of the uploaded file, example:

      $ car upload-application-version-file --app-id app-xxx --path C:\\data\\xxx.zip --version-id ver-xxx
      $ car upload-application-version-file --app-id app-xxx --path /data/xxx.zip --version-id ver-xxx
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
