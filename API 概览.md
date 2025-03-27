## 云手机 rc PaaS 相关接口

| 接口名称 | 接口功能 | 频率限制（次/秒） |
|-|-|-|
| CancelCloudPhoneMultipleStreamSession | 注销同屏推流会话 | 20 |
| CreateCloudPhoneApp | 创建云手机应用 | 20 |
| CreateCloudPhoneFile | 创建云手机文件 | 20 |
| CreateCloudPhoneInstanceBackup | 创建实例备份 | 20 |
| CreateCloudPhoneInstanceImage | 创建云手机实例镜像 | 20 |
| CreateCloudPhoneInstanceSSH | 创建云手机实例 SSH 连接 | 20 |
| CreateCloudPhoneInstancesAccessToken | 创建云手机实例控制 Token | 20 |
| CreateCloudPhoneInstancesScreenshot | 云手机实例截图 | 20 |
| CreateCloudPhoneInstancesStreamToken | 创建云手机实例推流 Token | 20 |
| CreateCloudPhoneMultipleStreamSession | 创建同屏推流会话 | 20 |
| DeleteCloudPhoneApps | 删除云手机应用 | 20 |
| DeleteCloudPhoneFiles | 删除云手机文件 | 20 |
| DeleteCloudPhoneInstanceImage | 删除云手机实例镜像 | 20 |
| DescribeCloudPhoneApps | 查询云手机应用 | 20 |
| DescribeCloudPhoneBatchTasks | 批量查询云手机任务 | 20 |
| DescribeCloudPhoneFiles | 查询云手机文件 | 20 |
| DescribeCloudPhoneInstanceADBAddr | 查询云手机实例 ADB 连接地址 | 20 |
| DescribeCloudPhoneInstanceApps | 获取云手机实例应用列表 | 20 |
| DescribeCloudPhoneInstanceImages | 查询云手机实例镜像列表 | 20 |
| DescribeCloudPhoneInstanceModels | 获取云手机实例机型列表 | 20 |
| DescribeCloudPhoneInstances | 查询云手机实例列表 | 20 |
| DescribeCloudPhoneMultipleStreamSessionSlaves | 从控设备生效选定详情 | 20 |
| DescribeCloudPhoneMultipleStreamSessions | 查看同屏推流会话列表 | 20 |
| DescribeCloudPhoneSubtasks | 查询云手机子任务 | 20 |
| DescribeCloudPhoneTasks | 查询云手机任务 | 20 |
| DistributeFileToCloudPhoneInstances | 分发文件到云手机实例 | 20 |
| ExecuteCommandAsyncOnCloudPhoneInstances | 以异步方式在云手机实例执行命令 | 20 |
| InstallCloudPhoneInstancesApp | 云手机实例安装应用 | 20 |
| ManageCloudPhoneInstancesApp | 管理云手机实例应用 | 20 |
| ModifyCloudPhoneInstancesBandwidth | 设置云手机实例限速 | 20 |
| ModifyCloudPhoneInstancesImage | 修改云手机实例镜像 | 20 |
| ModifyCloudPhoneInstancesMemory | 设置云手机实例内存 | 20 |
| ModifyCloudPhoneInstancesSkin | 云手机实例换肤 | 20 |
| RebootCloudPhoneHosts | 重启云手机实例宿主机 | 20 |
| RebootCloudPhoneInstances | 重启实例 | 20 |
| RecoverCloudPhoneInstances | 恢复云手机实例出厂设置 | 20 |
| RenewCloudPhoneMultipleStreamSession | 同屏推流会话续期 | 20 |
| ReplaceCloudPhoneInstance | 替换云手机实例 | 20 |
| RestoreCloudPhoneInstances | 还原云手机实例数据 | 20 |
| SelectCloudPhoneMultipleStreamSessionSlaves | 从控设备生效选定 | 20 |
| StopCloudPhoneInstanceStream | 停止云手机实例推流 | 20 |
| SwitchCloudPhoneMultipleStreamSessionMaster | 主屏控制权切换 | 20 |
| SwitchCloudPhoneMultipleStreamSessionSlaves | 从控设备切换 | 20 |

>! 以上给出的接口频率限制维度为`API + 接入地域 + 子账号`，有关限频更多说明参考：[API 频率限制说明](https://cloud.tencent.com/document/product/1278/109059)