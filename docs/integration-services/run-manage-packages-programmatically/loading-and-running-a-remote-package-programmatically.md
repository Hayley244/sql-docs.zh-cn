---
title: "加载和以编程方式运行远程包 |Microsoft 文档"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- remote packages [Integration Services]
ms.assetid: 9f6ef376-3408-46bf-b5fa-fc7b18c689c9
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9890f84a983b07534713fe5ec8c547f01e5b2264
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="loading-and-running-a-remote-package-programmatically"></a>以编程方式加载和运行远程包
  若要从未安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的本地计算机运行远程包，请启动这些包，以便它们可在安装了 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的远程计算机上运行。 为此，可在本地计算机上使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理、Web 服务或远程组件来启动远程计算机上的包。 如果尝试直接从本地计算机启动远程包，则这些包将加载到本地计算机上，并尝试在本地计算机上运行。 如果本地计算机未安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]，这些包将不会运行。  
  
> [!NOTE]  
>  你不能之外运行包[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]不具有的客户端计算机上[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]安装，和的条款你[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]授权可能不允许你安装[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]在其他计算机上。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 是服务器组件，不可再分发至客户端计算机。  
  
 或者，您也可以从安装了 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的本地计算机运行远程包。 有关详细信息，请参阅[加载和本地包以编程方式运行](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)。  
  
##  <a name="top"></a>在远程计算机上运行远程包  
 如上所述，可以用多种方法在远程服务器上运行远程包：  
  
