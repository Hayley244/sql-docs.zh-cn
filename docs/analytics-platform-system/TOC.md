# 关于此版本
## [新增功能](whats-new-analytics-platform-system.md)
## [新的和已更新的项目](new-updated-analytics-platform-system.md)

# 体系结构
## [并行数据仓库概述](parallel-data-warehouse-overview.md)
## [硬件组件](hardware-components.md)
## [硬件配置](hardware-configurations.md)
## [处理容量和存储容量](processing-and-storage-capacity-planning.md)
## [高可用性](high-availability.md)

# 备份和加载硬件
## [概述](backup-and-loading-hardware.md)
## [获取和配置加载服务器](acquire-and-configure-loading-server.md)
## [加载服务器容量计划工作表](loading-server-capacity-planning-worksheet.md)
## [获取和配置备份服务器](acquire-and-configure-backup-server.md)
## [备份服务器容量计划工作表](backup-capacity-planning-worksheet.md)
## [配置 InfiniBand 网络适配器](configure-infiniband-network-adapters.md)

# Query
## [监视活动查询](monitoring-active-queries.md)

# 加载
## [概述](load-overview.md)
## [创建临时数据库](staging-database.md)
## [使用 Integration Services 加载](load-with-ssis.md)
## [创建使用 PDW 目标适配器的 Integration Services 脚本任务](create-ssis-script-task-using-pdw-destination-adapter.md)
## [适用于 dwloader 的数据类型转换规则](dwloader-data-type-conversion-rules.md)
## [使用 INSERT 加载数据](load-with-insert.md)
## [dwloader 命令行加载工具](dwloader.md)
## [监视加载](monitor-loads.md)

# 数据库管理
## 备份和还原
### [概述](backup-and-restore-overview.md)
### [还原 TDE 保护的数据库](restore-database-protected-by-tde.md)
## [PDW 权限](pdw-permissions.md)
### [授予权限](grant-permissions.md)
## [错误消息](error-messages.md)
## [锁定行为](locking-behavior.md)
## [远程表副本](remote-table-copy.md)
### [配置外部 Windows 系统以使用 InfiniBand 接收远程表副本](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)
### [配置外部 SMP SQL Server 以接收远程表副本](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)
### [为远程表副本配置 SQL Server PDW](configure-sql-server-pdw-for-remote-table-copies.md)
## [系统数据库](system-databases.md)
### [保留数据库名称](reserved-database-names.md)
### [tempdb 数据库](tempdb-database.md)
### [master 数据库](master-database.md)
## [用户会话](user-sessions.md)
## [工作负荷管理](workload-management.md)
### [工作负荷管理任务](workload-management-tasks.md)

# 安全性
## [透明数据加密](transparent-data-encryption.md)
## [预配证书](provision-certificate.md)

# [设备管理任务](appliance-management-tasks.md)
## [设备安装和配置概述](appliance-installation-and-configuration-overview.md)
### [从 IHV 中获取的信息](information-to-obtain-from-your-ihv.md)
### [硬件安装](hardware-installation.md)
## [连接到设备节点](connect-to-appliance-nodes.md)
## [防病毒软件](antivirus-software.md)
## [设备配置](appliance-configuration.md)
### [PDW 和设备结构物理组件](pdw-and-appliance-fabric-physical-components.md)
### [启动 Configuration Manager](launch-the-configuration-manager.md)
### [设备拓扑](appliance-topology.md)
### [密码重置](password-reset.md)
### [设备时区配置](appliance-time-zone-configuration.md)
### [设备网络网络](appliance-network-configuration.md)
### [PDW 拓扑](pdw-topology.md)
### [PDW 证书预配](pdw-certificate-provisioning.md)
### [PDW 防火墙配置](pdw-firewall-configuration.md)
### [PDW 服务状态](pdw-services-status.md)
### [即时文件初始化配置](instant-file-initialization-configuration.md)
### [还原 master 数据库](restore-the-master-database.md)
### [在目录服务还原模式 (DSRM) 中设置用于登录到 AD 节点的管理员密码](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md)
### [配置 Windows Server Update Services](configure-windows-server-update-services-wsus.md)
### [配置到外部数据的 PolyBase 连接](configure-polybase-connectivity-to-external-data.md)
### [使用 DNS 转发器来解析非设备 DNS 名称](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)
### [创建 APS 域管理员](create-an-aps-domain-administrator-aps.md)
### [向 Microsoft 发送遥测反馈](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)
## [软件维护服务](software-servicing.md)
### [下载和应用 Microsoft 更新](download-and-apply-microsoft-updates.md)
### [卸载 Microsoft 更新](uninstall-microsoft-updates.md)
### [应用 Analytics Platform System 修补程序](apply-analytics-platform-system-hotfixes.md)
### [卸载 Analytics Platform System 修补程序](uninstall-analytics-platform-system-hotfixes.md)
## [打开或关闭 APS 设备](power-the-aps-appliance-on-or-off.md)
## [设备监视](appliance-monitoring.md)
### [使用管理控制台监视设备](monitor-the-appliance-by-using-the-admin-console.md)
### [使用系统视图监视设备](monitor-the-appliance-by-using-system-views.md)
### [使用 System Center Operations Manager 监视设备](monitor-the-appliance-by-using-system-center-operations-manager.md)
#### [安装 SCOM 管理包](install-the-scom-management-packs.md)
#### [为 PDW 导入 SCOM 管理包](import-the-scom-management-pack-for-pdw.md)
#### [配置 SCOM 以监视 Analytics Platform System](configure-scom-to-monitor-analytics-platform-system.md)
### [监视设备健康状况](monitor-appliance-health-state.md)
### [跟踪设备警报](track-appliance-alerts.md)
### [查看容量利用率](view-capacity-utilization.md)
### [确定轮询频率](determine-polling-frequency.md)
### [确定哪个群集节点失败](determine-which-cluster-node-failed.md)
### [了解管理控制台警报](understanding-admin-console-alerts.md)

# 参考
## [T-SQL 语言元素](tsql-language-elements.md)
## [T-SQL 语句](tsql-statements.md)
## [T-SQL 系统视图](tsql-system-views.md) 