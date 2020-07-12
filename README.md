# Overview (Execute Spark Program on Hadoop Cluster)

<b><i>Apache Spark</i></b> is a BigData Processing library which can run workload 100x faster. Please visit this link (http://spark.apache.org/) to get details information about Apache Spark.

In this tutorial you can get an idea about how to Execute Spark Program on Hadoop Cluster(For Hadoop Cluster GCP "Dataproc" has been used)


# Perquisites:
    1. Java 8 or later
    2. Eclipse or Intellij
    3. GCP Billing Enabled Account (Don't worry GCP provide 300USD free balance after opening an Account)


# What Can be learn from this Code:
I have developed & designed this Sample tutorial project for the person who want to learn Spark(for BigData handling) on **GCP Dataproc** managed **Hadoop Cluster**

# Steps to Run this Project :
       1. Create a Project in GCP
       2. Upload input file into GCP Cloud Storage
       3. Run and Build Package (.jar) & upload to GCP Cloud Storage
       4. Configure GCP Dataproc 
       5. Then Execute the Java Executable(.jar)
 
# 1. Create a Project in GCP
Please visit the following link to get step by step instruction to create a GCP Project.

GCP Project creation link: https://cloud.google.com/appengine/docs/standard/nodejs/building-app/creating-project

<b><i> N.B. Please be remembered that you must need to Enable the Billing Enable Account but you will get 300USD free balance after creating new account and you can delete and stop all services after practicing this tutorial</i></b>

# 2. Upload input file GCP Cloud Storage
You need a Cloud Storage to hold tutorial data. Please follow the following steps to create the GCP Cloud Storage and you have to upload the jar & datafile       
        
        1. Visit this link [https://cloud.google.com/storage/docs/quickstart-console] to create a Bucket
        2. Then create two folder [<b>in</b> & <b>out</b>] inside the bucket
        3. Then upload the input data file[<b>in/2016-stack-overflow-survey-responses.csv</b>] to the <b>in</b> folder of your GCP Bucket 

# 3. Run and Build Package (.jar) & upload to GCP Cloud Storage

At first you have to put your **GCP Cloud Storage Bucket Name** in your source code as follows
 # Example:
 **Before Changing:**
        
        String inputFile = "gs://{gcp_bucket_name}/in/2016-stack-overflow-survey-responses.csv";        
        String outputFile = "gs://{gcp_bucket_name}/out/2016-stack-overflow-survey-responses.csv";
    
 **After Changing (if the bucket name is "test_bucket"): **
 
        String inputFile = "gs://test_bucket/in/2016-stack-overflow-survey-responses.csv";        
        String outputFile = "gs://test_bucket/out/2016-stack-overflow-survey-responses.csv";

Please follow the following steps to Biuld the Source:

       1. Clone the Git Repo by using (git clone ) or Download the source and import it in Eclipse or Intellij IDE to do any customize Code.
       2. Then Go to Physical directory and execute <b><i>mvn clean package</i></b> or You can execute this maven comand from the IDE.
       3. Copy the Generated <b>.jar</b> file to your desired location. (Let's say the Generated **jar** file Name is **SparkWithCloudPro.jar**)
       4. After that please upload the jar file **SparkWithCloudPro.jar** into GCP cloud storage bucket 
 
# 4. Configure GCP Dataproc

       1. In the GCP console, click Navigation menu > Dataproc > Clusters on the top left of the screen / you create write on the Search field "Dataproc" and Enble it.
       2. To create a new cluster, click <b>Create cluster</b>
       3. There are some parameters you can configure when creating a new cluster. Set values for the parameters listed below, leave the default settings for the              other parameters.
                name -> test_sprak
                Region -> us-central1
                Zone -> us-central1-c
                <b>Master node - Machine type</b> ->2 vCPUs (n1-standard-2)
                <b>Worker node - Machine type</b> ->2 vCPUs (n1-standard-2)
    
    Click on Create to create the new cluster. You will see the Status go from Provisioning to Running.
    
 # 5. Submit a Spark job to your cluster
   You have to do it from **Dataproc** browser that is shown at step: 4
      
      1. Select Jobs to switch to Dataproc's jobs view
      2. Click Submit job
      3. Set values for the parameters listed below, leave the default settings for the other parameters.
          Region -> us-central1
          Cluster -> test_spark
          Job type -> Spark
          Main class or jar -> {main clas }
          Arguments -> 100 (This sets the number of tasks)
          Jar files -> {Jar file full path with name from GCP cloud storage bucket}
       4. Click Submit. 
       5. Your job should be shown in the Jobs list, which shows all your project's jobs with their cluster, type, and current status. The new job displays as "Running"—move on once you see "Succeeded" as the Status. And you can get the output file from the <b>out folder of the GCP Stroage Bucket</b>




   
       







      