-   [使用 SQL Server 代理以编程方式运行远程包](#agent)  
  
-   [使用 Web 服务或远程组件以编程方式运行远程包](#service)  
  
 使用本主题中用于加载和保存包的几乎所有方法都需要引用**Microsoft.SqlServer.ManagedDTS**程序集。 例外情况是执行本主题中演示的 ADO.NET 方法**sp_start_job**存储过程，其中需要仅引用**System.Data**。 在添加到引用后**Microsoft.SqlServer.ManagedDTS**在新项目中，导入的程序集<xref:Microsoft.SqlServer.Dts.Runtime>具有命名空间**使用**或**导入**语句。  
  
###  <a name="agent"></a>使用 SQL Server 代理以编程方式在服务器上运行远程包  
 下面的代码示例演示如何以编程方式使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在服务器上运行远程包。 代码示例调用系统存储过程中， **sp_start_job**，此时将启动[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理作业。 该存储过程启动的作业名为 `RunSSISPackage`，并且此作业位于远程计算机上。 然后 `RunSSISPackage` 作业在远程计算机上运行包。  
  
> [!NOTE]  
>  返回值**sp_start_job**存储的过程指示存储的过程是否能够启动[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理作业已成功。 此返回值不指示该包成功还是失败。  
  
 有关排查从运行的包信息[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理作业，请参阅 Microsoft 文章， [SSIS 包不运行时从 SQL Server 代理作业步骤调用 SSIS 包](http://support.microsoft.com/kb/918760)。  
  
### <a name="sample-code"></a>示例代码  
  
```vb  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
  
    Dim jobConnection As SqlConnection  
    Dim jobCommand As SqlCommand  
    Dim jobReturnValue As SqlParameter  
    Dim jobParameter As SqlParameter  
    Dim jobResult As Integer  
  
    jobConnection = New SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI")  
    jobCommand = New SqlCommand("sp_start_job", jobConnection)  
    jobCommand.CommandType = CommandType.StoredProcedure  
  
    jobReturnValue = New SqlParameter("@RETURN_VALUE", SqlDbType.Int)  
    jobReturnValue.Direction = ParameterDirection.ReturnValue  
    jobCommand.Parameters.Add(jobReturnValue)  
  
    jobParameter = New SqlParameter("@job_name", SqlDbType.VarChar)  
    jobParameter.Direction = ParameterDirection.Input  
    jobCommand.Parameters.Add(jobParameter)  
    jobParameter.Value = "RunSSISPackage"  
  
    jobConnection.Open()  
    jobCommand.ExecuteNonQuery()  
    jobResult = DirectCast(jobCommand.Parameters("@RETURN_VALUE").Value, Integer)  
    jobConnection.Close()  
  
    Select Case jobResult  
      Case 0  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.")  
      Case Else  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.")  
    End Select  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace LaunchSSISPackageAgent_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      SqlConnection jobConnection;  
      SqlCommand jobCommand;  
      SqlParameter jobReturnValue;  
      SqlParameter jobParameter;  
      int jobResult;  
  
      jobConnection = new SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI");  
      jobCommand = new SqlCommand("sp_start_job", jobConnection);  
      jobCommand.CommandType = CommandType.StoredProcedure;  
  
      jobReturnValue = new SqlParameter("@RETURN_VALUE", SqlDbType.Int);  
      jobReturnValue.Direction = ParameterDirection.ReturnValue;  
      jobCommand.Parameters.Add(jobReturnValue);  
  
      jobParameter = new SqlParameter("@job_name", SqlDbType.VarChar);  
      jobParameter.Direction = ParameterDirection.Input;  
      jobCommand.Parameters.Add(jobParameter);  
      jobParameter.Value = "RunSSISPackage";  
  
      jobConnection.Open();  
      jobCommand.ExecuteNonQuery();  
      jobResult = (Int32)jobCommand.Parameters["@RETURN_VALUE"].Value;  
      jobConnection.Close();  
  
      switch (jobResult)  
      {  
        case 0:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.");  
          break;  
        default:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.");  
          break;  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
###  <a name="service"></a>使用 Web 服务或远程组件以编程方式运行远程包  
 上面的以编程方式在服务器上运行包的解决方案不需要服务器上的任何自定义代码。 但是，您可能更倾向于不依赖 SQL Server 代理来执行包的解决方案。 下面的示例演示可在服务器上创建用于在本地启动 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的 Web 服务，以及可用于从客户端计算机调用 Web 服务的测试应用程序。 如果想要创建而不是 Web 服务的远程组件，你可以使用相同的代码逻辑很少更改远程组件中。 但是，与 Web 服务相比，远程组件可能需要更广泛的配置。  
  
> [!IMPORTANT]  
>  使用 Web 服务的默认身份验证和授权设置，加载和执行包时通常没有足够的权限来访问 SQL Server 或文件系统。 你可能需要将适当的权限分配给 Web 服务中，通过配置在其身份验证和授权设置**web.config**文件并分配适当的数据库和文件系统权限。 有关 Web、数据库和文件系统权限的全面讨论已超出了本主题的范围。  
  
> [!IMPORTANT]  
>  方法<xref:Microsoft.SqlServer.Dts.Runtime.Application>以便使用与 SSIS 包存储区中的类仅支持"。"，localhost 或服务器的本地服务器的名称。 不能使用“(local)”。  
  
### <a name="sample-code"></a>示例代码  
 下面的代码示例演示如何创建和测试 Web 服务。  
  
#### <a name="creating-the-web-service"></a>创建 Web 服务  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包可从文件或 SQL Server 直接加载，也可以从 SSIS 包存储区加载，该存储区在 SQL Server 和特殊文件系统文件夹中管理包存储。 此示例通过使用支持所有可用的选项**Select Case**或**切换**构造选择合适的语法，用于启动包以及要连接的输入自变量适当地。 LaunchPackage Web 服务方法返回的包执行结果为整数形式，而不是 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 值，以便客户端计算机不需要引用任何 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 程序集。  
  
###### <a name="to-create-a-web-service-to-run-packages-on-the-server-programmatically"></a>以编程方式创建 Web 服务以在服务器上运行包  
  
1.  打开 Visual Studio，并使用首选的编程语言创建一个 Web 服务项目。 示例代码将该项目命名为 LaunchSSISPackageService。  
  
2.  添加对的引用**Microsoft.SqlServer.ManagedDTS**并添加**导入**或**使用**语句的代码文件与**Microsoft.SqlServer.Dts.Runtime**命名空间。  
  
3.  将 LaunchPackage Web 服务方法的示例代码粘贴到类中。 （该示例显示了代码窗口的全部内容。）  
  
4.  生成该 Web 服务，并通过为 LaunchPackage 方法的输入参数提供一组指向现有包的有效值来进行测试。 例如，如果 package1.dtsx 存储在服务器的 C:\My Packages 中，则传递“file”作为 sourceType 的值，“C:\My Packages”作为 sourceLocation 的值，以及“package1”（不带扩展名）作为 packageName 的值。  
  
```vb  
Imports System.Web  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.IO  
  
<WebService(Namespace:="http://dtsue/")> _  
<WebServiceBinding(ConformsTo:=WsiProfiles.BasicProfile1_1)> _  
<Global.Microsoft.VisualBasic.CompilerServices.DesignerGenerated()> _  
Public Class LaunchSSISPackageService  
  Inherits System.Web.Services.WebService  
  
  ' LaunchPackage Method Parameters:  
  ' 1. sourceType: file, sql, dts  
  ' 2. sourceLocation: file system folder, (none), logical folder  
  ' 3. packageName: for file system, ".dtsx" extension is appended  
  
  <WebMethod()> _  
  Public Function LaunchPackage( _  
    ByVal sourceType As String, _  
    ByVal sourceLocation As String, _  
    ByVal packageName As String) As Integer 'DTSExecResult  
  
    Dim packagePath As String  
    Dim myPackage As Package  
    Dim integrationServices As New Application  
  
    ' Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName)  
  
    Select Case sourceType  
      Case "file"  
        ' Package is stored as a file.  
        ' Add extension if not present.  
        If String.IsNullOrEmpty(Path.GetExtension(packagePath)) Then  
          packagePath = String.Concat(packagePath, ".dtsx")  
        End If  
        If File.Exists(packagePath) Then  
          myPackage = integrationServices.LoadPackage(packagePath, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid file location: " & packagePath)  
        End If  
      Case "sql"  
        ' Package is stored in MSDB.  
        ' Combine logical path and package name.  
        If integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty) Then  
          myPackage = integrationServices.LoadFromSqlServer( _  
            packageName, "(local)", String.Empty, String.Empty, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case "dts"  
        ' Package is managed by SSIS Package Store.  
        ' Default logical paths are File System and MSDB.  
        If integrationServices.ExistsOnDtsServer(packagePath, ".") Then  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case Else  
        Throw New ApplicationException( _  
          "Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.")  
    End Select  
  
    Return myPackage.Execute()  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.IO;  
  
[WebService(Namespace = "http://dtsue/")]  
[WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
public class LaunchSSISPackageServiceCS : System.Web.Services.WebService  
{  
  public LaunchSSISPackageServiceCS()  
  {  
    }  
  
  // LaunchPackage Method Parameters:  
  // 1. sourceType: file, sql, dts  
  // 2. sourceLocation: file system folder, (none), logical folder  
  // 3. packageName: for file system, ".dtsx" extension is appended  
  
  [WebMethod]  
  public int LaunchPackage(string sourceType, string sourceLocation, string packageName)  
  {   
  
    string packagePath;  
    Package myPackage;  
    Application integrationServices = new Application();  
  
    // Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName);  
  
    switch(sourceType)  
    {  
      case "file":  
        // Package is stored as a file.  
        // Add extension if not present.  
        if (String.IsNullOrEmpty(Path.GetExtension(packagePath)))  
        {  
          packagePath = String.Concat(packagePath, ".dtsx");  
        }  
        if (File.Exists(packagePath))  
        {  
          myPackage = integrationServices.LoadPackage(packagePath, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid file location: "+packagePath);  
        }  
        break;  
      case "sql":  
        // Package is stored in MSDB.  
        // Combine logical path and package name.  
        if (integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty))  
        {  
          myPackage = integrationServices.LoadFromSqlServer(packageName, "(local)", String.Empty, String.Empty, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      case "dts":  
        // Package is managed by SSIS Package Store.  
        // Default logical paths are File System and MSDB.  
        if (integrationServices.ExistsOnDtsServer(packagePath, "."))  
        {  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      default:  
        throw new ApplicationException("Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.");  
    }  
  
    return (Int32)myPackage.Execute();  
  
  }  
  
}  
```  
  
#### <a name="testing-the-web-service"></a>测试 Web 服务  
 下面的示例控制台应用程序使用 Web 服务运行包。 Web 服务的 LaunchPackage 方法返回的包执行结果为整数形式，而不是 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 值，以便客户端计算机不需要引用任何 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 程序集。 该示例创建私有枚举，该枚举的值镜像 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 值，以报告执行结果。  
  
###### <a name="to-create-a-console-application-to-test-the-web-service"></a>创建用于测试 Web 服务的控制台应用程序  
  
1.  在 Visual Studio 中，使用首选的编程语言将新的控制台应用程序添加到包含 Web 服务项目的解决方案中。 示例代码将该项目命名为 LaunchSSISPackageTest。  
  
2.  将新的控制台应用程序设置为解决方案中的启动项目。  
  
3.  添加对 Web 服务项目的 Web 引用。 如有必要，可调整示例代码中分配给 Web 服务代理对象的名称的变量声明。  
  
4.  将主例程和私有枚举的示例代码粘贴到代码中。 （该示例显示了代码窗口的全部内容。）  
  
5.  编辑调用 LaunchPackage 方法的代码行，为输入参数提供一组指向现有包的有效值。 例如，如果 package1.dtsx 存储在服务器的 C:\My Packages 中，则传递“file”作为 `sourceType` 的值，“C:\My Packages”作为 `sourceLocation` 的值，以及“package1”（不带扩展名）作为 `packageName` 的值。  
  
```vb  
Module LaunchSSISPackageTest  
  
  Sub Main()  
  
    Dim launchPackageService As New LaunchSSISPackageService.LaunchSSISPackageService  
    Dim packageResult As Integer  
  
    Try  
      packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage")  
    Catch ex As Exception  
      ' The type of exception returned by a Web service is:  
      '  System.Web.Services.Protocols.SoapException  
      Console.WriteLine("The following exception occurred: " & ex.Message)  
    End Try  
  
    Console.WriteLine(CType(packageResult, PackageExecutionResult).ToString)  
    Console.ReadKey()  
  
  End Sub  
  
  Private Enum PackageExecutionResult  
    PackageSucceeded  
    PackageFailed  
    PackageCompleted  
    PackageWasCancelled  
  End Enum  
  
End Module  
```  
  
```csharp  
using System;  
  
namespace LaunchSSISPackageSvcTestCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS launchPackageService = new LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS();  
      int packageResult = 0;  
  
      try  
      {  
        packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage");  
      }  
      catch (Exception ex)  
      {  
        // The type of exception returned by a Web service is:  
        //  System.Web.Services.Protocols.SoapException  
        Console.WriteLine("The following exception occurred: " + ex.Message);  
      }  
  
      Console.WriteLine(((PackageExecutionResult)packageResult).ToString());  
      Console.ReadKey();  
  
    }  
  
    private enum PackageExecutionResult  
    {  
      PackageSucceeded,  
      PackageFailed,  
      PackageCompleted,  
      PackageWasCancelled  
    };  
  
  }  
}  
```  
  
## <a name="external-resources"></a>外部资源  
  
-   视频，[如何： 通过使用 SQL Server 代理 （SQL Server 视频） 自动执行 SSIS 包](http://technet.microsoft.com/sqlserver/ff686764.aspx)，technet.microsoft.com 上  
  
## <a name="see-also"></a>另请参阅  
 [了解本地和远程执行之间的差异](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [加载和以编程方式运行本地包](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [加载本地包的输出](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  