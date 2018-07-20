---
title: 创建使用新建会话对话框中的扩展的事件会话 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SSMS.XEDISPLAY.GROUPING.F1
- SQL12.SSMS.XEDISPLAY.AGGREGATION.F1
- SQL12.SSMS.XEDISPLAY.NEWMERGEDCOLUMN.F1
- SQL12.SSMS.XENEWEVENTSESSION.GENERAL.F1
- SQL12.SSMS.XEDISPLAY.EDITCOLUMNS.F1
- SQL12.SSMS.XEDISPLAY.FILTERS.F1
helpviewer_keywords:
- Extended Events Dialog Box
ms.assetid: 6b2244bc-df6a-4b0a-990e-ddd8d42f7907
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 92fc98d32c8fe021af008dcd1058f6e43fc2fdd0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306247"
---
# <a name="create-an-extended-events-session-using-the-new-session-dialog"></a>使用“新建会话”对话框创建扩展事件会话
  通过“新建会话”对话框，您可以定义捕获、显示和分析数据的扩展事件会话。 “新建会话”对话框公开所有扩展事件功能。  
  
 通过 [新建会话向导](../ssms/object/object-explorer.md) ，您也可以定义扩展事件会话，并且支持大多数扩展事件功能。  
  
## <a name="before-you-begin"></a>开始之前  
 若要打开“新建会话”对话框，请在对象资源管理器中，展开 **“管理”** 节点，然后展开 **“扩展事件”**。 右键单击 **“会话”**，然后单击 **“新建会话”**。  
  
##  <a name="BeforeYouBegin"></a> 权限  
 若要创建扩展事件会话，您必须具有 ALTER ANY EVENT SESSION 权限。  
  
## <a name="to-create-an-extended-events-session-using-the-new-session-dialog"></a>使用“新建会话”对话框创建扩展事件会话  
 使用 **“常规”** 页可以选择模板和计划事件会话的时间。  
  
#### <a name="to-select-a-template-and-schedule-an-event-session"></a>选择模板和计划事件会话的时间  
  
1.  在对象资源管理器中，依次展开 **“管理”** 节点和 **“扩展事件”**。 右键单击 **“会话”**，然后单击 **“新建会话”**。  
  
2.  在 **“常规”** 页上的 **“会话名称”** 框中，键入事件会话的有意义的名称。  
  
3.  在“模板”框中，从下拉列表中选择要使用的模板。  
  
     你可以从为常见问题设计的一组预先配置的模板中进行选择，也可以选择“从文件”以便使用从以前的会话定义导出的模板文件。 请注意，您还可以在应用模板后更改会话的配置。  
  
4.  在 **“计划”** 部分中，如果您想要在启动服务器时启动会话，则选中 **“在服务器启动时启动事件会话”** 复选框。  
  
     如果您想要在创建会话后启动会话，则选中 **“在会话创建后立即启动事件会话”** 复选框。  
  
5.  若要查看您的事件会话的实时数据，请单击 **“在捕获时查看屏幕上的实时数据”**。 实时数据将在创建会话后立即开始显示跟踪。  
  
6.  在 **“因果关系跟踪”** 部分，选中 **“跟踪事件彼此相关的方式”** 复选框，以便跟踪跨多个任务的工作。  
  
     有关因果关系跟踪的详细信息，请参阅 [SQL Server Extended Events Sessions](../relational-databases/extended-events/sql-server-extended-events-sessions.md) 主题中的“会话内容和特征”。  
  
     若要向您的会话添加事件，请在 **“选择页”** 部分中单击 **“事件”**。  
  
    > [!NOTE]  
    >  在完成事件会话的创建前，不要单击“确定”。  
  
 使用 **“事件”** 页可以查找和添加要为会话捕获的事件。  
  
#### <a name="to-add-events-to-a-session"></a>向会话添加事件  
  
1.  在“新建会话”对话框的 **“选择页”** 部分中，选择 **“事件”**。  
  
2.  在“事件”页上，单击“选择”（如果已处于“选择要捕获的事件”屏幕中，则“选择”按钮将灰显）。  
  
     您可以通过在 **“事件库”** 框中输入要搜索的文本，搜索表中的任何词语。 例如，如果你想要查找 **lock_acquired** 事件，则可以输入 **lock** 或 **lock acquire**。  
  
