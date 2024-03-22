# IBM - Machine Learning with Apache Spark - notes
Implementing machine learning using Apache Spark

## 🧸💬 Before we start

🧸💬 Before we start understanding the basic concept of working sessions with Apache Spark, it is the same as Tensorflow and distributed processes machine learning and remote tasks executions solution. </br>
🐑💬 ➰ Apache Spark is a network application capable of network routes and application implementation with supporting programming languages such as angular.js, Python, Pytorch, Java, Javascript, machine learning APIs, and data scientific APIs. </br>
🦤💬 The remote execution tasks and synchronized are important in the research study too, we measure the abandoned executions for solution performance while remote execution can work parallel for verification methods for some execution tasks verification with the same or different process execution as we know EDW data warehouse processes. 🗺️💬 See you in the next 6 hours from Australia. </br>
💃( 👩‍🏫 )💬 I had a project contact center for financial products the communications of customers and organizing of the method implementing of the products, software, and solutions. The process of organizing and managing the wishing list and target customer groups is identified and selected by manual and automation processes. There are operators to perform these tasks between working automation system ETL process, running commands, and decision making to perform action and confirmation of the process success with automated outputs program indicators and the operators across the countries or system analysts from the IT financial solution. 🗳️💳🧾 ...</br>
🐑💬 ➰ There are many application and integration points, Avaya or Cisco or Interactive Intelligence products agents and supervisors working with application interfaces including AS-400 and applications to manage data records selection from the business units criteria. They used to use the AS-400 and ODBC integration drivers, SQL integration services, and worksheet applications for business team management of records and bin types. Now Apache Airflows, Apache Apark, Batch management system, and software support execution and management processes as we introduced to the ETL process. ⚙️⚙️⚙️ ...</br>
</br>
🐑💬 ➰ The ELT process is a flexible process to extract, load, and transform or extract, transfer, and load data into data lakes to create data pipelines for applications that can work with the instant of application services or data services. We are call data lakes and data pipelines because of the commercial name but they are databases with data integration services and Apache Spark comes with a build automation application routing process and support of Linux and programming language command and batch command at the data pipeline execution process with monitoring tools and applications setting configuration level. Trancent is another option they came with web application GUI and application settings for remote execution process and series execution with multiple methods notifications and drag and drop handlers. ⚙️⚙️⚙️ ...</br>
*( 🐑💬 ➰  Before I create this notes I had IBM Datawarehouse and Apache Airflows experiment in my computer )*  </br>

### 🧸💬 It is important to manage the session or later start a session may need to identify the session name

```
import findspark                                               # 🧸💬 Do not forget session name is the same as the database connection
findspark.init()                                               # 🧸💬 before we need to limit session timeout manage the session
                                                               # 🧸💬 close and dispose before leave the program.
from pyspark.sql import SparkSession
```

### 🧸💬 Create or re-use of the session

```
# 🧸💬 You can create a session and call it DekDee but this session name is used by process monitoring services
spark = SparkSession.builder.appName("DekDee using Spark").getOrCreate() 
```

## ETL processes

## Word phase tokenizers

## NLTK and implementation

## The n-grams word tokenizers and speech engine processing

## Attention networks
