# End To End Data Engineering Project involing migration of data from On Premise Server to Microsoft Fabric
This an end-to-end data engineering project on the Microsoft Fabric. Where I did data ingestion from a on-premise SQL Server to One Lake using Data Factory workspace to transformation using synapse data engineering workspace levaraging spark, loading to Lakehouse and then copying it to warehouse and creating sql views on top of it , and reporting using PowerBI.

# 💾 Dataset
AdventureWorks is a database provided by Microsoft for free on online platforms. It is a product sample database originally published by Microsoft to demonstrate the supposed design of a SQL server database using SQL server 2008. Here are some key points to know about AdventureWorks:

AdventureWorks database supports a manufacturing MNC named Adventure Works Cycles. It is a sample Online Transaction Processing (or OLTP) database, which is a type of data processing where multiple transactions occur concurrently. These are shipped by Microsoft with all of their SQL server products. For this project I used the Lightweight (LT) data: a lightweight and pared down version of the OLTP sample. [download here](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=ssms)

# 🎯 Project Goals
-> Establish a connection between on-premise SQL server and Microsoft fabric.

->Ingest tables into the Lakehouse.

->Apply data cleaning and transformation using Spark.

->Utilize Synapse Data Warehouse for loading clean data.

->Create interactive data visualizations and reports with Microsoft Power BI.

# 🕵️ Key Insights
💸 Total Revenue by Product Category.

 ->Touring Bikes is the top 1 category generating revenue with 32% followed by Road Bikes with 26% and Mountain Bikes with 24%.

🚻 Revenue by Gender

 ->81% of the revenue is generated by Male customers 19% of the revenue is generated by Female customers

💸 Company through which customers puchased which generated in huge revenue.

 ->Action Bicylcist is the company that invloved in purchases made of around 30,565$.

# 📝 Project Architecture 
 
   ![azure project-1 architecture diagram](https://github.com/PARUCHURI7781/Cloud-Migration-from-On-premise/assets/65880017/80649d64-dcb1-4157-9b9e-c54342c30ecc) 

# 📤 Data Ingestion 

  ![on-premise sql server database](https://github.com/PARUCHURI7781/Cloud-Migration-from-On-premise/assets/65880017/75136831-c43d-4bee-b6c3-8669b902afe5)
  The above is how the required data resides in the database of sql server 
  
### step1: establishing an data gateway on the server where sql server resides. 
    ![gateway connectionh](https://github.com/PARUCHURI7781/Cloud-Migration-from-On-premise/assets/65880017/253b6269-93e9-439d-b573-6aab33665c14)

### step2: Establishing connectionj between data gateway on the server and the fabric account.
    ![connecting gateway to fabric and keep it running](https://github.com/PARUCHURI7781/Cloud-Migration-from-On-premise/assets/65880017/6a4818a9-b1ac-409c-bcba-b3181cfb6727) 
    
#### step3: Leaveraging azure data factory for copying the data tables and storing it into bronze layer 
     ![data pipeline 1](https://github.com/PARUCHURI7781/Cloud-Migration-from-On-premise/assets/65880017/690262e7-8a7f-4d5b-a917-8df6a13b48d6)

     1. we have used activities like lookup activity to fetch all the table names in the information schema of the sql server passed as a query. This also acts as parameterization of table names passed later.
     2. Using for each iterates over each item at one time and then copy activity using the parameterization sumps the data into one lake as delimited text format.
     ![copy activity destination](https://github.com/PARUCHURI7781/Cloud-Migration-from-On-premise/assets/65880017/291ce395-8d27-4c99-8846-9c4a08b2ae0d)
    
