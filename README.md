## Building-AWS-Comprehend-Lex-ChatBot

## Scenario
本次實驗將要教導如何建立一個自己專屬的聊天機器人，並用lambda函數結合情感分析以及翻譯功能。

## Prerequisites


## Lab tutorial
### Create a lambda function
1.  Open the Lambda console.
2.  Choose Create Function.
3.  Choose Author from scratch.
4.  For Runtime, choose Python 3.6.
5.  For Role, choose Create a custom role. The custom execution role allows the function to detect sentiments, create a log group, stream log events, and store the log events.
6.  Enter the following values:
7.  For Role Description, enter Lambda execution role permissions.
8.  For IAM Role, choose Create an IAM role.
9.  For Role Name, enter LexSentimentAnalysisLambdaRole.
10. For Policy, use the following policy:

paste the script

   

