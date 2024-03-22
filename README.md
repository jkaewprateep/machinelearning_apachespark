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
import findspark                                                         # 🧸💬 Do not forget the session name is the same as the database connection
findspark.init()                                                         # 🧸💬 before we need to limit session timeout manage the session
                                                                         # 🧸💬 close and dispose before leave the program.
from pyspark.sql import SparkSession
```

### 🧸💬 Create or re-use of the session

```
# 🧸💬 You can create a session and call it DekDee but this session name is used by process monitoring services
spark = SparkSession.builder.appName("DekDee using Spark").getOrCreate() 
```

### 🧸💬 Introduction to DataFrame and communication objects

```
data = [("student1",64,90),                                               # 🧸💬 A tuple, np.array or Panda.Dataframe or dictionary 
        ("student2",59,100),                                              # or FS or HDFS is a sample of data communication objects here.
        ("student3",69,95),                                               # 🐑💬 ➰ Do not forget the dataset, and data module class as they 
        ("",70,110),                                                      # can integrated with Django and Tensorflow as well.
        ("student5",60,80),                                               # 🐐💬 Data integrations management system can implement at this 
        ("student3",69,95),                                               # level with support of programming languages and bash scripts.
        ("student6",62,85),
        ("student7",65,80),
        ("student7",65,80)]
```

### 🧸💬 Spark data frame is similar to Pandas data frame but supports of Spark commands and selected support data aggregation command

```
# 🧸💬 Create instant of Spark data frame
df = spark.createDataFrame(data, ["student","height_inches","weight_pounds"])
```

- - -

### 🧸💬 This is sample of create instant data frame from statics value

🐑💬 ➰  Both Apache Spark and Pandas have .csv reader object and file reader and .json format support with built-in functions. </br>

```
_class = ["fruits", "fruits", "vegetable", "vegetable", "vegetable"]      # 🧸💬 A class names array
calrories = [95.0, 202.0, 164.0, np.nan, 207.0]                           # 🧸💬 A column record values array
colnames = ["class", "avg calories per unit"]                             # 🧸💬 A column name values array
fruits = ["apple", "mango", "potato", "onion", "broccoli"]                # 🧸💬 A category name values array

series = {}                                                               # 🧸💬 Create an empty object for the record to fill
for i in range(len(fruits)):                                              # 🧸💬 Iterations by the object available
    series[fruits[i]] = [_class[i], calrories[i]]                         # 🧸💬 Create Pandas series with objects value
    
series = pd.DataFrame(series)                                             # 🧸💬 Create instant of pandas series
series = series.T                                                         # 🧸💬 Transpose organize columns

for i in range(len(colnames)):                                            # 🧸💬 Iteration for items in column names array
    series.rename(columns={i: colnames[i]}, inplace=True)                 # 🧸💬 Rename of the column to value in column name array

print(series)                                                             # 🧸💬 Print out display
print("------------------------------------------------")
```

<p align="center" width="100%">
    <img width="50%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/01.png">
</p>
🐑💬 ➰ 🤫 Example of IBM data warehouse exames

- - -

## ETL processes

```
df = spark.read.csv("student-hw.csv", header=True, inferSchema=True)       # 🧸💬 Read dataset from file
df.write.mode("overwrite").parquet("student-hw.parquet")                   # 🧸💬 Write parquet file
df = spark.read.parquet("student-hw-single.parquet")                       # 🧸💬 Read parquet file
df = df.withColumn("height_centimeters", expr("height_inches * 2.54"))     # 🧸💬 Create new column from expression
df.write.mode("overwrite").csv("student_transformed.csv", header=True)     # 🧸💬 Save to .csv file
spark.stop()                                                               # 🧸💬 Remove and dispose of the session as an initial state we discussed
```

## Display data frame to console or output stream IO target

```
df.show(truncate = False)                                                  # 🧸💬 The saem as Pandas dataframe.show()
```

<p align="center" width="100%">
    <img width="50%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/02.png">
</p>
🐑💬 ➰ 🤫 Apache Spark support of both Spark native, work compatibility, and expression string. </br>

## Word phase tokenizers

```
from pyspark.ml.feature import Tokenizer                                   # 🧸💬 Import Spark Tokenizer library

tokenizer = Tokenizer(inputCol="sentence", outputCol="words")              # 🧸💬 Create tokenizer instant object
token_df = tokenizer.transform(df)                                         # 🧸💬 Apply tokenizer and setting to target dataframe
token_df.show(truncate=False)                                              # 🧸💬 Display of the tokenized dataframe
```

🐑💬 ➰ I will explain NLTK for natural language processing and Tensorflow vocaburay and tokenizer too to support multiple task assignments. </br>
👧💬 🎈 ``` Warning it may contain of encoding/decoding value and loves song letter ``` </br>

<p align="center" width="100%">
    <img width="50%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/03.png">
</p>
🐑💬 ➰ 🤫 Word combination is not new and introduced in a unique word processing program for command translation or speech composition. </br>
🛥️💬 He mails you everyday ... </br>

### TensorFlow sample encoder/decoder using data model and vocaurary

```
text = "I love cats"                                                       # 🧸💬 Sample word string input
# 🧸💬 Simple tokenizer you can apply an alpha function or specification-related token you to apply.
tokenizer = tf.keras.preprocessing.text.Tokenizer(num_words=10000, oov_token='<oov>')
tokenizer.fit_on_texts([text])                                             # 🧸💬 Break input word by tokenizer
```

```
text = "I love cats"                                                       # 🧸💬 Sample word string input
# 🧸💬 Sample of vocabulary as spherical secrete codes 
vocab = [ "a", "b", "c", "d", "e", "f", "g", "h", "I", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z", "_" ]
# 🧸💬 Sample of input data or output from the previous token
data = tf.constant([["_", "_", "_", "I"], ["l", "o", "v", "e"], ["c", "a", "t", "s"]])

# 🧸💬 Define network custom layer for string lookup vocabulary
layer = tf.keras.layers.StringLookup(vocabulary=vocab)
sequences_mapping_string = layer(data)                                     # 🧸💬 Apply instant setting to target input
# 🧸💬 Reshape of the output
sequences_mapping_string = tf.constant( sequences_mapping_string, shape=(1,12) )
```

[data model and vocaburary]( https://github.com/jkaewprateep/Simple_encode_decode/blob/main/README.md ) </br>
[speriral secret for networks comm exames]( https://github.com/jkaewprateep/SphericalSecreteWord/blob/main/sample2 ) </br>

## Vectorization ( 🐑💬 ➰ Data model is already vector by vocabulary lookup )

```
from pyspark.ml.feature import CountVectorizer                             # 🧸💬 Import count vector library

cv = CountVectorizer(inputCol="words", outputCol="features")               # 🧸💬 Create instant of count vector with settings
model = cv.fit(textdata)                                                   # 🧸💬 Create instant of a linear model with learning
result = model.transform(textdata)                                         # 🧸💬 Transform target input data, apply any data with shape equal
result.show(truncate=False)                                                # 🧸💬 Display results or IO output
```

<p align="center" width="100%">
    <img width="80%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/04.png">
</p>
🐑💬 ➰ 🤫 Compacts and can be synchronized as WinZip compression because one-hot vector lookup for table and dictionary </br>

## NLTK and implementation

## The n-grams word tokenizers and speech engine processing

## Attention networks
