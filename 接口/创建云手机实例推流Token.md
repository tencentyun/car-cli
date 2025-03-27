## 1. 接口描述

接口请求域名： gs.tencentcloudapi.com 。

创建云手机实例推流 Token

默认接口请求频率限制：20次/秒。

<div class="rno-api-explorer">
    <div class="rno-api-explorer-inner">
        <div class="rno-api-explorer-hd">
            <div class="rno-api-explorer-title">
                推荐使用 API Explorer
            </div>
            <a href="https://console.cloud.tencent.com/api/explorer?Product=gs&Version=2019-11-18&Action=CreateCloudPhoneInstancesStreamToken" class="rno-api-explorer-btn" hotrep="doc.api.explorerbtn"><i class="rno-icon-explorer"></i>点击调试</a>
        </div>
        <div class="rno-api-explorer-body">
            <div class="rno-api-explorer-cont">
                API Explorer 提供了在线调用、签名验证、SDK 代码生成和快速检索接口等能力。您可查看每次调用的请求内容和返回结果以及自动生成 SDK 调用示例。
            </div>
        </div>
    </div>
</div>

## 2. 输入参数

以下请求参数列表仅列出了接口请求参数和部分公共参数，完整公共参数列表见 [公共请求参数](/document/api/1162/40732)。

| 参数名称 | 必选 | 类型 | 描述 |
|---------|---------|---------|---------|
| Action | 是 | String | [公共参数](/document/api/1162/40732)，本接口取值：CreateCloudPhoneInstancesStreamToken。 |
| Version | 是 | String | [公共参数](/document/api/1162/40732)，本接口取值：2019-11-18。 |
| Region | 否 | String | [公共参数](/document/api/1162/40732)，此参数为可选参数。 |
| InstanceIds.N | 是 | Array of String | <strong><font color="blue">此参数仅产品内部展示。</font></strong>实例 ID 列表<br/>示例值：[RK5838P1262207595_0983c1f6-1967-466c-b4fe- 8f8a7e761aaa] |
| DeviceId | 是 | String | <strong><font color="blue">此参数仅产品内部展示。</font></strong>设备 ID<br/>示例值：4297f44b13955235245b2497399d7a93 |
| RenewalTime | 否 | Integer | <strong><font color="blue">此参数仅产品内部展示。</font></strong>有效时长(小时)，默认2<br/>示例值：2 |

## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| Tokens | Array of [CloudPhoneStreamToken](/document/api/1162/40743#CloudPhoneStreamToken) | <strong><font color="blue">此参数仅产品内部展示。</font></strong>推流 Token 列表|
| RequestId | String | 唯一请求 ID，由服务端生成，每次请求都会返回（若请求因其他原因未能抵达服务端，则该次请求不会获得 RequestId）。定位问题时需要提供该次请求的 RequestId。|

## 4. 示例

### 示例1 创建云手机实例推流 Token

创建云手机实例推流 Token

#### 输入示例

```
POST / HTTP/1.1
Host: gs.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: CreateCloudPhoneInstancesStreamToken
<公共请求参数>

{
    "InstanceIds": [
        "RK8S37P1402445261_3f86d6f5-2db9-4903-a70d-889987c9b2ac",
        "RK8S37P1402445261_95de5774-0f9f-4cc2-aa67-58d41378d209"
    ],
    "DeviceId": "dc1079f85676"
}
```

#### 输出示例

```json
{
    "Response": {
        "RequestId": "c425d4ea-e655-4675-9057-7d31365fcd26",
        "Tokens": [
            {
                "CoturnServers": [
                    {
                        "Addr": "101.67.33.168:3478",
                        "ISP": 2
                    },
                    {
                        "Addr": "183.247.255.168:3478",
                        "ISP": 1
                    },
                    {
                        "Addr": "pstreama-pass-hzc.phone.tcloud.com:3478",
                        "ISP": 4
                    }
                ],
                "DeviceId": "dc1079f85676",
                "ExpireTime": "2025-01-08 12:32:07",
                "InstanceId": "RK8S37P1402445261_3f86d6f5-2db9-4903-a70d-889987c9b2ac",
                "SignalServer": {
                    "TCPAddr": "nats://pstreama-pass-hzc.phone.tcloud.com:4432",
                    "WSAddr": "nats://pstreama-pass-hzc.phone.tcloud.com:44912/nats",
                    "WSSAddr": "wss://pstreama-pass-hzc.phone.tcloud.com:44913/nats"
                },
                "Token": "OWExYzA1MjI3ODlmNGY0ZiZSSzhTMzdQMTQwMjQ0NTI2MV8zZjg2ZDZmNS0yZGI5LTQ5MDMtYTcwZC04ODk5ODdjOWIyYWMmZGMxMDc5Zjg1Njc2"
            },
            {
                "CoturnServers": [
                    {
                        "Addr": "101.67.33.168:3478",
                        "ISP": 2
                    },
                    {
                        "Addr": "183.247.255.168:3478",
                        "ISP": 1
                    },
                    {
                        "Addr": "pstreama-pass-hzc.phone.tcloud.com:3478",
                        "ISP": 4
                    }
                ],
                "DeviceId": "dc1079f85676",
                "ExpireTime": "2025-01-08 12:32:07",
                "InstanceId": "RK8S37P1402445261_95de5774-0f9f-4cc2-aa67-58d41378d209",
                "SignalServer": {
                    "TCPAddr": "nats://pstreama-pass-hzc.phone.tcloud.com:4432",
                    "WSAddr": "nats://pstreama-pass-hzc.phone.tcloud.com:44912/nats",
                    "WSSAddr": "wss://pstreama-pass-hzc.phone.tcloud.com:44913/nats"
                },
                "Token": "OTdjYTRiYTEzYWQ5NGZmNyZSSzhTMzdQMTQwMjQ0NTI2MV85NWRlNTc3NC0wZjlmLTRjYzItYWE2Ny01OGQ0MTM3OGQyMDkmZGMxMDc5Zjg1Njc2"
            }
        ]
    }
}
```


