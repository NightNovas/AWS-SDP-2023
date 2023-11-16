# AWS Set Up for Edukit
## Edukit Tutorial for https://core2-for-aws-docs.m5stack.com/en/getting-started/
------------------------------------------------------------------------------------
- Step 1: Make sure you have your IAM account made not the ROOT user in order to make the following steps work
- Step 2: Open VS code and gmake sure you have platformIO(PIO) installed
- Step 3: On the upper left click on terminal and the new terminal. We will have to log in into AWS. This is something you have to do if you want to work with the edukit since it need the credentials and endpoints for the edukit to communicate to the aws.
- Step4: In the terminal write the following command to log in to aws `aws sso login --profile <Profile>` . This can be done in the CMD that windows has but doing it in VS code it makes it easier. Once you run the command it will launch a aws website for you to log into. 
![image](https://github.com/NightNovas/AWS-SDP-2023/assets/62362854/cb2b3798-d9da-43db-9079-3f5934700e49)
where it says `Successfully logged into Start URL: https://d-91672c1355.awsapps.com/start#` in the terminal click the URL it gives you. This will allow you to enter the AWS account where you will need to get the command line information
- Step 5: Once you have your credentials you want to run the command `aws configure` . You NEED to run this always or else you will not be able to get your endpoints. Since AWS uses short term credentials the ones you have from the account change and the token you have on the host machine will not be the correct.
- Step 6: Once you have updated the credentials you will need to update the aws token.
  ![image](https://github.com/NightNovas/AWS-SDP-2023/assets/62362854/7f1232d1-5106-434e-858f-6846abde1265)
  Once you have the token go back to the terminal and type the following `aws configure set aws_session_token <Insert Token Here>`
- Step 7: The token credentials have been updated you can confirm that everything is good if youre able to get the end point credentials by running this command which is needed for the endpoints in the tutorials ahead. `aws iot describe-endpoint --endpoint-type iot:Data-ATS` . NOTE: If you are the following the tutorial from https://core2-for-aws-docs.m5stack.com/en/getting-started/ you will notice that the command they give you is wrong.
- Step 8: When you run the command you should be able to get end point like the picture below. After this you should be able to continue with the tutorials
  ![image](https://github.com/NightNovas/AWS-SDP-2023/assets/62362854/3d8a4cc0-942f-483d-8711-dc1f999beab6)

  # Notable Errors You Might Encounter
   ------------------------------------------------------------------------------------
## Error 1:

![image](https://github.com/NightNovas/AWS-SDP-2023/assets/62362854/cd7ea877-b57a-487e-bb80-e0e8de997af8)

The fix for this error is a simple one. You have to go to your host machine files and change the values on a file. 
if you go to `core2-for-AWS-IoT-Edukit>Blinky-Hello-World>Utilities>AWS_IoT_registaration_helper` Here you will find the `requirements.txt` where you will have to open the file and where it says hidapi change the line to this one `hidapi==0.14.0`. Save and exit and the code should work.

## Error 2:

![image](https://github.com/NightNovas/AWS-SDP-2023/assets/62362854/92d53a88-dfcd-4740-9502-751c250cb31c)

If you get this error it means that you have a endpoint issue and your credentials are not providing a endpoint to the aws. Follow the steps on how to update the token and it should be fine after that.

