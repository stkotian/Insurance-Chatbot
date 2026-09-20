Introduction

Financial institutions heavily rely on credit risk assessment tools to evaluate the creditworthiness of individuals and businesses. Among these tools, the FICO score is one of the most widely recognized metrics used to predict an individual's likelihood of repaying debt. However, traditional FICO score assessments often lack transparency, leaving individuals unaware of the specific factors contributing to their credit risk.
This project aims to address this issue by developing a machine learning-based web application that predicts a user’s risk performance using their financial and credit-related data. The application goes beyond mere prediction by integrating explainable AI techniques, particularly SHAP (SHapley Additive exPlanations), to provide users with a clear understanding of the key factors that influence their risk performance.
The project leverages a multi-step web interface to collect user data and employs a neural network model to predict the user’s risk as either "Good" or "Bad." SHAP explanations are generated for each prediction, helping users understand which financial behaviors or attributes contributed most to the result. This level of transparency and user interaction makes the application more than just a predictive tool—it becomes a valuable resource for financial decision-making.
The goal of this project is to combine the accuracy and efficiency of machine learning with the interpretability required to foster user trust. In doing so, the application not only aids in assessing credit risk but also provides actionable insights that users can leverage to improve their financial standing.
________________________________________
1. Problem Definition
   
The purpose of this project is to create a machine learning-based application that predicts a user's FICO score risk performance, focusing on transparency and interpretability through explainable AI (XAI). Traditional credit scoring models, while accurate, often lack transparency, which can lead to confusion for users trying to understand why they are assessed as "Good" or "Bad" credit risks.
This project seeks to answer the following questions:
•	How can machine learning be leveraged to predict credit risk with accuracy?
•	How can we make these predictions transparent and interpretable for users?
•	What are the key financial factors driving these predictions, and how can users take actionable steps to improve their financial profiles?
The core objective is to provide users with not only a risk prediction but also an explanation of how their financial data influenced the result. This bridges the gap between opaque machine learning models and user-friendly, interpretable outputs.
________________________________________
2. Methodology
   
The methodology involves several components, ranging from model development and explainability techniques to the implementation of a web-based user interface for data collection and result presentation.
a) model.py:
The model.py file forms the backbone of the machine learning model. The key features are:
•	Neural Network Model:
o	A binary classification model, built using TensorFlow/Keras, predicts whether a user's risk performance will be "Good" or "Bad" based on input features like credit history, delinquencies, and inquiries.
o	The model architecture consists of multiple hidden layers, batch normalization for stability during training, and dropout layers to mitigate overfitting.
•	Regularization and Early Stopping:
o	Early stopping is employed to prevent overfitting, where training stops once the model's performance on validation data ceases to improve.
o	Dropout layers are added to the network to further prevent overfitting by randomly ignoring certain neurons during training.
The dataset includes 23 features, which are scaled and preprocessed before being used to train the model. These features cover essential aspects of credit history, such as the number of satisfactory trades, delinquencies, and inquiries, which are critical in assessing credit risk.
b) explanatory_shap.py:
The explanatory_shap.py file is dedicated to providing explainability to the model predictions:
•	SHAP (SHapley Additive exPlanations): SHAP values assign each feature an importance score for its contribution to the final prediction. This helps users understand which features had the most impact on their predicted risk performance.
•	SHAP Visualization:
o	SHAP plots visually display the contribution of each feature, helping users understand how their financial behavior (e.g., overdue payments, credit inquiries) impacts their credit risk.
o	This method of explainability enhances the model's transparency, making it more user-centric and interpretable.
The SHAP values are integrated into the user interface through the results.html file, where users can visualize and interpret their prediction results.
c) app.py:
The app.py file manages the application’s backend functionality:
•	Flask Web Framework: The app is built using Flask, a lightweight Python framework, to handle routing, form submissions, and predictions.
•	Routing and Prediction:
o	Routes are defined to serve different pages, including the form input page (index.html), the risk calculator (external_risk.html), and the results page (results.html).
o	User inputs are collected through the form and passed to the trained model for prediction. The model's prediction and the SHAP explanations are then returned and displayed on the results page.
The app.py file ensures smooth interaction between the user interface and the machine learning model, providing real-time predictions based on user inputs.
d) index.html
The index.html file provides the multi-step form for data collection:
•	Multi-step Form: Users input their financial details in a step-by-step process. Each step collects crucial information such as:
o	External Risk Estimate: Calculated based on age, employment, income, and assets.
o	Months Since Oldest Trade Open: Reflects the user’s credit history length.
o	Delinquency History: Tracks how many payments were overdue and for how long.
•	Real-time Validation: Input validation ensures users provide accurate and reasonable data for the model.
This approach reduces user confusion by breaking down complex financial details into easy-to-understand steps.
e) results.html
The results.html file displays the prediction results:
•	Prediction Display: The user's predicted risk ("Good" or "Bad") is shown in a circular, color-coded widget. The color and animation of the circle vary depending on the prediction.
•	SHAP Explanations:
o	The SHAP values for the user's prediction are displayed in a separate modal. Users can view a breakdown of which financial behaviors influenced their score and in what direction (positive or negative).
o	Top predictors, both good and bad, are shown as pie charts, providing a visual representation of the key factors that contributed to the result.
This page helps users understand their risk performance and the key financial actions that led to the prediction.
f) external_risk.html:
The external_risk.html page allows users to calculate an external risk score based on personal information:
•	Risk Calculation: Users input data such as age, employment status, annual income, and estimated assets. Based on these factors, a risk value (0 to 100) is calculated.
•	Redirection: The calculated external risk score is automatically passed to the main prediction form in index.html, where it pre-fills the External Risk Estimate field.
This functionality simplifies the process for users, ensuring they can quickly assess their initial risk before proceeding to the full risk performance prediction.
________________________________________
3. Findings
   
