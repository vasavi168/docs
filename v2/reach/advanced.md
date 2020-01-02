# Advanced OBD

Advanced obd is similart to customize sms:

#### Use Case
  
  For example you want to play the name of the user and his details who answered the call.

  Using Advanced OBD we can achieve this

  Step 1 : Prepare File

     You need to create a file with columns containing user information as follow

          mobile  name  emailid  address etc..

  Step 2 : Configuring audio

     Create the voice flow and give it a name for further usage in step3. 

     Add a play a widget, configure the message you want to play as follows


     Example: Dear {{name}} , your emailid is {{emailid}} and address is  {{address}}. If it is correct then press 1 to continue...

     Here {{name}} must match with column name in the uploaded file.

   Step 3 : Call Initiation

      Upload the file  prepared in step1 advanced obd page, and select the flow which you created in step2.