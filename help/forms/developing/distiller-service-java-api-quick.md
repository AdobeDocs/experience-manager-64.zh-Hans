---
title: Distiller服务Java API快速入门(SOAP)
seo-title: Distiller Service Java API QuickStart(SOAP)
description: 使用Distiller服务Java API将PostScript文件转换为PDF文档。
seo-description: Use the Distiller Service Java API to convert a PostScript file to a PDF document.
uuid: 7781f074-cea4-4109-892b-118cfad4ec36
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 59dd61d1-c6b1-4bea-b666-4aa7897384a1
role: Developer
exl-id: 0d7cdb60-e892-4644-8a72-a8068ca2e224
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 2%

---

# Distiller服务Java API快速入门(SOAP) {#distiller-service-java-api-quickstart-soap}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Java API快速入门(SOAP)可用于Distiller®服务：

[快速入门（SOAP模式）：使用Java API将PostScript文件转换为PDF文档](distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

AEM Forms操作可以使用AEM Forms强类型API执行，连接模式应设置为SOAP。

>[!NOTE]
>
>“使用AEM表单进行编程”中的“快速入门”基于JBoss应用程序服务器和Microsoft Windows操作系统上部署的Forms服务器。 但是，如果您使用的是其他操作系统（如UNIX），请将特定于Windows的路径替换为适用操作系统支持的路径。 同样，如果您使用的是其他J2EE应用程序服务器，请确保指定有效的连接属性。 请参阅 [设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## 快速入门（SOAP模式）：使用Java API将PostScript文件转换为PDF文档 {#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api}

以下代码示例将名为*Loan.ps *的PostScript文件转换为名为的PDF文件 *Loan.pdf*. (请参阅 [将PostScript转换为PDF文档](/help/forms/developing/converting-postscript-pdf-documents.md#converting-postscript-to-pdf-documents).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-distiller-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
  
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.util.Properties; 
 import com.adobe.livecycle.generatepdf.client.CreatePDFResult; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.distiller.client.DistillerServiceClient; 
  
 public class JavaAPICreatePDFSoap { 
  
     public static void main(String[] args) 
     { 
         try 
         {     
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
         // Create a ServiceClientFactory instance 
         ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); 
          
         DistillerServiceClient disClient = new DistillerServiceClient(factory ); 
          
         // Get a PS file document to convert to a PDF document and populate a com.adobe.idp.Document object 
         String inputFileName = "C:\\Adobe\Loan.ps"; 
         FileInputStream fileInputStream = new FileInputStream(inputFileName); 
         Document inDoc = new Document(fileInputStream); 
              
         //Set run-time options 
         String adobePDFSettings = "Standard"; 
          String securitySettings = "No Security"; 
           
          //Convert a PS  file into a PDF file 
         CreatePDFResult result = new CreatePDFResult(); 
         result = disClient.createPDF( 
                 inDoc,  
                 inputFileName,  
                      adobePDFSettings,  
                 securitySettings,  
                 null,  
                 null 
             ); 
               
          //Get the newly created document 
          Document createdDocument = result.getCreatedDocument(); 
               
          //Save the PDF file 
         createdDocument.copyToFile(new File("C:\\Adobe\Loan.pdf")); 
         } 
         catch (Exception e) { 
             e.printStackTrace(); 
         } 
     } 
 }
```