The key contributions of this project are the development of a predictive model and a user-friendly application that simplifies financial risk assessment. The main findings are:
•	Model Accuracy: The neural network model achieves high accuracy in predicting a user’s credit risk. It effectively captures relationships between the features and the target variable (Risk Performance).
•	Interpretability: SHAP values successfully explain the model's predictions, highlighting key financial behaviors that influence a user's credit risk. For instance, high delinquency rates negatively impact the prediction, while long credit history improves it.
•	User Experience: The multi-step form and clear presentation of results make the application accessible to users who may not have a strong background in finance. The SHAP explanations ensure that the application is not just a black box but offers actionable insights.
________________________________________
4. Impact and Significance of Results
   
The application offers significant value by:
•	Empowering Users: Users gain a deeper understanding of their financial profile and the factors influencing their credit risk. This transparency encourages responsible financial behavior.
•	Business Applications: Financial institutions can adopt this application as a tool for assessing clients' credit risk, improving customer relationships, and aiding in lending decisions.
•	Advancing Explainable AI: By integrating SHAP values into the user interface, this project demonstrates how complex machine learning models can be made interpretable, a critical factor for AI adoption in sensitive domains like finance.
________________________________________
5. Project Management
   
Project management followed an organized and systematic approach:
•	GitHub: The codebase was maintained on GitHub, ensuring version control and collaboration.
•	Sprint Boards: Trello was used to plan tasks, including model development, frontend design, SHAP integration, and testing.
•	Team Contributions: Each team member played a role in different areas of the project, with clear tracking of contributions and issue resolution.
Challenges such as handling missing data and optimizing model performance were addressed efficiently through research and team collaboration.
________________________________________
6. Presentation Style
   
The project report and the web application were structured in a user-friendly manner:
•	Clear Visuals: All charts and explanations are properly labeled, making it easy for users to interpret their predictions.
•	Well-Organized Content: The report follows a logical flow, covering problem definition, methodology, findings, and impact. The web pages (index.html, results.html, external_risk.html) are clean, intuitive, and responsive.
________________________________________
Declaration of AI Usage
Generative AI tools were used in drafting and organizing the content of this report. However, significant human oversight and original contributions were made to refine and extend beyond AI-synthesized content. The critical analysis, explanations, and methodology showcase a deep understanding of the project, exceeding the outputs generated by AI tools.
