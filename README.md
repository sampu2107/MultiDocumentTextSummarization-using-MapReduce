# MultiDocumentTextSummarization-using-MapReduce
Summarizing Large Text Collection of News Articles Using K-Means Clustering and Topic Modelling based on the MapReduce framework.

The proposed technique is designed using semantic similarity based clustering and topic modeling using Latent Dirichlet Allocation (LDA) for summarizing the large text collection over MapReduce framework. The presented technique is evaluated in terms of scalability and various text summarization parameters namely, compression ratio and ROUGE score is used to measure the performance of the summaries.

Multiple document summarization task has been performed in 5 stages:
TFIDF : Multiple news articles are represented in a vector format using information retrieval technique, TFIDF.
Document Clustering stage : K- Means Clustering technique has been employed on the multi-document text collection to create the text document clusters.
Latent Dirichlet Allocation (LDA) : LDA topic modelling technique has been employed on each individual text document cluster to generate the cluster topics and terms belonging to each cluster topic.
Frequent and Semantic terms: Global frequent and semantic terms are generated from the collection of multiple text documents.
Sentence filtering: For each document, the sentences which are containing the frequent terms and semantic similar terms are selected for participation in the summarized document. Output of this project is the summarized documents of large News Article collections.

#Execution Instructions:
-- SUMMARY --

This is a README file for the project - Text Summarization

-- REQUIREMENTS --

HADOOP Environment and Ubuntu.


-- Running the program --

The input folder should contain the dataset - 

* Before you run the sample, you must create input and output locations in HDFS. Use the following commands to create the input directory /user/vpcl/project/input in HDFS:
$ sudo su hdfs
$ hadoop fs -mkdir /user/vpcl
$ hadoop fs -chown vpcl /user/vpcl
$ exit
$ sudo su vpcl
$ hadoop fs -mkdir /user/vpcl/project /user/vpcl/project/input 

* Move the text files of the collection from the project website, provided to use as input, and move them to the 
/user/vpcl/project/input directory in HDFS. 

$ hadoop fs -put file* /user/vpcl/project/input

-- External JAR Libraries/Dependencies --
mallet-deps.jar
mallet.jar
jaws-bin.jar

Please drop these libraries (provided with links and source code) into '/usr/lib/hadoop' as superuser.


-- Stop Words(Used to filter and rate terms) --
$ hadoop fs -mkdir /user/vpcl/project/stopword  


Put stopwords text file(provided with source) into the above dir.

-- Dict Files (Used to find semantic terms) --
$ hadoop fs -mkdir /user/vpcl/project/dict 

Put dict file contents (provided with source) into the above dir.

* Compile the project class.
To compile in a package installation:

$ mkdir -p build

* From the source directory,
$ javac -cp /usr/lib/hadoop/*:/usr/lib/hadoop-mapreduce/*:. TextSummarizationDriver.java -d ~/build/ -Xlint

* Create a JAR file for the project application.
$ jar -cvf textsum.jar -C ~/build/ .

* Run the project application from the JAR file, by passing the appropriate paths to input and output
$ hadoop jar textsum.jar TextSummarizationDriver /user/vpcl/project/input /user/vpcl/project/output/processed /user/vpcl/project/output/termfreq /user/vpcl/project/output/project /user/vpcl/project/output/inputvector/ /user/vpcl/project/output/kmeans /user/vpcl/project/output/topicterms /user/vpcl/project/output/similarterms /user/vpcl/project/output/summarization /user/vpcl/project/stopword /user/vpcl/project/dict /user/vpcl/project/output/topics /user/vpcl/project/output/semanticTerms /user/vpcl/project/output/Center/inputCenter.txt /user/vpcl/project/output/Iterations/depth_1 /user/vpcl/project/output/Iterations/depth_ /user/vpcl/project/output/KMeansOutput /user/vpcl/project/output/KMeansOutput/part-r-00000 /user/vpcl/project/output/kmeans/ /user/vpcl/project/output/topics/topic

* Output can be seen using the below command:
$ hadoop fs -cat /user/vpcl/project/output/summarization/*

* If you want to run the sample again, you first need to remove the output directory. Use the following command.
$ hadoop fs -rm -r /user/vpcl/project/output 

-- CONTACT --

* Sampath Kumar Gunasekaran (sgunase2@uncc.edu)
* Ajaykumar Prathap (aprathap@uncc.edu)
* Viseshprasad Rajendraprasad (vrajend1@uncc.edu)
