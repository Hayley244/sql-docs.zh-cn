---
title: 配置 SSL 加密的客户端 |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ae34cd1f-3569-4759-80c7-7c9b33b3e9eb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7a45a0da57be9df27d205b644e1d7156151982f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32832534"
---
# <a name="configuring-the-client-for-ssl-encryption"></a>为 SSL 加密配置客户端
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]或客户端必须验证服务器是正确的服务器和客户端信任的证书颁发机构颁发其证书。 为了验证服务器证书，在连接时必须提供信任材料。 此外，服务器证书的颁发者必须是客户端信任的证书颁发机构。  
  
 本主题首先介绍了如何在客户端计算机中提供信任材料。 然后，本主题介绍当私钥证书颁发机构颁发 SQL Server 实例的安全套接字层 (SSL) 证书时，如何将服务器证书导入到客户端计算机的信任存储区。  
  
 有关验证服务器证书的详细信息，请参阅中的验证服务器 SSL 证书部分[了解 SSL 支持](../../connect/jdbc/understanding-ssl-support.md)。  
  
## <a name="configuring-the-client-trust-store"></a>配置客户端信任存储区  
 验证服务器证书要求，必须在连接时通过提供信任材料**trustStore**和**trustStorePassword**连接属性显式，或通过隐式使用基础 Java 虚拟机 (JVM) 的默认信任存储区。 有关如何设置的详细信息**trustStore**和**trustStorePassword**属性在连接字符串中，请参阅[使用 SSL 加密连接](../../connect/jdbc/connecting-with-ssl-encryption.md)。  
  
 如果**trustStore**属性为未指定或设置为 null，[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]将依赖于基础 JVM 安全提供程序，Java 安全套接字扩展 (SunJSSE)。 SunJSSE 提供程序提供了默认 TrustManager，用于验证信任材料信任存储区中提供针对 SQL Server 返回的 X.509 证书。  
  
 TrustManager 尝试找到默认 trustStore 按以下搜索顺序：  
  
-   如果定义的系统属性"javax.net.ssl.trustStore"，则 TrustManager 将尝试通过使用该系统属性所指定的文件名来查找默认 trustStore 文件。  
  
-   如果未指定"javax.net.ssl.trustStore"系统属性，并且该文件"\<java 主页 >/lib/安全/jssecacerts"存在，使用该文件。  
  
-   如果文件"\<java 主页 >/lib/安全/cacerts"存在，使用该文件。  
  
 有关详细信息，请参阅 Sun Microsystems 网站上的 SUNX509 TrustManager 接口文档。  
  
 Java 运行时环境允许您设置 trustStore 和 trustStorePassword 系统属性，如下所示：  
  
```  
java -Djavax.net.ssl.trustStore=C:\MyCertificates\storeName  
java -Djavax.net.ssl.trustStorePassword=storePassword  
```  
  
 在这种情况下，在此 JVM 上运行的任何应用程序都将使用这些设置作为默认设置。 若要重写你的应用程序中的默认设置，应设置**trustStore**和**trustStorePassword**连接字符串中或在相应的连接属性setter 方法的[SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)类。  
  
 此外，你可以配置和管理的默认信任存储区文件，如"\<java 主页 >/lib/安全/jssecacerts"和"\<java 主页 >/lib/安全/cacerts"。 为此，请使用随 JRE（Java 运行时环境）安装的 JAVA“keytool”实用工具。 有关“keytool”实用工具的详细信息，请参阅 Sun Microsystems 网站上的 keytool 文档。  
  
### <a name="importing-the-server-certificate-to-trust-store"></a>将服务器证书导入到信任存储区  
 在 SSL 握手期间，服务器向客户端发送其公钥证书。 公钥证书的颁发者称为证书颁发机构 (CA)。 客户端必须确保证书颁发机构是客户端信任的证书颁发机构。 这是通过提前了解受信任的证书版本机构的公钥来实现的。 通常，JVM 随附了一组预定义的受信任的证书颁发机构。  
  
 如果私钥证书颁发机构颁发了 SQL Server 实例的 SSL 证书，则您必须将证书颁发机构的证书添加到客户端计算机的信任存储区内的信任证书列表中。  
  
 为此，使用 JAVA"keytool"实用程序随 JRE （Java 运行时环境） 一起安装。 下面的命令提示演示如何使用“keytool”实用工具从文件中导入证书：  
  
```  
keytool -import -v -trustcacerts -alias myServer -file caCert.cer -keystore truststore.ks  
```  
  
 此示例使用名为“caCert.cer”的文件作为证书文件。 您可以从服务器获得此证书文件。 以下步骤说明如何将服务器证书导出到文件中：  
  
1.  单击“开始”，然后单击“运行”并键入 MMC。 （MMC 是 Microsoft 管理控制台的首字母缩写词。）  
  
2.  在 MMC 中，打开“证书”。  
  
3.  展开“个人”，然后展开“证书”。  
  
4.  右键单击服务器证书，然后选择“所有任务”\“导出”。  
  
5.  单击“下一步”以略过“证书导出向导”的“欢迎使用”对话框。  
  
6.  确认选中了“否，不导出私钥”，然后单击“下一步”。  
  
7.  确保选中了“DER 编码的二进制 X.509 (.CER)”或“Base-64 编码的 X.509 (.CER)”，然后单击“下一步”。  
  
8.  输入导出文件名。  
  
9. 单击“下一步”，然后单击“完成”以导出证书。  
  
## <a name="see-also"></a>另请参阅  
 [使用 SSL 加密](../../connect/jdbc/using-ssl-encryption.md)   
 [保护 JDBC 驱动程序应用程序](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