3.  在“事件库”部分中，从下拉列表选择你搜索要捕获的事件的方式。 例如，您可以搜索事件名称或者事件名称及其说明。 在 **“搜索”** 框中输入您的搜索条件。  
  
    > [!NOTE]  
    >  默认情况下将隐藏来自 **“调试”** 渠道的事件。 若要显示调试事件，请从“渠道”下拉列表中选择“调试”。  
  
     所选事件的详细信息将出现在 **“事件库”** 下的“详细信息”窗格中。  
  
     这些事件按名称的字母顺序排序。 您可以通过单击相应的列标题，按其他事件详细信息进行排序。 例如，您可以按 **“类别”** 或 **“渠道”** 列排序。  
  
4.  选择你要捕获的事件，然后单击右箭头以便将这些事件移到“所选事件”部分中。  
  
    > [!NOTE]  
    >  你可以通过使用 CTRL 或 SHIFT 键，从“事件库”中同时选择多个事件。  
  
     若要配置所选事件，请单击 **“配置”**。  
  
    > [!NOTE]  
    >  在完成事件会话的创建前，不要单击“确定”。  
  
 使用 **“数据存储”** 页可以向事件会话添加目标。 目标存储事件数据，并且可以执行各种操作，例如将事件保存到文件以便以后查看和聚合会话的事件数据。 有关扩展事件目标的详细信息，请参阅 [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md)。  
  
 下面是可用于扩展事件会话的目标：  
  
-   **etw_classic_sync_target**。 用于将 SQL Server 事件与 Windows 操作系统或应用程序事件数据相关联。  
  
-   **event_counter**。 计算在启动扩展事件会话后发生的所有指定事件的数目。 用于获取有关工作负荷特征的信息，不必因进行完整的事件收集而增加系统开销。  
  
-   **event_file**。 用于将事件会话输出从完整内存缓冲区写入磁盘。  
  
-   **histogram**。 用于基于指定的事件列或操作，对指定事件发生的次数进行计数。  
  
-   **pair_matching**。 用于确定指定的成对的事件何时未成对发生。  
  
-   **ring_buffer**。 用于在先进先出 (FIFO) 的基础上或按事件 FIFO 的基础上将事件数据保存在内存中。  
  
#### <a name="to-configure-global-fields-for-a-session"></a>为会话配置全局字段  
  
1.  在 **“事件”** 页上，在选择要添加到事件会话的事件后，单击 **“配置”**。  
  
     在您单击 **“配置”** 后， **“事件库”** 部分将折叠，并且 **“所选事件”** 部分将滑动到页面的左侧。 您用于配置事件的 **“事件配置选项”** 部分将出现在页面的右侧。 使用此页上的选项卡可为您的事件会话配置操作。  
  
2.  在 **“全局字段”** 选项卡上，选择您要应用于所选事件的字段。  
  
     可为每个事件选择多个字段。  
  
    > [!NOTE]  
    >  如果已选择的两个事件配置有不同的操作，则扩展事件将显示部分检查的操作。 若要迅速找到已启用的操作，您可以通过单击复选框上方的列标题，按启用/禁用状态进行排序。  
  
3.  在“筛选器”选项卡上，应用筛选器（也称作谓词）可限制要捕获的事件。  
  
     如果某个筛选器应用于所选事件，则复选标记将出现在列中。  
  
    > [!NOTE]  
    >  您可以通过使用 CTRL 或 SHIFT 键，选择要将筛选器应用于的多个事件。 但是，只有公共事件字段才会出现以便进行配置。 如果两个所选事件已具有为其配置的不同筛选器，则筛选器将不出现。 重新配置筛选器将覆盖现有的筛选器值。  
  
    > [!NOTE]  
    >  在您为筛选器配置组子句时，在保存结果后多余的括号将从筛选器中删除。 例如，如果您创建一个筛选器分组 **Clause 1** 和 **Clause 2**，则括号会将这两个子句括起来。 在您保存筛选器后，多余的括号将被删除。 删除这些括号不会影响筛选器逻辑。  
  
