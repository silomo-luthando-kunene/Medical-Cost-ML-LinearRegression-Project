# 🏥 Medical Insurance Cost - Regression Lifecycle Project (README TO BE FINALISED)

This project demonstrates a beginner Machine Learning workflow from exploratory data analysis to model evaluation, aimed at investigating the impact of lifestyle choices on insurance premiums. By analysing the Medical Cost Personal Dataset I developed a Linear Regression, Lasso and Ridge Regularisation model that predicts annual charges with R sqaured value of 0.7836, 0.7806 and 0.7835 respectively. Key highlights include implementing StandardScaler for fair regularization and using Lasso and Ridge models to validate feature significance.

## 🛠️ Project Lifecycle
1. Exploratory Data Analysis.

I investigated the relationship between the independent variables and the target variable (charges).
* **Key Discovery:** Smoking status is the most aggressive insurance premium cost driver.
* **Distribution:** Medical charges are positively skewed meaning most people have low costs but a few outliers have extremely high expenses.

<table width="100%">
  <tr>
    <td width="50%" align="left">
      <img src="https://github.com/silomo-luthando-kunene/Medical-Cost-ML-LinearRegression-Project/blob/main/SmokerBoxPlot.png" width="100%" alt="Smoker Box Plot" />
    </td>
    <td width="50%" align="right">
      <img src="https://github.com/silomo-luthando-kunene/Medical-Cost-ML-LinearRegression-Project/blob/main/ChargesDistribution.png" width="100%" alt="Medical Charges Histogram" />
    </td>
  </tr>
</table>
<br>

2. Data Preprocessing & Scaling.

To ensure the models were accurate and fair I performed the following:
* **One Hot Encoding:** Converted categorical data (Sex, Smoker, Region) into numerical values for ease of use in my Linear Regression Model.
* **StandardScaling:** I applied `StandardScaler` specifically for the **Lasso** and **Ridge** models. This ensured that features with larger raw numbers (like Age) don't unfairly affect features with smaller numbers (like Children) during the regularisation penalty.
<br>

3. Model Performance Comparison.
* I compared a simple **Linear Regression** model against two regularised models (Lasso and Ridge) to check for overfitting and feature significance.

| Model | $R^2$ Score | MAE | MSE | RMSE |
| :--- | :--- | :--- | :--- | :--- |
| **Linear Regression** | 0.7836 | 4181.19 | 33596915.85 | 5796.28 |
| **Lasso (L1)** | 0.7806 | 4210.60 | 34056599.87 | 5835.80 |
| **Ridge (L2)** | 0.7835 | 4182.80 | 33604973.54 | 5796.98 |

<br>

**Note:** Since my R2_score values are consistent/nearly identical, it shows that regularisation (Lasso and Ridge) did not siginifcanty change the performance of the model's output. This is verifies that my initial simple Linear Regression does not overfit. The top 3 cost drivers (Smoker, Age and BMI) are dominant and regularisation did not shrink any coefficients to zero as a result.

## 📈 Key Insights & Results

### Feature Impact (Coefficients)
By visualising the weights assigned by the models, I identified the top 3 cost drivers:
1. **Smoker** (The highest impact by far)
2. **BMI** 
3. **Age** 

<div align="left">
  <h3>Feature Importance Analysis</h3>
  <img src="https://github.com/silomo-luthando-kunene/Medical-Cost-ML-LinearRegression-Project/blob/main/RegularisationModelCoefficients.png" alt="Coefficient Plot" width="550" height="400" />
  <p><i>Comparison of feature importance across models.</i></p>
</div>

### Residual Analysis
I created Linear Regression model residual plots to check for model bias.
* **Finding:** Majority of the residuals are tightly clustered around the zero line while a few clusters are significantly removed from the zero line. Other residuals are dispersed with no clear pattern.
* **Limitation:** The behaviour of tiny clusters away from the zero line especially at higher costs suggests the model is less certain when predicting extremely high medical charges (outliers).

<div align="left">
  <h3>Model Evaluation</h3>
  <img src="https://github.com/silomo-luthando-kunene/Medical-Cost-ML-LinearRegression-Project/blob/main/LinearRegressionResidualsScatterPlot.png" alt="Residual Plot" width="550" height="400" />
  <p><i>Visualising where the model is most and least accurate.</i></p>
</div>
<br>

## 💡 Conclusion
For this dataset, **Linear Regression** is the most efficient choice. While Lasso and Ridge provided stability and confirmed feature importance, the relationship between these specific variables is strongly linear. 

**Next Steps:** In future potential iterations, I will explore **Polynomial Regression** to see if the graph of aging or BMI impact on medical charges can be captured more accurately.

## 🗂️ Project Structure
* `Medical_Cost_Regression.ipynb`: Full Python code and analysis.
* `insurance.csv`: Dataset (Source: Kaggle).
* `README.md`: Project report and summary.

`#machine-learning` `#regression` `#python` `#scikit-learn` `#data-science`
<br>

**NB:** Everything I applied in this project was what I have learned to date in my ALX Africa ML course. My journey into ML is still in a very beginner phase.