## 5. 开发者资源

### 腾讯云 API 平台

[腾讯云 API 平台](https://cloud.tencent.com/api) 是综合 API 文档、错误码、API Explorer 及 SDK 等资源的统一查询平台，方便您从同一入口查询及使用腾讯云提供的所有 API 服务。

### API Inspector

用户可通过 [API Inspector](https://cloud.tencent.com/document/product/1278/49361) 查看控制台每一步操作关联的 API 调用情况，并自动生成各语言版本的 API 代码，也可前往 [API Explorer](https://cloud.tencent.com/document/product/1278/46697) 进行在线调试。

### SDK

云 API 3.0 提供了配套的开发工具集（SDK），支持多种编程语言，能更方便的调用 API。
* Tencent Cloud SDK 3.0 for Python: [GitHub](https://github.com/TencentCloud/tencentcloud-sdk-python/blob/master/tencentcloud/gs/v20191118/gs_client.py) [Gitee](https://gitee.com/TencentCloud/tencentcloud-sdk-python/blob/master/tencentcloud/gs/v20191118/gs_client.py)
* Tencent Cloud SDK 3.0 for Java: [GitHub](https://github.com/TencentCloud/tencentcloud-sdk-java/blob/master/src/main/java/com/tencentcloudapi/gs/v20191118/GsClient.java) [Gitee](https://gitee.com/TencentCloud/tencentcloud-sdk-java/blob/master/src/main/java/com/tencentcloudapi/gs/v20191118/GsClient.java)
* Tencent Cloud SDK 3.0 for PHP: [GitHub](https://github.com/TencentCloud/tencentcloud-sdk-php/blob/master/src/TencentCloud/Gs/V20191118/GsClient.php) [Gitee](https://gitee.com/TencentCloud/tencentcloud-sdk-php/blob/master/src/TencentCloud/Gs/V20191118/GsClient.php)
* Tencent Cloud SDK 3.0 for Go: [GitHub](https://github.com/TencentCloud/tencentcloud-sdk-go/blob/master/tencentcloud/gs/v20191118/client.go) [Gitee](https://gitee.com/TencentCloud/tencentcloud-sdk-go/blob/master/tencentcloud/gs/v20191118/client.go)
* Tencent Cloud SDK 3.0 for Node.js: [GitHub](https://github.com/TencentCloud/tencentcloud-sdk-nodejs/blob/master/src/services/gs/v20191118/gs_client.ts) [Gitee](https://gitee.com/TencentCloud/tencentcloud-sdk-nodejs/blob/master/src/services/gs/v20191118/gs_client.ts)
* Tencent Cloud SDK 3.0 for .NET: [GitHub](https://github.com/TencentCloud/tencentcloud-sdk-dotnet/blob/master/TencentCloud/Gs/V20191118/GsClient.cs) [Gitee](https://gitee.com/TencentCloud/tencentcloud-sdk-dotnet/blob/master/TencentCloud/Gs/V20191118/GsClient.cs)
* Tencent Cloud SDK 3.0 for C++: [GitHub](https://github.com/TencentCloud/tencentcloud-sdk-cpp/blob/master/gs/src/v20191118/GsClient.cpp) [Gitee](https://gitee.com/TencentCloud/tencentcloud-sdk-cpp/blob/master/gs/src/v20191118/GsClient.cpp)
* Tencent Cloud SDK 3.0 for Ruby: [GitHub](https://github.com/TencentCloud/tencentcloud-sdk-ruby/blob/master/tencentcloud-sdk-gs/lib/v20191118/client.rb) [Gitee](https://gitee.com/TencentCloud/tencentcloud-sdk-ruby/blob/master/tencentcloud-sdk-gs/lib/v20191118/client.rb)

### 命令行工具

* [Tencent Cloud CLI 3.0](https://cloud.tencent.com/document/product/440/6176)

## 6. 错误码

以下仅列出了接口业务逻辑相关的错误码，其他错误码详见 [公共错误码](/document/api/1162/40744#.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81)。

| 错误码 | 描述 |
|---------|---------|
| FailedOperation | 操作失败。 |
| InternalError | 内部错误。 |
| InvalidParameter | 参数错误。 |
| InvalidParameterValue | 参数取值错误。 |
