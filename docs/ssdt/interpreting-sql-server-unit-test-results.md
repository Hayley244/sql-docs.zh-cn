---
title: 解释 SQL Server 单元测试结果 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fde3c95b-2f68-483d-a197-0f7161b72fa3
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1709d7ca64eedf5e4f0dd170606082e7f99f3e31
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083859"
---
# <a name="interpreting-sql-server-unit-test-results"></a>解释 SQL Server 单元测试结果
运行 SQL Server 单元测试时，将会自动生成测试结果，将其保存到磁盘并在“测试结果”窗口中显示摘要信息。 启动测试运行后，“测试结果”窗口将出现并显示测试运行的进度。 此显示内容包括正在运行的测试和已完成的测试。  
  
若要查看有关某个测试结果的详细信息，请在“测试结果”窗口中双击该测试结果以显示“测试结果详细信息”页。 有关测试结果的详细信息，请双击测试结果。  
  
有关如何更改“测试结果”窗口的显示的详细信息，请参阅[如何：在测试窗口中添加或移除列 (Visual Studio 2010)](http://msdn.microsoft.com/library/ms182508(VS.100).aspx)或[如何：在测试窗口中添加或移除列 (Visual Studio 2012)](http://msdn.microsoft.com/library/ms182508.aspx)。  
  
## <a name="storing-test-results"></a>存储测试结果  
单元测试的结果将会自动存储在硬盘上文件扩展名为 .trx 的文件中。 .trx 文件是包含测试运行的详细信息的 XML 文件。 您可加载之前的测试运行的 .trx 文件以查看这些测试运行的结果或重新运行之前的测试。 有关详细信息，请参阅[如何：重新运行测试 (Visual Studio 2010)](http://msdn.microsoft.com/library/ms182472(VS.100).aspx)。  
  
> [!NOTE]  
> 不能远程运行单元测试。  
  
如果团队使用 Visual Studio Team Foundation Server 团队项目来帮助管理团队工作，则还可将测试数据发布到称为“操作存储区”的 SQL Server 数据库。  
  
有关如何保存测试结果、重用测试结果以及与团队共享测试结果的详细信息，请参阅[如何：在 Visual Studio 2010 中保存和打开测试结果](http://msdn.microsoft.com/library/ms404662(VS.100).aspx)或[如何：在 Visual Studio 2012 中保存和打开测试结果](http://msdn.microsoft.com/library/ms404662.aspx)。  
  
## <a name="see-also"></a>另请参阅  
[运行 SQL Server 单元测试](../ssdt/running-sql-server-unit-tests.md)  
  
