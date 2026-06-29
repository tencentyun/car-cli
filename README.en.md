# CAR Command Line Tool

- zh [中文](README.md)
- en [English](README.en.md)

# Commands and Parameters

- `car help` : Get help information about the command, including syntax and related parameters.

      car help

- `car create-application` : Create a new application. The application name only supports Chinese characters, letters, numbers, or hyphens `-` within 16 characters. Use `--app-type` to specify the application type. If omitted, the default is desktop `Application3D`. Supported values are `Application3D`, `ApplicationXR`, `ApplicationAPK`, and `ApplicationWeb`; use `ApplicationAPK` for mobile applications. Note that `--app-type` means application type, while `create-application-version --type` means package file type. Examples:

      $ car create-application --name xxx
      $ car create-application --name mobile-xxx --app-type ApplicationAPK
      ...

- `car create-application-version` : Create a new version for an application. The number of versions under the same application cannot exceed 5. You need to provide the application `app-id`, version name, and package type. Desktop applications support `zip`/`rar`/`7z`; mobile applications support `apk`/`xapk`/`zip`. The backend validates the package type against the actual application type. If there is a version in `Creating`/`Normal`/`CreateFailed`, the operation will be rejected. `--regions` and `--update-mode` only take effect for desktop applications: pass them when desktop distribution regions or update mode are needed; mobile applications do not need these two parameters. Example:

      $ car create-application-version --app-id app-xxx --name xxx --type zip --regions ap-chinese-mainland,ap-tokyo --update-mode FULL
      $ car create-application-version --app-id app-xxx --name mobile-v1 --type apk
      ...

- `car upload-application-version-file` : Upload an application version file. Provide the application `app-id`, local path, and application `version-id` for local upload. Make sure the `app-id` and `version-id` are correct. After upload succeeds, the version name and package type will be replaced by the uploaded file name and type. For URL upload, only `app-id` and `url` are required. Examples:

      $ car upload-application-version-file --app-id app-xxx --path C:\data\xxx.zip --version-id ver-xxx
      $ car upload-application-version-file --app-id app-xxx --path /data/xxx.apk --version-id ver-xxx
      $ car upload-application-version-file --app-id app-xxx --url xxx
      ...

- `car set-version-online` : Publish an application version. Provide the application `app-id` and `version-id`. Desktop applications keep launch path validation; mobile applications skip that validation automatically. Example:

      $ car set-version-online --app-id app-xxx --version-id ver-xxx
      ...

- `car delete-application-version` : Delete an application version. Provide the application `app-id` and `version-id`. Deletion is asynchronous; use `describe-application-version` to check the result. Example:

      $ car delete-application-version --app-id app-xxx --version-id ver-xxx
      ...

- `car describe-application-version` : Display application version list. Provide the application `app-id`. The command outputs version id and status. Example:

      $ car describe-application-version --app-id app-xxx
      $ car describe-application-version --app-id app-xxx | grep -v "Inuse" | awk '{print $1}' | head -n 1
      ...

# Configuration File

- Replace the `SecretId`, `SecretKey`, and `AppId` of your Tencent Cloud account. **Ensure that the executable file and the configuration file are in the same directory when using this tool.**

# Application Version Distribution Regions

- ap-chinese-mainland     // Chinese mainland (mainland default)
- ap-tokyo                // Tokyo standard region (international default)
- ap-tokyo-fusion         // Tokyo fusion region
- ap-seoul                // Seoul standard region
- ap-seoul-fusion         // Seoul fusion region
- ap-singapore            // Singapore standard region
- ap-singapore-fusion     // Singapore fusion region
- eu-frankfurt            // Frankfurt standard region
- eu-frankfurt-fusion     // Frankfurt fusion region
- na-north-america        // North America standard region
- na-north-america-fusion // North America fusion region
- me-middle-east-fusion   // Middle East fusion region
- sa-south-america-fusion // South America fusion region