4.  在 **“事件字段”** 选项卡上，选择您要应用于所选事件的事件字段。  
  
     事件包含始终收集的许多字段，这些字段显示在 **“事件字段”** 选项卡中并且没有复选框。 一个事件还可以具有默认不收集的可选字段（例如，不选择占用大量资源的可选字段）。 可选字段也在 **“事件字段”** 选项卡中列出并且具有复选框。 若要收集某一可选字段，请选中该可选字段前面的复选框。  
  
    > [!NOTE]  
    >  事件字段选项将显示在跟踪结果中捕获和查看的字段。 （扩展事件仅显示事件字段的数据类型。 例如，不显示只读事件字段。）如果您选择两个或更多事件，则“新建会话”对话框将在 **“事件字段”** 选项卡上显示空白。  
  
5.  若要向某一事件会话添加目标，请在 **“选择页”** 部分中选择 **“数据存储”**。  
  
    > [!NOTE]  
    >  在完成事件会话的创建前，不要单击“确定”。  
  
#### <a name="to-add-targets-to-an-event-session"></a>向事件会话添加目标  
  
1.  在“新建会话”对话框的 **“选择页”** 部分中，选择 **“数据存储”**。  
  
2.  在“数据存储”页中，从下拉列表选择目标类型。  
  
     在选择目标类型后，将显示目标说明。 一次只能添加一个目标。 如果您已将该目标添加到会话，则该目标将不出现在下拉列表中。  
  
3.  单击 **“添加”** 可为事件会话添加目标。 如果您想要删除某一目标，则单击 **“删除”**。  
  
     目标属性出现在 **“目标”** 部分的下方，具体位置取决于您选择的目标。  
  
4.  下面是根据您选择的目标可指定的属性：  
  
    |Target|目标属性|  
    |------------|-----------------------|  
    |**etw_classic_sync_target**|**服务器上的会话日志文件名称**。 输入服务器上的日志文件名称和目录，或者单击 **“浏览”** 以便查找和选择日志文件。<br /><br /> **最大日志文件大小**。 为 Windows 事件跟踪 (ETW) 事件输入最大日志文件大小。 默认值为 20 MB。 您可以从下拉列表中选择不同的存储单位。<br /><br /> **缓冲区大小**。 为事件会话输入内存中缓冲区大小。 默认值为 128 KB。 您可以从下拉列表中选择不同的存储单位。<br /><br /> **会话名称**。 输入有意义的 ETW 会话名称。<br /><br /> **出错时重新尝试写入 ETW**。 选中此复选框可以重新尝试将事件发布到 ETW 子系统。<br /><br /> **最大重试次数**。 输入您要将事件发布给 ETW 子系统的最大重试次数，在此次数之后将删除该事件。 默认的重试次数是零 (0)。 对于此目标属性，零 (0) 意味着不重试。|  
    |**event_counter**|没有用于事件计数器的目标属性。|  
    |**event_file**|**服务器上的文件名**。 输入服务器上的目录和目标文件名，或者单击 **“浏览”** 以便查找和选择目标文件。<br /><br /> **最大文件大小**。 为文件目标指定最大文件大小。 如果未指定最大文件大小，则文件将一直增长到磁盘变满为止。 默认文件大小为 1 GB。 您可以从下拉列表中选择不同的存储单位。<br /><br /> **启用文件滚动更新**。 选中此复选框可为文件目标启用文件滚动更新。<br /><br /> **文件的最大数目**。 输入要保留在文件系统中的最大文件数。|  
    |**直方图**|**要筛选的事件**。 从下拉列表中选择要筛选的事件。 您可以筛选在事件会话中存在的任何事件。 您还可以选择 **\<None >** 从下拉列表以便包括所有事件和操作基础存储桶。<br /><br /> **存储桶基于: 操作**。 选择此选项可以将存储桶基于用作数据源的操作名称，然后从下拉列表中选择该操作。<br /><br /> **存储桶基于: 字段**。 选择此选项可以将存储桶基于用作数据源的事件字段，然后从下拉列表中选择该字段。<br /><br /> **最大存储桶数**。 输入要保留的存储桶的最大数目。 达到此值后，事件会话将忽略不属于现有存储桶的任何新事件。|  
    |**pair_matching**|**事件: 开头为**。 从下拉列表中选择在成对序列中指定开始事件的事件名称。<br /><br /> **事件: 结尾为**。 从下拉列表中选择在成对序列中指定结束事件的事件名称。<br /><br /> **字段和操作: 开头为**。 从下拉列表中选择成对序列中的开始字段和/或操作。<br /><br /> **字段和操作: 结尾为**。 从下拉列表中选择成对序列中的结束字段和/或操作。<br /><br /> **如果内存压力发生，放弃不成对的新事件**。 如果选中此复选框，则在计算机处于内存压力下时，将停止收集针对 pair_matching 目标的事件。 在不再存在内存压力后，事件的收集将恢复。<br /><br /> **孤立事件最大数目**。 指定您要保留在内存中的孤立事件的最大数目。|  
    |**ring_buffer**|**要保留的事件的数目**。 使用向上和向下箭头可以指定要保留的事件的数目。 默认值为 1000。<br /><br /> **最大缓冲区内存大小**。 输入要使用的最大内存量。 达到此值时将删除现有事件。 默认内存大小为 0 MB，这意味着无限制。 您可以从下拉列表中选择不同的存储单位。<br /><br /> **在缓冲区已满时保留指定数目的事件(按类型)**。 选择此选项可以在缓冲区中保留每种类型的指定数目的事件。<br /><br /> **要保留的事件的数目(按类型)**。 输入缓冲区中要保留的每种类型的首选事件数。|  
  
