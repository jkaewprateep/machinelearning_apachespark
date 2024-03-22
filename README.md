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
textdata = "I love cats"                                                   # 🧸💬 Sample word string input
# 🧸💬 Simple tokenizer you can apply an alpha function or specification-related token you to apply.
tokenizer = tf.keras.preprocessing.text.Tokenizer(num_words=10000, oov_token='<oov>')
tokenizer.fit_on_texts([textdata])                                         # 🧸💬 Break input word by tokenizer
```

```
textdata = "I love cats"                                                   # 🧸💬 Sample word string input
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

[Tokenizer for word sentence to sequence vector]( https://github.com/jkaewprateep/text_to_sequence/blob/main/README.md )

## Hashing algorithms ( 🐑💬 ➰ It does not require hashing algorithm since the input is a vector )

```
from pyspark.ml.feature import HashingTF, IDF, Tokenizer                    # 🧸💬  Import HashingTF, IDF and Tokenizer library

tokenizer = Tokenizer(inputCol="sentence", outputCol="words")               # 🧸💬 Create instant of tokenizer with settings
wordsData = tokenizer.transform(df)                                         # 🧸💬 Transform target input data by apply token settings
wordsData.show(truncate = False)                                            # 🧸💬 Display results or IO output
```

<p align="center" width="100%">
    <img width="40%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/05.png">
</p>
🐑💬 ➰ 🤫 Tokenizer can apply with target language model for multi-language support including English, Thai, Vietnamese, Japanese, Bermis or Singaporean lah </br>

[Tokenizer for word sentence to sequence vector]( https://github.com/jkaewprateep/text_to_sequence/blob/main/README.md )

```
# 🧸💬 Create instant of hashing linear model with settings
hashingTF = HashingTF(inputCol="words", outputCol="rawFeatures", numFeatures=10)
featurizedData = hashingTF.transform(wordsData)                              # 🧸💬 Transform data frame by apply hash settings

featurizedData.show(truncate = False)                                        # 🧸💬 Display results or IO output
```

<p align="center" width="100%">
    <img width="40%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/06.png">
</p>
🐑💬 ➰ 🤫 More than hashing we can create data feature extraction by mathematical lessons from class. Hashing can be performed during string lookup but to create more effects apply application support data to your data for better results. </br>

[Mel-frequency response]( https://github.com/jkaewprateep/Mel-Frequency-response/blob/main/README.md )

## ITIDF vectorization ( 🐑💬 ➰ Complexing expressions such as words from human languages and desirable expressions can be vectorized by IDITF algorithm that supports proficiency )

```
idf = IDF(inputCol="rawFeatures", outputCol="features")                      # 🧸💬 Create TIIDF instant object
idfModel = idf.fit(featurizedData)                                           # 🧸💬 Create instant linear model and learning input data
tfidfData = idfModel.transform(featurizedData)                               # 🧸💬 Trained model can apply knowledge on new feature data
tfidfData.select("sentence", "features").show(truncate=False)                # 🧸💬 Display results or IO output
```

<p align="center" width="100%">
    <img width="45%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/07.png">
</p>
🐑💬 ➰ 🤫 Handling proficiency and attributes such as robot word phases or indicate text variables and number of time appearances is typical for file process because of object format type support and they are working as the same as vectorized object identification. </br>

[data model and vocaburary]( https://github.com/jkaewprateep/Simple_encode_decode/blob/main/README.md ) </br>

## StandardScaler ( 🐑💬 ➰ Data training model with settings )

```
from pyspark.ml.feature import VectorAssembler                               # 🧸💬 Import vector assembler library

# 🧸💬 Create an instant vector assembler by its input
assembler = VectorAssembler(inputCols=["Cylinders", "Engine Disp", "Horsepower", "Weight"], outputCol="features")
transformed_data = assembler.transform(data)                                 # 🧸💬 Apply vector assemble settings to new data
transformed_data.select("MPG","features").show(truncate = False)             # 🧸💬 Display results or IO output
spark.stop()                                                                 # 🧸💬 Close and dispose session
```

<p align="center" width="100%">
    <img width="20%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/08.png">
</p>
🐑💬 ➰ 🤫 It features label mapping and you can do both left-to-right or right-to-left in TensorFlow as well as in Spark but you need to create a custom criterian function or loss estimation function for them to learn of the assignment data. </br>

[Grey scales colour data generation]( https://github.com/jkaewprateep/Grayscale_to_colors/blob/main/README.md ) </br>
[Train model n-grams selection]( https://github.com/jkaewprateep/text_as_sequences/blob/main/README.md ) </br>

## NLTK and implementation

### 🦤💬 Lexical diversity - application of the input text words from a document, data generation, speech, and natural languages to find target patterns or matching of the desirable functions is one task of NLTK. Lexical diversity is how significant predicting word or text input from the current process or process is to make them significant to improve the results. </br>

💃( 👩‍🏫 )💬 This memo is simple but can explain how random selection target actions and co-relation finding are different, from the cylindrical secrete you can select any alphabets to create a sequence of word or responding text string to open the lock see the item inside or further create a combination of word from the spherical problem. </br>
💃( 👩‍🏫 )💬 The problem is how to find the response word that makes the secrete breaks that take a short time process ⁉️ </br>
👧💬 🎈 Languages and words are significant this word means because you live in an environment where you are comfortable with continued activities and honesty, you can select an item or recognize of object from the work environment or story you reading on the Internet in case you are not aware of backlog tracking. This method is powerful but effective remember a princess escapes from hidden palance by guessing answers from the questions of the Sultan and go back to take care of her parent. </br>
💃( 👩‍🏫 )💬 In a modern world working with computers and high-power calculation units they create longer and more complex mixtures to prevent her from doing the same, this can create more chance by summing previous input or learning from mistakes and using results feedback to supervised artificial intelligence networks training to perform better than guessing password from dictionary or lexicons dictionary to create a combination. Languages and connections are supreme courts of the process but that is not enough to create an effective process. It will require more techniques to collect some correlation values but we are now studying Lexical diversity and this example can teach about finding action responses it is a process of improving ten or more times iterations to find the satisfaction results from our setting at the beginning of the project. </br>
🧸💬 There are no algorithms to revert back to settings files or applications to find database correlation values but the database correlation values they are using are generated function, tracing backlog or output is clean by the prove method but possible by unmatch or modified secrete encryption library. In example of Oracle you need to use the Oracle database encryption library come with the database installation but some programmer may miss configuration and find external library or previous project library from different versions is matching to the current method of text and secrete encryption. </br>

### Secrete breaks by correlation values response

```
def nhl_correlation(): 
   
    new_nhldf = create_nhldataset( );                                                      # 🧸💬 Create a new dataset from a custom definition.
    new_nhldf = remove_index(new_nhldf, 0);                                                # 🧸💬 Secrete order (1) for target correlation value.
    new_nhldf = remove_index(new_nhldf, 18);                                               # 🧸💬 Secrete order (2) for target correlation value.
    new_nhldf = remove_index(new_nhldf, 21);                                               # 🧸💬 Secrete order (3) for target correlation value.
    ###
    
    win_loss_by_region = np.asarray(new_nhldf["W/L"], dtype=np.float32);                   # 🧸💬 Conversion and assign variable value.
    population_by_region = np.asarray(new_nhldf["Population"], dtype=np.float32);          # 🧸💬 Conversion and assign variable value.

    # 🧸💬 Verification part.
    assert len(population_by_region) == len(win_loss_by_region), "Q2: Your lists must be the same length"
    assert len(population_by_region) == 28, "Q2: There should be 28 teams being analysed for NBA"

    # 🧸💬 Return the target correlation number.
    return stats.pearsonr(population_by_region, win_loss_by_region)[0]
```

[Introduction to Data Science in Python - Michigan University - notes]( https://github.com/jkaewprateep/lessonfrom_Introduction_to_Data_Science_in_Python/blob/main/README.md ) </br>

<p align="center" width="100%">
    <img width="45%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/09.png">
</p>
🐑💬 ➰ 🤫 In the movie I watched the antique secrete chamber had a rubric spherical secrete password on it and they worked synchronized with alphanumeric characters, this is from a book I read about how the ancient scientists try to imagine about tools of gods or beyond technology that even now if this secretes door had been build I may be not able to open it and see someone from another side. </br>    
🥺💬 They always leave some hints to find their name or secret method if there are a lot of infographics and a long time to discovery from a far land and expecting of different culture they should have a little scroll(s) can help to solve of this issue in case of someone need to take care of them by assignment because the power or King is beyond everything that is the first rule of the land. </br>

### Whitespace and word tokenizer

```
text1_reconstituted = ' '.join(list(text1))

tk = WhitespaceTokenizer();                                                                # 🧸💬 For creating word token (separator characteristic ) from whitespaces string formats.
_temp = tk.tokenize(text1_reconstituted);                                                  # 🧸💬 Apply token on the text string object. 

numberof_whitespaces = len(_temp);                                                         # 🧸💬 Find number of words by whitespace.

#################################################################
_temp = nltk.sent_tokenize(text1_reconstituted)                                            # 🧸💬 For creating stntence token.
numberof_sentences = len(_temp);                                                           # 🧸💬 Find number of sentences from the text object.
```

[ University of Michigan - Applied Text Mining in Python - notes ]( https://github.com/jkaewprateep/lessonfrom_Applied_Text_Mining_in_Python/blob/main/README.md ) </br>

### The steady area under ROC curves

🐐💬 This is a simple task to predict action response without proving from the previous input sequence or testing with the same function required, learning algorithms can create vary of result when prediction. </br>   
🦭💬 One secret of this process is we need to treat a fair chance from all possible actions when prediction had some biases, slower and steady perform well with unknown than fast develop. </br> 
🐯💬 I support this reason because of smarter trends to answer questions they know first or communication to people they know when the answer is not guaranteed but steady and continuous is required for the best result. </br>
🐐💬 He could catch the van trunk but he selected the train and do not forget in machine learning remote devices they had 100% accuracy punishment feedback. </br>
🐑💬 ➰ That is because you are connected to the four-wired instead of human input. A drawback accuracy we called it for auto-hack preventions. </br>

```
from sklearn.metrics import auc;

tfidf = TfidfVectorizer(min_df=3);                                                         # 🧸💬 Create TFid object with minimum 3 words appearnce.
vectorNB = MultinomialNB(alpha=0.1);                                                       # 🧸💬 Create Multinomial model with alpha = 0.1
                                                                                           # 🧸💬 Polynomail with multi-coefficients.
vectorNB.fit(tfidf_X_train, y_train);                                                      # 🧸💬 Traning for weights momentum.

tfidf_X_train = tfidf.fit_transform(X_train);                                              # 🧸💬 Array shape property reshape for prediction and train.
tfidf_X_test = tfidf.transform(X_test);                                                    # 🧸💬 Array shape property reshape for prediction.
predictions = vectorNB.predict_proba(tfidf_X_test)[:, 1];                                  # 🧸💬 Prediction from transformed, (label, "array values")

roc_auc_score(y_test, predictions);                                                        # 🧸💬 Integration curve and area under curve, Proxima value.
```

### Networks implemented with word tokenized and dataset categorize, document email fitering

```
document_spam = spam_data[spam_data["target"] == 1];                                       # 🧸💬 Pandas selection for spam target email.
document_nonspam = spam_data[spam_data["target"] != 1];                                    # 🧸💬 Pandas selection for non-spam target email.

document_spam["lenght"] = document_spam["text"].apply( lambda x: len(x) );                 # 🧸💬 Create array of lenght from its input.
avg_length_document_spam = document_spam["lenght"].mean();                                 # 🧸💬 Aveage value of the array create previolusly.

document_nonspam["lenght"] = document_nonspam["text"].apply( lambda x: len(x) );           # 🧸💬 Create array of lenght from its input.
avg_length_nondocument_spam = document_nonspam["lenght"].mean();                           # 🧸💬 Aveage value of the array create previolusly.

```

[ University of Michigan - Applied Text Mining in Python - notes ]( https://github.com/jkaewprateep/lessonfrom_Applied_Text_Mining_in_Python/blob/main/README.md ) </br>

## The n-grams word tokenizers and speech engine processing

👧💬 🎈 In not normal situations some frequencies will not properly respond and to their sources but none famous amplitude frequencies allow to filter of distorted signals for example. </br>

<p align="center" width="100%">
    <img width="50%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/10.png">
</p>
🐑💬 ➰ 🤫 They removed the navigation command and they bring back in version 8 for some systems but it is because of the Dos operation system business case but they still famous and this feature available in the full versions of the operating system and some word processing application. </br>

### Recall effects this also one problem in probability actions prediction for example from the n-grams, in gramms.

👧💬 🎈 In radio signal stereo and frequency responses, the sound is created from the near side and far side as a tube to create amplitude differentiation, this amplitude differentiation removes noises and creates signals with harmonics radio signals frequency, they are radio grammars and communications required of attitudes, the magnitude of frequency accumulator is created to multiply of the effects. It happens inside the radio with high power output without anyone knowing when to listen to them. The recall feedback saved us from using high voltage energy and told us about news and announcements before today the same as reflection light from flash from low battery voltages can create high contrast power that is recall effects. 📸📺📻... </br>         

<p align="center" width="100%">
    <img width="50%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/11.png">
</p>
🦭💬 In n-grams application in speech engine and natural language processing the recall effects is accumulate of probability and increase the chances every time the function predicts for target values. </br> 

[ University of Michigan - Applied Text Mining in Python - notes ]( https://github.com/jkaewprateep/lessonfrom_Applied_Text_Mining_in_Python/blob/main/README.md ) </br>

## Attention networks

👧💬 🎈 In many examples we had presented the teacher-student networks in Tensorflow for speech tasks as attention networks or communications issues solutions. This is one example of attention networks in R studio language, recall effects of model learning from a trained model in R studio language. </br>

<p align="center" width="100%">
    <img width="50%" src="https://github.com/jkaewprateep/machinelearning_apachespark/blob/main/12.png">
</p>
