# WebServices-FrameWork


>Are you tired of repetitive coding? 

** If yes, then this framework is for you **
WebServices-FrameWork allows the developer to efficiently carry out services required by the client. This framework allows you to develop/implement your server side code faster by saving time as the developer will only have to write the main logic (only) and the rest is done for you.
**Can only be used with tomcat **

# Table Of Contents
- [Dependencies](#dependencies)
- [SetUp](#setup)
- [How to Use](#how-to-use)
- [Documentation](#documentation)

# Dependencies
* Tomcat 8.5 or above
* JDK 6 or above

# SetUp
 1. Install all the above dependencies.
 2. Create an application in c:\tomcat9\webapps\ folder say, web-app-name.
 3. To use the framework copy paste **serviceJar.jar** in the c:\tomcat9\webapps\web-app-name\WEB-INF\lib 
 4. copy paste PDFGenerator in same folder as that of the newly created web-app
 5. copy paste .jar files from AdditionalJars in lib folder of WEB-INF (if you don't have gson and itext jars)


# How To Use 
-**Service FrameWork**
 1. Create a folder named, classes in WEB-INF folder of your web-app-name
 2. Create a public class Service.java (you can change the name if you want) and write the following statement
  - > import com.thinking.machines.employees.servlets.* ;
  - extend TMService class
  -implement init() method of Service.java and on firstLine write super.init()
 3. Create another class named, ServiceProcess.java and import com.thinking.machines.servlets package
  - ServiceProcess class must extend ProcessService
  - pass the reference of HttpServletRequest and HttpServletResponse to the service() method of the ProcessService class
    you can do it by writing super.service() and passing request amd response object refernce respectively.
 4. Map ServiceProcess in web.xml to the URL /service   
 5. Create your own class and apply the annotations specified in the documentation.(Must apply path annotation to use any service.)
 6. To send the request to any service the client must write --->
    > https://localhost:8080/web-app-name/service/path-to-service-specifed-in-path-annotation
    
  -**PDFGenerator**   
  -It can generate the list of services /errors in pdf. You have to pass Service or Error as arg0
    >java -classpath path-to-additionalJars\* PDFGenarator Service path-to-WED-INF-folder 

# Documentation
The framework provides the following annotations using which the user can programmer the site faster.
## Annotation

|Name |Property | ElemnetType | Usage |
|:---|:---|:---| :---|
|Path| value | METHOD, CLASS | maps the class/method (on which @Path is applied) to the url |
| RequestData | value | METHOD | extract the data from request object (supports json object ) |
|ResponseType | value | METHOD | sending the response to the client |
| Secured | value | METHOD | authentication |
| FileExtractor | location,maxFileSize | METHOD | extract mutiple/single file if send in request|

