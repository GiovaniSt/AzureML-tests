
# Exploring Automated Machine Learning in Azure ML
In this exercise, I've used the automated machine learning feature in Azure Machine Learning to train and evaluate a machine learning model, then deployed and tested the trained model.

- After creating an Azure Machine Learning subscription at [Azure Portal](https://portal.azure.com), I have provisioned an Azure Machine Learning workspace on left side menu option **Create a resource**.
- Then I created a new Automated ML job on [Azure ML Studio](https://ml.azure.com) using the left side option menu **Automated ML**.
- I used a Web data source available in https://aka.ms/bike-rentals with the following parameters:

    1) Task type: Regression
    2) Primary metric: Normalized root mean squared error
    3) Models: RandomForest and LightGBM 
    4) Validation type: Train-validation split
    5) Compute type: Serverless


- Once I got the best model it trained, I deployed and tested the model with the following endpoint model:

```
{
   "Inputs": { 
     "data": [
       {
         "day": 12,
         "mnth": 4,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 3,
         "workingday": 2,
         "weathersit": 2, 
         "temp": 0.4, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.2 
       }
     ]    
   },   
   "GlobalParameters": 1.0
 }
```

- Finally giving the output:

```
{
  "Results": [
    777.519045919871
  ]
}
```

That's it! My first contact with Azure ML using a dataset of historical bicycle rental data to train a model. The model predicts the number of bicycle rentals expected on a given day, based on seasonal and meteorological features. =)