5.  如果您想要设置高级配置属性，则在 **“选择页”** 部分中选择 **“高级”** 。  
  
    > [!NOTE]  
    >  在完成事件会话的创建前，不要单击“确定”。  
  
#### <a name="to-set-advanced-configurations"></a>设置高级配置  
  
1.  在“新建会话”对话框的 **“选择页”** 部分，选择 **“高级”**。  
  
2.  在 **“高级”** 页上，若要为事件会话指定 **“事件保留模式”** 选项，请执行以下操作：  
  
    1.  **单个事件丢失**。 选择此选项可允许丢失单个事件。  
  
    2.  **多个事件丢失**。 选择此选项可允许丢失多个事件。  
  
    3.  **无事件丢失**。 如果您想要禁止事件丢失，则选择此选项。 不建议选择此选项。  
  
        > [!NOTE]  
        >  某些事件（例如 **sqlos.wait_info** 事件）与 **无事件丢失** 事件保留模式不兼容。  
  
3.  若要为事件会话指定 **“最大调度滞后时间”** 选项，请执行以下操作：  
  
    1.  **秒**。 选择此选项可延长或缩短最大调度滞后时间。 使用向上和向下箭头可以秒为单位指定最大调度滞后时间。  
  
    2.  **无限制**。 如果您希望仅在缓冲区已满时调度事件，则选择此选项。  
  
4.  在 **“最大内存大小”** 框中，输入最大内存大小。 达到此值时将删除现有事件。 您可以从下拉列表中选择不同的存储单位。  
  
5.  在 **“最大事件大小”** 框中，为大到无法在 **“最大内存大小”** 中包含的事件，输入最大事件大小。 如果您未在收集非常大的事件，则无需配置此选项。 您可以从下拉列表中选择不同的存储单位。  
  
6.  若要为事件会话指定 **“内存分区模式”** 选项，请执行以下操作：  
  
    1.  **无**。 如果您不需要内存分区模式，则选择此选项。  
  
    2.  **按节点**。 如果您要按节点对内存进行分区，则选择此选项。  
  
    3.  **按 CPU**。 如果您按 CPU 对内存进行分区，则选择此选项。  
  
 若要恢复之前的会话属性的配置默认值，请单击 **“恢复默认设置”**。  
  
## <a name="see-also"></a>请参阅  
 [创建扩展的事件会话使用查询编辑器](../../2014/database-engine/create-an-extended-events-session-using-query-editor.md)   
 [创建扩展的事件会话使用向导&#40;对象资源管理器&#41;](../ssms/object/object-explorer.md)   
 [编写扩展事件会话的脚本](../../2014/database-engine/script-an-extended-event-session.md)  
  
  