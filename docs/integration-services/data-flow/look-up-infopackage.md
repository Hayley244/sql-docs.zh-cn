---
title: "查找 Infopackage |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c0cb7a4-cd07-44cc-85cb-eb1ad91f85fd
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 603f32bbcf61ce562b0e8f6645e0384bb4dccdf2
ms.contentlocale: zh-cn
ms.lasthandoff: 08/03/2017

---
# <a name="look-up-infopackage"></a>查找 InfoPackage
  使用 **“查找 InfoPackage”** 对话框查找在 SAP Netweaver BW 系统中定义的 InfoPackage。 当 InfoPackage 列表显示时，选择您需要的 InfoPackage，然后目标将使用需要的值填充关联的选项。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目标使用 **“查找进程链”** 对话框。 若要了解有关 SAP BW 目标的详细信息，请参阅 [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md)。  
  
> [!IMPORTANT]  
>  针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。 有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。  
  
 **打开“查找 InfoPackage”对话框**  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。  
  
2.  在“数据流”选项卡上，双击 SAP BW 目标。  
  
3.  在 **“SAP BW 目标编辑器”**中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。  
  
4.  在“连接管理器”页面上的“InfoPackage/InfoSource”组框中，单击“查找”显示“查找 InfoPackage”对话框。  
  
## <a name="lookup-options"></a>查找选项  
 在查找字段中，您可以使用星号通配符 (*) 或使用部分字符串结合星号通配符来筛选结果。 但是，如果您将查找字段保留为空，则查找操作仅与该字段中的空字符串匹配。  
  
 **InfoPackage**  
 输入您要查找的 InfoPackage 的名称，或输入部分名称加上星号通配符 (*)。 或者，仅使用星号通配符，以包括所有 InfoPackage。  
  
 **InfoSource**  
 输入 InfoSource 的名称，或输入部分名称加上星号通配符 (*)。 或者，仅使用星号通配符以包括所有 InfoPackage（而无论 InfoSource 是什么）。  
  
 **源系统**  
 输入源系统的名称，或输入部分名称加上星号通配符 (*)。 或者，仅使用星号通配符以包括所有 InfoPackage（而无论源系统是什么）。  
  
 **查找**  
 查找在 SAP Netweaver BW 系统中定义的匹配 InfoPackage。  
  
## <a name="lookup-results"></a>查找结果  
 单击“查找”按钮后，将在一个包含以下列标题的表中显示 SAP Netweaver BW 系统中 InfoPackage 的列表。  
  
 **InfoPackage**  
 显示在 SAP Netweaver BW 系统中定义的 InfoPackage 的名称。  
  
 **类型**  
 显示 InfoPackage 的类型。 下表列出了该类型的可能值。  
  
|“值”|Description|  
|-----------|-----------------|  
|Trans.|事务数据。|  
|Attr.|属性数据。|  
|文本|文本。|  
  
 **Description**  
 显示 InfoPackage 的说明。  
  
 **InfoSource**  
 显示与 InfoPackage 相关联的 InfoSource（如果有）的名称。  
  
 **Source System**  
 显示源系统的名称。  
  
 当 InfoPackage 列表显示时，选择您需要的 InfoPackage，然后目标将使用需要的值填充关联的选项。  
  
## <a name="see-also"></a>另请参阅  
 [SAP BW 目标编辑器（“连接管理器”页）](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Microsoft Connector for SAP BW F1 帮助](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  