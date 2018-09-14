## Building-AWS-Comprehend-Lex-ChatBot

### Scenario
This experiment will teach you how to build your own serverless ChatBot and use lambda functions to connect AWS Comprehend and AWS Translation services.

### Prerequisites
* Sign-in an AWS account, and make sure you have select N.Virginia region.
* Download source file from this Github.

### Lab tutorial
This lab has two part, one for lambda creating and one for Lex Chatbot building.

### Create a lambda function
1.  Open the Lambda in the console.
2.  Choose **Create Function**.
3.  Choose **Author from scratch**.
4.  For Runtime, choose **Python 3.6**.

![1.png](/Lex_img/1.png)


5.  For Role, choose **Create a custom role** and set following information:
*  For **Role Description**, enter Lambda execution role permissions.
*  For **IAM Role**, choose **Create a new IAM Role**.
*  For **Role Name**, enter **myLexLambdaRole**.

![2.png](/Lex_img/2.png)

*  For **Policy**, **Edit** it and use the following policy:

        {
          "Version": "2012-10-17",
          "Statement": [{
              "Effect": "Allow",
              "Action": [
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents"
              ],
              "Resource": "arn:aws:logs:*:*:*"
            },
            {
              "Action": [
                "comprehend:DetectDominantLanguage",
                "comprehend:DetectSentiment"
              ],
              "Effect": "Allow",
              "Resource": "*"
            },
            {
              "Effect": "Allow",
              "Action": [
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:DescribeAlarms",
                "cloudwatch:DescribeAlarmsForMetric",
                "kms:DescribeKey",
                "kms:ListAliases",
                "lambda:GetPolicy",
                "lambda:ListFunctions",
                "lex:*",
                "polly:DescribeVoices",
                "polly:SynthesizeSpeech"
              ],
              "Resource": [
                "*"
              ]
            },
            {
                "Action": [
                  "translate:TranslateText",
                  "comprehend:DetectDominantLanguage",
                  "cloudwatch:GetMetricStatistics"
                ],
                "Effect": "Allow",
                "Resource": "*"
              }

          ]
        }
6. Click **Allow**.
7. Go back to Create function page and choose the role you just create and click **Create function**.
8. Paste the lambda script in this Github.

### Set up Lex Chatbot
1. In AWS console, select Lex service.
2. Click **create**.
3. Click **Custom bot** and set following content:
* Type Bot name as **lambda_bot**.
* Choose the Output voice **None**.
* Set the **Session timeout**.
* In COPPA, check **Yes**.

![3.png](/Lex_img/3.png)


4. Click **Create**.   
5. Click **Create intent** and type the intent name as **lambda_bot_intent**.

![4.png](/Lex_img/4.png)


6. Add some sample utterances. (ex. good, bad) 

![5.png](/Lex_img/5.png)

7. In **Fulfillment**, click **AWS Lambda function** and choose the lambda function you've created.
8. It will show the notification to add permission to lambda function, click OK.
9. Click **Build**.
10. After building your Chatbot, click **Test** to type some sentence and make sure it works. (ex. This service is too bad to use!)

![6.png](/Lex_img/6.png)



### Conclusion
* Now you learn how to build your serverless Lex chatbot with sentiment analysis function.

