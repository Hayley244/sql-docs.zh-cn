---
title: 什么是分析平台系统 – 向外缩放数据仓库中的新增功能
description: 请参阅什么是 Microsoft® 分析平台系统承载 MPP SQL Server 并行数据仓库的横向扩展的本地设备中的新增功能。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b4059d9460eec5cd69e6e8b4a2f2ac95af5b3d0e
ms.sourcegitcommit: 2e038db99abef013673ea6b3535b5d9d1285c5ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39400640"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>什么是横向扩展 MPP 数据仓库的分析平台系统中的新增功能
请参阅什么是最新的设备更新为 Microsoft® Analytics Platform System (APS) 中的新增功能。 APS 是承载 MPP SQL Server 并行数据仓库的横向扩展的本地设备。 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"

## <a name="aps-au7"></a>APS AU7
APS 2016 后，才可以升级到 AU7。 以下是 APS AU7 中的新增功能：

### <a name="auto-create-and-auto-update-statistics"></a>自动创建和自动更新统计信息
APS AU7 创建，并默认情况下将自动更新统计信息。 若要更新统计信息设置，管理员可以使用中的新功能切换菜单项[Configuration Manager](appliance-configuration.md#CMTasks)。 [功能开关](appliance-feature-switch.md)控制不符、 自动更新和异步更新统计信息的行为。 此外可以更新使用的统计信息设置[ALTER DATABASE （并行数据仓库）](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)语句。

### <a name="t-sql"></a>T-SQL
选择@var现在支持。 有关详细信息，请参阅 [选择本地变量] （/ sql/t-sql/language-elements/select-local-variable-transact-sql） 

现在支持哈希和 ORDER GROUP 查询提示。 有关详细信息，请参阅 [Hints(Transact-SQL)-查询] （/sql/t-sql/查询/提示-transact-sql 的查询）

### <a name="feature-switch"></a>功能开关
APS AU7 引入了中的功能切换[Configuration Manager](launch-the-configuration-manager.md)。 AutoStatsEnabled 和 DmsProcessStopMessageTimeoutInSeconds 现在都可以由管理员更改的可配置选项。

### <a name="known-issues"></a>已知问题
APS AU7 软件还修复了描述为问题提供 Intel BIOS 更新*推理执行旁道攻击*。 攻击的目标是利用所谓*Spectre 和 Meltdown 漏洞*。 尽管与 APS 一起打包，手动安装 BIOS 更新而不是作为 APS AU7 软件安装的一部分。

Microsoft 建议所有客户，若要安装更新 BIOS。 Microsoft 已在各种环境中的各种 SQL 工作负荷上测量内核虚拟地址隐藏 (KVAS)、 内核页表间接寻址 (KPTI) 和间接分支预测缓解措施 (IBP) 的效果。 度量值上某些工作负荷找到显著下降。 根据结果，建议是测试对性能产生影响的生产环境中部署之前启用 BIOS 更新。 请参阅 SQL Server 指南[此处](https://support.microsoft.com/en-us/help/4073225/guidance-protect-sql-server-against-spectre-meltdown)。

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"

## <a name="aps-2016"></a>APS 2016
本部分针对 APS 2016 AU6 所述的新功能。

### <a name="sql-server-2016"></a>SQL Server 2016

APS AU6 上最新的 SQL Server 2016 版本中，在运行，并使用默认数据库的兼容性级别 130。 SQL Server 2016 支持等新功能：

- 聚集列存储索引的辅助索引。
- Polybase Kerberos。

### <a name="t-sql"></a>T-SQL
APS AU6 支持这些 T-SQL 的兼容性改进。  这些其他语言元素，使其更轻松地从 SQL Server 和其他数据源迁移。 

- [列级 SQL 排序规则][]现在还支持，除了 Windows 排序规则。
- [聚集列存储索引的非聚集索引][]改进搜索聚集列存储索引中的特定值的查询的性能。 
- [选择...到][] 
- [sp_spaceused()][]显示的磁盘空间使用或保留的表或数据库中。
- [宽表][]支持是 SQL Server 2016 相同。 32k 的行大小的上一限制不再存在。 

**数据类型**

- [VARCHAR(MAX)][]， [NVARCHAR(MAX)][]并[VARBINARY （MAX)][]。 这些 LOB 数据类型具有的最大大小为 2 GB。 若要加载这些对象，请使用[bcp Utility][]。 Polybase 和 dwloader 当前不支持这些数据类型。 
- [SYSNAME][]
- [唯一标识符][]
- [NUMERIC][]和 DECIMAL 数据类型。

**开窗函数**

- [ROWS 或 RANGE][] OVER 子句的 SELECT 语句中。
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

**安全函数**

- [CHECKSUM()][]和[BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

**其他函数**

- [NEWID()][]
- [RAND()][]

### <a name="polybasehadoop-enhancements"></a>PolyBase/Hadoop 增强功能

- 与的 Hortonworks HDP 2.4 和 HDP 2.5 兼容性
- Kerberos 支持通过数据库范围凭据
- 使用 Azure 存储 Blob 的凭据支持

### <a name="install-and-upgrade-enhancements"></a>安装和升级增强功能

**企业体系结构更新**到 AP AU6 升级你现有的设备安装最新的固件和驱动程序更新，其中包括安全修补程序。 

新的设备从 HPE 或 DELL 包括所有最新的更新以及：

- 最新生成处理器支持 (Broadwell)
- 更新到采用 DDR4 Dimm
- 改进了的 DIMM 吞吐量

**集成**

- 完全限定域名 (FQDN) 的支持使可能安装到设备的域信任。 
- 若要使用 FQDN，您需要执行完全升级并且选择在升级过程。 

**减少了停机时间**安装或升级到 AP AU6 更快，且需要较少的停机时间比以前的版本。 若要降低停机时间、 安装或升级： 

 - 简化通过使用包含截至 2016 年 6 月的所有更新的映像应用 WSUS 更新
 - 应用安全更新的驱动程序和固件更新
 - 将最新修补程序和设备验证实用程序 (PAV) 置于你的设备这样他们就可以使用无需在下载之后进行安装。

::: moniker-end

<!--
Link references to other articles in this same GitHub repo.

The link format that starts with '/sql/what-ever/my-artlcle' is not appropriate for common links within the same repo (as most of these link are).  The first couple links have been edited to show the proper syntax, but all other links in this article need to be similarly edited.
The proper formats have at least two big advantages.  One big advantage is that the proper formats enable the OPS Build system to detect broken links at Pull Request build time, instead of only later during run time.
-->
[database compatibility level 130]: ../t-sql/statements/alter-database-transact-sql-compatibility-level.md
[列级 SQL 排序规则]: ~/relational-databases/collations/collation-and-unicode-support.md

[聚集列存储索引的非聚集索引]:/sql/t-sql/statements/create-index-transact-sql
[VARCHAR(MAX)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[NVARCHAR(MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY （MAX)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[选择...到]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[宽表]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[bcp Utility]:/sql/tools/bcp-utility
[唯一标识符]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[NUMERIC]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
[ROWS 或 RANGE]:/sql/t-sql/queries/select-over-clause-transact-sql
[FIRST_VALUE]:/sql/t-sql/functions/first-value-transact-sql
[LAST_VALUE]:/sql/t-sql/functions/last-value-transact-sql
[CUME_DIST]:/sql/t-sql/functions/cume-dist-transact-sql
[PERCENT_RANK]:/sql/t-sql/functions/percent-rank-transact-sql
[CHECKSUM()]:/sql/t-sql/functions/checksum-transact-sql
[BINARY_CHECKSUM()]:/sql/t-sql/functions/binary-checksum-transact-sql
[HAS_PERMS_BY_NAME()]:/sql/t-sql/functions/has-perms-by-name-transact-sql
[NEWID()]:/sql/t-sql/functions/newid-transact-sql
[RAND()]:/sql/t-sql/functions/rand-transact-sql


  

  


