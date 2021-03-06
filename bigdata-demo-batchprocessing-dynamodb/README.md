# Ankara Cloud Meetup Big Data Demo - [BATCH PROCESSING] Creating AWS DynamoDB Table to Save Batch Analyze Results

1. What is `bigdata-demo-batchprocessing-dynamodb` module?
==============
`bigdata-demo-batchprocessing-dynamodb` explains how to define **AWS DynamoDB** table to store batch analyze results generated by 
batch processing application (`bigdata-demo-batchprocessing-hadoop`).

2. Instructions
==============
1. Go to [AWS DynamoDB](https://console.aws.amazon.com/dynamodb) console and click **Create table**.
   Then you will be redirected to table creation page.
2. Enter name of the table (i.e. `ankaracloudmeetup-bigdata-demo-tweet-batch-analyse-results`), 
   which you want to save realtime results, for **Table name** field.
3. Enter `id` for **Primary key** field and select **String** as type.
4. Remove tick (make unchecked) for **Use default settings** field under **Table settings** section below
   and go to **Secondary indexes** section.
5. Click **Add index**, enter `hour` for **Primary key** field and select **Number** as type.
   Then click **Add index**.
6. Click **Add index** again, enter `day` for **Primary key** field and select **Number** as type.
   Then click **Add index**.
7. Click **Add index** again, enter `month` for **Primary key** field and select **Number** as type.
   Then click **Add index**.
8. Click **Add index** again, enter `year` for **Primary key** field and select **Number** as type.
   Then click **Add index**.
9. So table schema will look like this (Note that `positiveTweetCount`, `negativeTweetCount` and `neutralTweetCount` columns 
   are not defined, but will be specified by the application while saving results):
```
|=======================================================================|
| Column name           | Column type            | Column Explanation   |
|=======================================================================|
| id                    | String <primary key>   | Primary key          |
| hour                  | Number                 | Secondary index      |
| day                   | Number                 | Secondary index      |
| month                 | Number                 | Secondary index      |
| year                  | Number                 | Secondary index      |
| positiveTweetCount    | Number                 | Is specified on save |
| negativeTweetCount    | Number                 | Is specified on save |
| neutralTweetCount     | Number                 | Is specified on save |
|=======================================================================|
```   
10. Click **Create** below and wait until table is created and ready to use.
11. So you will be able to save realtime results generated by consumers.  
    Then you will build and deploy stream processing consumer application to generate and save results.
12. Congratulations!!! You have created your **AWS DynamoDB** table for storing batch analyze results.
