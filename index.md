# KNOW YOUR CUSTOMER (KYC)

KYC is a way of verifying the identity of the Smartcall's Rica Agents or Customers and assessing their suitability, along with the potential risks intended towards the business.

The KYC System provides automated indentity assessments on Rica Agents and the company's clients in general. The useability of the system is controlled and easy to use.  The assesments is based on the
imformation provided by the customer with crosspondence to their identity documents/files they provide to support and verify the identity.





## KYC System Architecture
All the componets makes Communication through the database.

**KYC component diagram**

*The system component architecture diagram*
![Development Diagram](/img/component.PNG)










## Data collection
Rica agents provides documents for validation and assesments. KYC provides the file upload system for Rica agents to upload their documents. Once the documents are uploaded, then they get stored as  raw data into the KYC_systems database.
Thus, the data goes for data analysis.  


![data collection](/img/data collection.png)
## Data analysis
The data analysis  provides us with document verification, classification(listing type) and data extraction, which helps make rulling for Rica Agents approval or rejection.
Analysis of data consists of Tests, Results and request.

KYC provides Rica Agents administration to the  Rica customers, with the ability to digitally draw and compare identity data against  the one that is provided by the external ApI interface databses, i.e Department of Home Affairs verfied data that 
customers declares to the company against the one obtained by the company.


KYC provider uses intelligent algorithms to do assessments on information and documents provided on agents/customers.
The applications includes computer vision, Machine Learning(ML)/Arificial intelligence(AI), Optical charater recognition(OCR), pbVerify API Services/XDS ID Verification and Openview facial recognition.

 *kyc data analysis component diagram*
![data collection](/img/data analysis.png)

**Google Vision** 

Google vision is a google cloud platform for different API services. We use google vision API to construct data from our Agent documnets provided by extracting the text from them by using google OCR API.
 Thus, We use relavent text to analysis, like ID number and agent name.

 **XDSVeify**

 XDSVerify API is an ID verification tool provide by the third party company, used to aunthentuicate the identity information provided on the South African Citizen identity book.
 We use XDSVerify API to validate the ID documents provided by the agents. It is useful since it is linked with the South African Department of Home Affair Database.

 ***PBverify***

 PBVerify API is also an ID verification tool provided by another third party company. It does the same function as the the XDSVerify. 

 ***Kyc-Death***

 Using the infomation provided by the PBVerify and the XDSVerify analysis, we can determine wether an agent provided information is for a dissed or living. 
 This helps much with identity fraud detection.

**Kyc-SA-ID, Kyc-SA-Drivers, Kyc-Image-ID, Kyc-foreign-passport, Kyc-asslum**:

This are some information provided by the Rica Agents/customers.

**Kyc-Blur**

Once the image is submited it gets assest for quality, once of the of the rules covers bluriness measurements, this helps to chect the quality of the provided documents to check if it be used for further analysis.
Sometimes this helps to gives reason why some of the analysis are giving poor results. The idea will be the higher the bluriness the poorer the analysis/test results.

**Kyc-face-retrivals**

Kyc also provides face extraction intelligent algorithm used to detect and extract faces from the documents provided. Thus, used to verify if the faces extracted and the actual agent face match.

**Kyc Tensorflow and Kyc Pytorch**

This are deep learning (Artificial intelligence) applications used to help with automated agent documents listings or classifications.

**Kyc-image-name**

Once the Classification analysis has been verified, kyc provides naming application for documents listings.

 **persistence systems files review**
![Data Analysis](/img/Persistence Unit agentAnalysis.png)




## Administration

**Front-End**

Kyc is provided with application Front-End Vue for administration and friendly usage of the interface.

![Data Analysis](/img/front-end.png)



##Security

**Authentication**

The RESTful Web Service security uses 2 steps Oath model over Https. Before any further requests for web service can take place succesfully, the user must first be authenticated and use the security token returned in all subsequent calls.



![Autherization](/img/authe.png)

**Authentication error**

401 - Unauthorized

This happens when the user uses wrong token or try to access the web service without authority.

**User Login**

The is system is accessed by Username and password login. The Username and the password are created by administration which enables the Authorization by use of a token.

Once the username and password are created the user can now login into the kyc Front-end Vue.

![Front-end login](/img/login.png)




##Databases

The kyc systems for kyc functional data resides within the Kyc-systems database in Seshat sever Engine.

**Tables**

within the kyc systems database, there resides all the system tables, i.e, tables for testing, training, rules and results.

![Data Analysis](/img/kyc_system.png)

Once all tests are done. The results summary get dumped into the kyc_docs database in the Yoda sever engine,  for storage.

![Database](/img/yoda.png)
![Database](/img/yoda.png)

##Kyc_system Servers

**Internal Servers**

 The components that makes up the servergroups are deployed in [jboss](http://196.35.119.36:9990/console/App.html#domain-deployments) and [potainer](http://196.35.119.167:9000/#/home).
 
 
#On Jboss
There are some components deployed on Jboss and hosted on Vili and Odin.

**Host 1** [Vili](http://baymax.smartcall.co.za/devwiki/index.php/Vili). 

**servergroup-kyc-tools
(server-kyc-tools)**


There are components running on Jboss, hosted on Odin server:



**servergroup-id-verification
(server-id-verification)**

1. Kyc-Analysis-Request

2. Kyc-Image-Analysis

3. Kyc-Rule-Suite-Analysis

 **servergroup-kyc-tools
(server-kyc-tools)**

1. Google vision

2. PbVerify

3. XdsVerify

**Host 3** [Odin](http://baymax.smartcall.co.za/devwiki/index.php/Odin) 

**servergroup-kyc-retrievals-1
(server-kyc-retrievals-1)**

1. Kyc-adress-data-and-rule

2. Kyc-asylum-data-and-rule

3. Kyc-Blur-data-and-rule

4. Kyc-death-data-and-rule

5. Kyc-face-retrivals-and-rule

6. Kyc-Image-ID-data-and-rule

7. Kyc-image-name-data-and-rule

8. Kyc-pbVerify-data-and-rule

9. Kyc-Pytorch-data-and-rule

10. Kyc-Tensorflow-data-and-rule

11. Kyc-SA-ID-data-and-rule

12. Kyc-XDS-data-and-rule

13. Kyc-SA-drivers-data-and-rule

14. Kyc-foreigh-Passport-data-and-rule

#Potainer
Our front-end components are deployed on [potainer](http://196.35.119.167:9000/#/home). This is hosted on **Thoth**.




**External Servers(The DMZ)**




	