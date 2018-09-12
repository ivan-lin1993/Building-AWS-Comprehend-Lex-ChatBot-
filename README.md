## Building-AWS-Comprehend-Lex-ChatBot

## Scenario
This experiment will teach you how to build a your own ChatBot and use lambda functions to connect AWS Comprehend and AWS Translation services.

## Prerequisites
* Sign-in a AWS account, and make sure you have select N.Virginia region.
* Download source file from this github.

## Lab tutorial

### Create IAM role



### Create a lambda function
1.  Open the Lambda console.
2.  Choose **Create Function**.
3.  Choose **Author from scratch**.
4.  For Runtime, choose **Python 3.6**.
5.  For Role, choose **Create a custom role**. The custom execution role allows the function to detect sentiments, create a log group, stream log events, and store the log events.
6.  Enter the following values:
7.  For **Role Description**, enter Lambda execution role permissions.
8.  For **IAM Role**, choose **Create an IAM role**.
9.  For **Role Name**, enter **LexLambdaRole**.
10. For Policy, use the following policy:

* AmazonLexFullAccess
* TranslateReadOnly
* CloudWatchLogsFullAccess
* ComprehendFullAccess

11. paste the script in this tutorial


### Set up Lex bot
1. In console, type Lex service

2. Click **create**.

3. Click **Custom bot** and set following content:
* Type Bot name as **lambda_bot**
* Choose the Output voice **None**
* Set the **Session timeout**
* In COPPA check **Yes**
  then, **Create**   

4. Create intent and type the intent name as **lambda_bot_intent**
5. Add some utterances.(eg. fine, bad) 
6. In Fulfillment, click **AWS Lambda function** and choose 
7. It will show the notification to add permission to lambda function, click ok.
8. Click **Bulid**.
9. After builded your Chatbot, click **Test** to type some sentense and make sure it work. (eg. Everything will be good)

