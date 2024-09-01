# Mailicious

## Introduction

Mailicious is a Mail Detection as a Service security solution. It provides detection & prevention capabilities for organization mails. Mailicious is composed of 3 major components, each one with an own Github repository.

Mailicious components:

- Detection Engine - This is the detection component, it runs each mail that is sent to him from the organization mail server through our detection pipeline, which is consisted out of various detection modules. 
It sends the classifications to the Backend server and queries him for the decision for every mail (according to the organization policy and detection results). It then sends the decision (BLOCK\ALLOW) back to the mail server.
** In our architecture the Detection Engine is also incharge of handling and saving all the mails attachments - it stores them in directories locally for future analysis and investigation.

- Backend server - The Backend serves both the Frontend server and the Detection Engine by exporting APIs they use for their logic and communication with the DB. 
The backend orchestrates the communication with those parties and the DB and handles logic related to Emails, Analysis, Users, Settings and more. 

- Frontend server - The Frontend server is incharge of the web app. This app presents all the data and offers security management of Mailicious.
The web app allows the security analysts and admins to perform queries and analyze data using charts and filters on their organization emails data. It also allows them to define a policy that fits their organization.
The app connects with the database using the API exported by the BackEnd server.


- Mail server - in order for the mails to be analyzed and verdicted, the organization mail server needs to forward to the Detection Engine every mail he receives and wait for each mail's verdict. 
After receiving the verdict he should forward the mail to it's destination within the organization or drop it.
- Sender Simulator - this is a mock mail client which sends mails to our detection server. It is created for testing the product and debugging purposes.

## Mailicious repos

- Detection Engine: https://github.com/nevo-n/Mailicious-DetectionEngine
- Backend: https://github.com/Niko10/Mailicious-BE
- Frontend: https://github.com/yuvalgv1/Mailicious-FrontEnd

- Sender Simulator: https://github.com/nevo-n/Mailicious-SenderSimulator
- Another python testing scripts repo for testing: https://github.com/eladport/mailicous (please use with care and at your own risk, some scripts contain malicious content used for our detection testing)
  Also, the `postfix_content_filter.py` script is what we use on our PostFix mail server in our lab in order to forward incoming mails for the detection engine for analysis.
