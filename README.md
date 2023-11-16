# AWS Set Up for Edukit
## Edukit Tutorial for https://core2-for-aws-docs.m5stack.com/en/getting-started/
------------------------------------------------------------------------------------
- Step 1: Ensure that you have an IAM account created, not the ROOT user, to facilitate the upcoming procedures
- Step 2: Launch VS Code and confirm the installation of PlatformIO (PIO).
- Step 3: Navigate to the upper-left corner, click on "Terminal," and select "New Terminal." Logging into AWS is necessary for working with the edukit, as it requires credentials and endpoints for communication with AWS.
- Step4: In the terminal, execute the following command to log in to AWS: `aws sso login --profile <Profile>` .
![image](https://github.com/NightNovas/AWS-SDP-2023/assets/62362854/cb2b3798-d9da-43db-9079-3f5934700e49)
Performing this in VS Code simplifies the process. After running the command, an AWS website will open for login. Click on the URL provided in the terminal where it says `Successfully logged into Start URL: https://d-91672c1355.awsapps.com/start#`.
- Step 5: After obtaining your credentials, run the command: `aws configure` . This command is crucial for acquiring endpoints. Since AWS uses short-term credentials, failing to run this command will result in incorrect information.
- Step 6:  Update the AWS token after updating the credentials. When you have the token, return to the terminal and execute: `aws configure set aws_session_token <Insert Token Here>`
  ![image](https://github.com/NightNovas/AWS-SDP-2023/assets/62362854/94947643-76a7-4bdd-bdf0-6835e92ad34d)

- Step 7: Confirm the successful update of token credentials by running the command:`aws iot describe-endpoint --endpoint-type iot:Data-ATS` . Note: If you are following the tutorial from https://core2-for-aws-docs.m5stack.com/en/getting-started/, be aware that the provided command is incorrect.
- Step 8: Upon executing the command, you should receive endpoint details as shown below. With this, you can proceed with the upcoming tutorials.
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

