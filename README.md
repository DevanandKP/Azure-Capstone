# Azure-Capstone

ADF- Azure Data Factory, a cloud-based ETL and data integration service that allows you to create data-driven workflows for orchestrating data movement and transforming data at scale.
 
# STEPS:

1. Create a container named 'capstone' for storing the data in your storage account.
![image](https://github.com/DevanandKP/Azure-Capstone/assets/100085173/97cfeeb6-a861-495a-b1c5-e9a390afe91a)

2. Create a folder named 'data' in the container and upload your dataset inside a folder named 'raw'.
![image](https://github.com/DevanandKP/Azure-Capstone/assets/100085173/e2f9c5d2-355a-44e6-bafd-139ee170e686)

3. Create an Azure Databricks workspace named 'devanand_capstone'.
![image](https://github.com/DevanandKP/Azure-Capstone/assets/100085173/64297b22-1a39-47a8-abe7-23d7b0196a75)

4. Now launch that workspace and create a cluster under the compute section.
![image](https://github.com/DevanandKP/Azure-Capstone/assets/100085173/25c1ec25-4cc5-4689-90be-a078bd21de86)

5. Create 3 different notebooks for data preparation, model training and scoring purposes.

6. # Model Creation 

        i. DATA PRE-PROCESSING
           
            A. Fetch your raw data from the blob storage.
     
            B. Read the data and drop the rows with null values.

            C. Apply sting indexer to the dependant variable column, in our case 'species'.

            D. Now create a vector assembler to merge multiple columns into a vector column 'features'.

            E. Now apply feature scaling to the 'features' column to normalize the range.

            F. Now save the dataframe into a new folder named 'processed' inside the 'data' folder inside our 'capstone' blob storage.

        ii. TRAINING AND TESTING
           
            A. Fetch the processed data and split the 70% of the data for training and the rest for testing.
     
            B. Train and test the data using logistic regression.

            C. Train and test the data using decision tree classifier.

            D. Train and test the data using random forest using Random forest classifier and set the hyperparameters.

            E. Now tune the hyperparameters using grid search and search for the best model using cross validation.

            F. Now use Multiclass Classification Evaluator to get the accuracy of all the models.

            E. Store the scores of the models inside a folder named 'model scores' inside our blob storage.

        iii. BEST MODEL
           
            A. Fetch the model scores from the blob storage.

            B. Sort the accuracy of all of the models to find the best one.

            C. Choose the models over 70% accuracy.
            
            D. Store the selected models and their accuracy in a csv file in our blob storage.
            

7. Create a Data Factory named 'devanand-capstone' and launch it.
![image](https://github.com/DevanandKP/Azure-Capstone/assets/100085173/2055d2c5-1df3-4ed8-a83f-c9dff55dffaf)

8. Now go to the manage section and create a linked service for our azure databricks workspace under the comute tab.

        i. Select your subscription, your workspace and your existing cluster.

        ii. Create an access token for your workspace. (databricks workspace ->  click the user icon in the top-right of the UI -> user setting -> access token -> generate new token).
   ![image](https://github.com/DevanandKP/Azure-Capstone/assets/100085173/0a8492d8-f83c-4f67-b38f-3c92f7c5c2e4)

9. Now create a new pipeline under the 'Author' tab.

        i. Drag and drop 3 notebooks from the 'Activities' tab under the 'databricks' section.

        ii. Now click on each of these notebooks, give them names, choose the linked service and add their locations.

        iii. Connect all these notebooks using the 'on success'property.

   ![image](https://github.com/DevanandKP/Azure-Capstone/assets/100085173/5eefa96a-82ec-4f8a-aae6-b880c8c44b16)

10. Click on debug to test run your pipeline.
![image](https://github.com/DevanandKP/Azure-Capstone/assets/100085173/75b6c1a8-19f0-460b-9880-fab98e1a7a85)

11. Select publish all and trigger your pipeline.

12. Check the status of your pipeline runs in the monitor section.
![image](https://github.com/DevanandKP/Azure-Capstone/assets/100085173/8c80cae8-4eab-47eb-812e-3eb568b245a7)
![image](https://github.com/DevanandKP/Azure-Capstone/assets/100085173/cadddc43-a268-4c52-8aa5-32f9b7e2b3ac)
