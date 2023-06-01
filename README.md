# Project4_Used-Cars-Prediction

# Objective: 

The objective of this project is to develop a deep learning model for predicting the prices of used cars. By utilising advanced machine learning techniques, the model will analyse various factors such as car specifications, year model, mileage, brand, and other relevant features to accurately estimate the market value of a used car. The predictions will enable potential buyers and sellers to make informed decisions and negotiate fair prices based on reliable and data-driven insights. The ultimate goal is to provide a reliable and efficient tool that assists in the decision-making process of buying or selling a used car.

# Process:

1. Data collection (web scraping) 
2. Data cleaning (drop columns and rows, null values, datatypes, etc.)
3. Data analysis and visualisation (plots and regression models)
5. Analysis of the results
6. Tableau (dashboard)

# Data collection

* Method: Web scraping.
* Tools used: BeautifulSoup, spliter, selenium.webdriver (chromedriver).
* Soruce: https://www.autotrader.com.au/ , https://www.autotrader.com.au/for-sale/wa/perth?distance=25
* Scope: Perth WA, 25km radius from postcode 6000.
* Pages scraped in the website: 251 (timeframe: 12 hours approx).
* Data size: 57 columns, 5671 records (many duplicates due to interruptions of a random survey prompt that stopped the scraping process). Records expected: 3,000.
* Data collected: 'Year model', 'Car Spec', 'Kilometres', 'Seller type', 'Price', 'Transmission', 'Body type', 'Drive type', 'Engine', 'Fuel type', 'Fuel consumption', 'Colour ext / int', 'Registration', 'Rego expiry','VIN', 'Stock No', 'ANCAP Safety rating', 'Green overall rating','Dealer', 'Address', 'Seating capacity', 'Doors', 'Front tyre size',       'Front rim size', 'Rear tyre size', 'Rear rim size','Injection / Carburation', 'CC', 'Number of cylinders','Front suspension', 'Rear suspension', 'Front brakes', 'Rear brakes', 'Fuel tank capacity', 'Valve gear type', 'Maximum torque', 'Maximum power (kW)', 'CO2 level (g/km)', 'Green house rating', 'Overall HxWxL', 'Ground clearance unladen', 'Wheelbase', 'Kerb weight', 'Turning circle', 'Rear track', 'Front track', 'Gross trailer weight braked', 'Make', 'Model', 'Variant', 'Series', 'Warranty when new (months)', 'Warranty when new (kms)', 'Service interval (months)', 'Service interval (kms)', 'Country of origin', 'Vehicle segment'.
* Output: csv file (output_from_1_to_251.csv).

# Data cleaning

* Method: Drop columns, drops rows, drop null values, remove duplicates, change datatypes, binning/grouping values, rename columns, regex, get latitude and longitude.
* Tools used: Pandas / Pandas DataFrame, Geoapify (request).
* Data size: 27 columns, 2126 records. 
* Data cleaned columns: 'Year model', 'Car Spec', 'Kilometres', 'Price', 'Transmission', 'Body type', 'Drive type', 'Fuel type', 'Fuel consumption per 100km', 'Colour ext', 'VIN', 'Dealer', 'Address', 'Seating capacity', 'Doors', 'CC', 'Number of cylinders', 'Fuel tank capacity', 'Valve gear type', 'Peak torque (Nm)', 'Horsepower', 'Kerb weight', 'Make', 'Model', 'Variant', 'Lat', 'Lon'.
* Output 1: csv file test before the geoapify call is executed (used_cars_dataset_test.csv)
* Output 2: csv file inclduing location after the geoapify call is executed (used_cars_dataset_loc.csv)
* Output 3: csv file after validating lat a lon were received correctly and adjusted (used_cars_dataset_complete.csv)

# Data analysis and visualisation
* Method: Supervised learning (linear regression and random forest regression).
* Tools used: Scikit-learn, Seaborn, Matplotlib, Pandas / Pandas DataFrame.
* Process:
1. Read the data and execute a descriptive analysis of the numercal values. 
2. Understand the distribution of the data and the relationships between different variables and the target variable 'Price'. Plots of numerical and categorical data.
3. Preprocess the data (StandardScaler and get_dummies())
4. Regression models by using LinearRegression and RandomForestRegressor.

# Analysis of the results: 

1. Plots of the distribution of the data and the relationships between different variables and the target variable 'Price'. Also display the correlation value:

