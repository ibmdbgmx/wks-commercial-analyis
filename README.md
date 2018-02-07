
# wks-nlu-sms-analysis
![Build Status](https://travis-ci.org/ragudiko/wks-nlu-sms-analysis.svg?branch=master)
![Bluemix Deployments](https://deployment-tracker.mybluemix.net/stats/2beb5ac0f2b130c628328825c48f65c5/badge.svg)
This is cognitive sms client which uses natural language understanding capability to analyze the sms and extracts entity data required.

Background: Current natural language processing techniques cannot extract/interpret the data as required by domain/industry specific. The data(entities) represent different meaning in different domain. Best answer to such problem is IBM Watson Knowledge Studio.
Consider an example where we need to extract entities present in commercial sms.
In such commercial sms usually interesting entities to be extracted are
1. what is the offer
2. who is providing(merchant)
3. offer name(if present in sms)
4. offer validity period

We can also additional info like merchant name, merchant location, merchant website, merchant phone number in case this info is available in sms.

The above requirement can be achieved by using our cognitive sms analysis.

## Maven
If Apache Maven is being used, the following dependency should be included:
```xml
<dependency>
    <groupId>com.ibm.watson.developer_cloud</groupId>
    <artifactId>java-sdk</artifactId>
    <version>1.0</version>
</dependency>
```

## Process Flow

![](doc/source/images/wks-nlu-process.png)

## Technical Architecture

![](doc/source/images/technical_architecture_-_2.png)


## Features
1. User can feed sms to NLU which has machine learning model deployed in it.
2. The NLU analyzes the sms and extracts the domain specific entities.
3. The extracted entities will provide info like what is the offer, who is providing offer and offer valid date etc.

## Create NLU service

![](doc/source/images/nlu/create_nlu_service-1.png)
![](doc/source/images/nlu/create_nlu_service-2.png)
![](doc/source/images/nlu/create_nlu_service-3.png)
![](doc/source/images/nlu/create_nlu_service-4.png)
![](doc/source/images/nlu/create_nlu_service-5.png)

## Create WKS model and deploy the model to nlu
1. Create wks service instance
![](doc/source/images/wks/dashboard.png)
![](doc/source/images/wks/creating_knowledge_studio_service-1.png)
![](doc/source/images/wks/creating_knowledge_studio_service-2.png)

2. Create workspace
![](doc/source/images/wks/knowledge_studio_launch_page.png)
![](doc/source/images/wks/workspace_page.png)
![](doc/source/images/wks/create_new_workspace.png)
![](doc/source/images/wks/workspace_creation_done.png)

3. Create Type System (Step 3 is provided for reference, you can go directly to step 4)
![](doc/source/images/wks/type_system-1.png)
![](doc/source/images/wks/type_system-2-_create_type_system_entry.png)
![](doc/source/images/wks/type_system-3-_type_system_entry_saved.png)

4. Import Type System
![](doc/source/images/wks/type_system-4-_upload_type_system_entry.png)
![](doc/source/images/wks/type_system-5-_entries.png)
![](doc/source/images/wks/type_system-6-_create_relation_entry.png)
![](doc/source/images/wks/type_system-7-_relation_entries.png)

5. Upload Documents (Step 5 is provided for reference, you can go directly to step 6)
![](doc/source/images/wks/documents-1-page.png)
![](doc/source/images/wks/documents-4-upload_documents.png)
![](doc/source/images/wks/documents-3-upload_documents.png)
![](doc/source/images/wks/documents-4-upload_documents.png)
![](doc/source/images/wks/documents-5-upload_documents.png)

6. Import Corpus Documents
![](doc/source/images/wks/documents-4-upload_corpus_documents.png)
![](doc/source/images/wks/documents-6-rename.png)
![](doc/source/images/wks/documents-7-rename.png)

7. Create Annotation Set
![](doc/source/images/wks/documents-9-create_annotation_set.png)
![](doc/source/images/wks/documents-10-create_annotation_set.png)

8. Create Task for Human Annotation
![](doc/source/images/wks/task-1-page.png)
![](doc/source/images/wks/task-2-create_task.png)

### Select Annotation Set for this task
![](doc/source/images/wks/task-3-create_task-select_annotation_set.png)
![](doc/source/images/wks/task-4-task_created.png)
![](doc/source/images/wks/task-5-list_of_annotation_set_for_this_task.png)
![](doc/source/images/wks/task-6-list_of_documents_within_annotation_set_chosen.png)
![](doc/source/images/wks/task-7-start_annotation-ground_truth_editor.png)

### Start Human Annotation clicking Annotate button
![](doc/source/images/wks/task-8-annotation-ground_truth_editor.png)
![](doc/source/images/wks/task-9-annotation-ground_truth_editor.png)
![](doc/source/images/wks/task-10-annotation-ground_truth_editor.png)
![](doc/source/images/wks/task-11-annotation-ground_truth_editor.png)
![](doc/source/images/wks/task-12-annotation-documents_status.png)
![](doc/source/images/wks/task-13-annotation-documents_status.png)

### Submit Annotation Set for which human annotation is complete
![](doc/source/images/wks/task-14-annotation-submit_annotated_documents.png)
![](doc/source/images/wks/task-15-annotation-documents_completed_status.png)
![](doc/source/images/wks/task-16-annotation-green-status_completed.png)
![](doc/source/images/wks/task-17-annotation-annotation_set_-submitted_status.png)
![](doc/source/images/wks/task-18-annotation-annotation_set_-accept.png)
![](doc/source/images/wks/task-19-annotation-annotation_set_-accept.png)
![](doc/source/images/wks/task-20-annotation-annotation_set_-accept-status_completed)

### Create model, train and evaluate
![](doc/source/images/wks/model_training_and_evaluation-1.png)
![](doc/source/images/wks/model_training_and_evaluation-2.png)
![](doc/source/images/wks/model_training_and_evaluation-3.png)
![](doc/source/images/wks/model_training_and_evaluation-4-training_in_progress.png)
![](doc/source/images/wks/model_training_and_evaluation-5-training_and_evaluation_completed.png)
![](doc/source/images/wks/model_training_and_evaluation-6-logs.png)
![](doc/source/images/wks/model_training_and_evaluation-7-multiple_training_and_evaluation_completed.png)

### Deploy the Machine Learning model to NLU
![](doc/source/images/wks/model_deployment-1.png)
![](doc/source/images/wks/model_deployment-2.png)
![](doc/source/images/wks/model_deployment-3.png)
![](doc/source/images/wks/model_deployment-4.png)




Usage
You can run simple java client provided in this project to extract the entities from sms.

Alternatively you can use the curl commands.

NLU without wks model

curl -u "username":"password" "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=DUNKI%20DONUTS%20is%20now%20open%20at%20Girgaum%20Chowpatty.%20Walk-in%20and%20enjoy%20the%20Valentaine%20SPL%20offer%20on%20your%20favorite%20Donuts.%20Buy%203%20%26%20Get%203%20FREE.%20Valid%20till%2015%20Feb%202017.%20T%26C&features=entities"

Output:{ "language": "en", "entities": [ { "type": "Company", "text": "DUNKI DONUTS", "relevance": 0.976076, "count": 1 }, { "type": "GeographicFeature", "text": "Girgaum Chowpatty", "relevance": 0.65276, "count": 1 } ] }
The api is able to capture company(merchant) and location which are generic entities. It fails to extract the offer details as per our expectation.

NLU with WKS model

curl -u "username":"password" "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=DUNKI%20DONUTS%20is%20now%20open%20at%20Girgaum%20Chowpatty.%20Walk-in%20and%20enjoy%20the%20Valentaine%20SPL%20offer%20on%20your%20favorite%20Donuts.%20Buy%203%20%26%20Get%203%20FREE.%20Valid%20till%2015%20Feb%202017.%20T%26C&features=entities&entities.model=10:a5172791-b31b-4b0d-b546-3610ec652ca4"


Output:{ "language": "en", "entities": [ { "type": "Merchant", "text": "DUNKI DONUTS", "count": 1 }, { "type": "Location", "text": "Girgaum", "count": 1 }, { **"type": "Offer", "text": "Get 3 FREE", "count": 1 }, { "type": "Offer_Period", "text": "Valid till 15 Feb 2017", "count": 1 }, { "type": "Term_and_Conditions", "text": "T&C",** "count": 1 } ] }

### If we look the entities extracted in the form of json, we got the domain specific entities like offer, offer period, merchant. The model I used is trained and evaluated based on few sample sms. The sample sms are available under data folder.

Once you build wks model and NLU api service you can replace username/password highlighted with your NLU service credentials. Replace wks model id(entities.model) with your wks model id. The sms text has to be URL encoded as it is passed as url query string in Curl command.

## Run JUnits using maven command
Download Maven : https://maven.apache.org/download.cgi

Install Maven: https://maven.apache.org/install.html

Configure maven: Open .bash_profile if exists, else create new .bash_profile file. Make below entries into .bash_profile file.

-- -- entry starts

JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.7.0_40.jdk/Contents/Home

export JAVA_HOME


M2_HOME=/usr/local/apache-maven/apache-maven-3.1.1

export M2_HOME

PATH=$PATH:$JAVA_HOME/bin:$M2_HOME/bin

export PATH

-- -- entry ends

Now from terminal run below command

mvn test

# Get your hands on with the NLU api and WKS tool
You can register at https://console.bluemix.net to access NLU.

You can try free version of WKS by logging into https://console.bluemix.net and select knowledge studio service under Watson

## Additional Resource
You can refer https://github.com/rameshpoomalai/ProcurementSystem for procurement use case where we have used WKS, Discovery and IBM Graph.

## Deploy the App

   [![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/ragudiko/wks-nlu-sms-analysis)