- Numerical data:

![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/88ef6339-a1f0-4de5-8ad4-6143dbd5e4b8)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/d326470c-3609-4577-a389-2090beb3d658)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/4fbd673f-edc5-44c2-b8ac-62e7f9105c61)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/4486b191-2175-465c-b878-516412f98928)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/d5877b78-b1d8-499c-bacc-293315f81b2b)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/7f6be4b5-a0f0-4161-8f8f-3a3c7c05e49c)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/36ca91f4-5650-428b-9a2a-5556e1bd26fd)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/0317a1af-c1cf-4c13-9f40-8e99d170b58e)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/dd9c563d-d4fd-4015-b303-e26186acfb1a)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/0a0dafbe-8734-4a07-831e-9945639a51d5)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/6cfadf37-5baa-48a8-8bbc-39eef3195e07)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/5f133c2a-afa4-4a7d-a538-aad4e640c458)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/f96c110c-f34f-49ff-a1df-463e4ddc701e)

- Categorical data:

![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/8dea48c6-e9bd-4565-827f-99ed93ee303f)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/6f94ff8a-6133-46ff-9998-1a1d8853cf29)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/a620a914-988f-439f-9236-dac14700eecf)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/e9a986b5-878d-4a84-b692-5daf55ddf802)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/053d27e8-3381-42fd-b89c-cb0b99e78b62)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/9723d423-768b-4a7a-9b70-689abae9066d)

2. Based on the results from the plots. Variables selected for the regression models are:
'Year model', 'Kilometres', 'Price', 'Body type', 'Drive type', 'Fuel type', 'CC', 'Number of cylinders', 'Fuel tank capacity', 'Valve gear type', 'Peak torque (Nm)', 'Horsepower', 'Kerb weight', 'Make'.

3. Train and test data:

![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/ec9d4592-fffd-47ae-a6c0-81d673758fe1)

4. Linear Regression model results

![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/59a7d352-f24e-4f04-88d2-16d813538d17)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/65dddeea-c82a-4c4c-ab1e-5d82fe8d44fc)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/0a9b010a-e1be-4084-b1be-66ad7e5b7eec)

5. Randome Forest model results

![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/ddc11c0b-3be0-4c15-b477-108313b3496c)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/40efdb3b-5272-47b4-9809-ffc15ba132b7)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/a087d905-43a6-484f-8e1a-5a0c1ddd6393)
![image](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/651f6f57-40ce-4972-9699-f3bb4f8acd09)

# Tableau dashboard

![used_cars_dashboard](https://github.com/Martinezj93/Project4_Used-Cars-Prediction/assets/89439553/499976b4-9a59-40bc-a9b5-8d8981bb8272)

# Conclusions

In this project, we aimed to develop a model for predicting the prices of used cars using advanced machine learning techniques. Two models, namely Linear Regression and Random Forest Regressor, were employed to accomplish this objective.

The Linear Regression model achieved a model score and R2 score of approximately 0.833, indicating that it can explain around 83.3% of the variance in used car prices. The mean squared error (MSE) was 90,012,996, suggesting an average squared difference between the predicted and actual prices. The root mean squared error (RMSE) was 9,587.57, indicating an average difference between the predicted and actual prices. Overall, the model demonstrated reasonable performance, but there is room for improvement.

The Random Forest Regressor outperformed the Linear Regression model with a model score and R2 score of approximately 0.904, indicating that it can explain approximately 90.4% of the variance in used car prices. The mean squared error (MSE) was 50,134,431, significantly lower than the Linear Regression model. The root mean squared error (RMSE) was 7,061.05, indicating a smaller average difference between the predicted and actual prices. The Random Forest Regressor exhibited higher accuracy and performed better in capturing the complex relationships among the features.

Moreover, the Random Forest Regressor provided insights into the importance of different features for predicting used car prices. The top five important features, in order of importance, were the number of cylinders, kilometers driven, year model, valve gear type, and drive type. These findings can guide potential buyers and sellers in considering the crucial factors that influence the prices of used cars.

Overall, the Random Forest Regressor yielded superior results compared to the Linear Regression model, showcasing its ability to accurately predict used car prices. The predictions generated by this model can assist potential buyers and sellers in making informed decisions and negotiating fair prices based on reliable and data-driven insights. However, further analysis and optimization can be pursued to enhance the model's performance and provide more precise estimations of used car prices.
