
# Performance Assessment: D208 Predictive Modeling Task 1 - Multiple Linear Regression.

## Michael Hindes
Department of Information Technology, Western Governors University
<br>D208: Predictive Modeling
<br>Professor Dr. Straw
<br>February 11, 2024


This project aims to understanding the exact relationship between a response and predictor variables and to create a multiple regression model derived from medical raw data, targeting a business question reflective of a real-world organizational challenge. Python is employed to conduct a multiple regression analysis to explore the research question thoroughly. The analysis is supported by visual aids. The process also involves  data cleaning to ensure accuracy and reliability. Additionally, the project shares the code used for the regression analysis, predictions and cleaning and wrangling. It concludes by detailing the regression equation, evaluating the statistical and practical significances, discussing limitations, and suggesting possible actions.

# Part I: Research Question
## Describe the purpose of this data analysis by doing the following::

### **A1. Research Question:**
**"A1. Research Question:
"What factors contribute to the length of a patient's hospital stay?"**

This question aims to identify key variables within the dataset that influence `Initial_days`, including possible financial aspects, services rendered, and patient risk factors. Understanding the primary drivers behind the length of a patient's hospital stay is crucial for multiple reasons. First, it allows healthcare providers to identify potential areas for improving operational efficiency, such as optimizing bed utilization and reducing wait times for incoming patients. Second, by recognizing which factors significantly impact hospital stay durations, healthcare professionals can tailor patient care plans more effectively, potentially leading to improved patient outcomes and satisfaction. Third, insights from this analysis can inform hospital administration decisions regarding resource allocation, staffing, and policy development, ensuring that the healthcare facility can better manage its resources while maintaining or enhancing the quality of care provided to patients. Lastly, given previous analyses on the dataset, there may be certain correlation between the number of days patient was hospitalized and his higher risk for readmission, which is costly to hospitals. Thus, the goal of this research is not only to uncover the underlying factors affecting hospital stays but also to leverage this understanding to facilitate better hospital management practices and improve overall patient care.



### **A2. Define the goals of the data analysis.**

This data analysis project is focused on developing a predictive model as a practical tool to help healthcare organizations in planning, patient care, and operational improvements. By examining a wide range of factors that potentially affect Initial_days, the project aims to understand any relationships initial_days may have with other variables. With that understanding, it seeks to build a model that supports data-driven decision-making in healthcare. The goals of the data analysis are as follows:

- Ensure Data Quality and Integrity: Prioritize data cleaning and preprocessing to ensure the dataset's accuracy, completeness, and consistency. This involves identifying and addressing missing values, outliers, and errors in the data. A clean dataset is fundamental for reliable analysis and modeling, enabling more accurate predictions and insights.

- Identify Key Predictors: Determine which variables significantly influence the length of hospital stays, considering a broad spectrum of factors, including but not limited to demographic information, medical history, financial aspects, and services received during the stay.

- Quantify Relationships: Establish how selected variables are related to Initial_days, quantifying the strength and nature of these relationships to provide actionable insights.

- Develop a Predictive Model: Create a multiple linear regression model that can accurately predict the length of a patient's hospital stay based on the identified variables, aiding in the anticipation of hospital capacity needs.

- Inform Policy Making: Provide evidence-based recommendations to healthcare administrators and policymakers for developing policies that address the key factors contributing to the length of hospital stays, with the goal of improving overall healthcare efficiency and patient satisfaction.


-------------------------------------

# Part II: Method Justification

## B. Describe multiple linear regression methods by doing the following:

### **B1. Summarize four assumptions of a multiple linear regression model:**

In multiple linear regression analysis, four key assumptions are critical: linearity between variables, independence of observations, constant error variance (homoscedasticity), and normal distribution of error terms. Understanding and checking these assumptions is essential for the model's reliability and accuracy, providing a solid basis for predictive analytics.

-   **Linearity** asserts that there is a straight-line relationship between each predictor (independent variable) and the response (dependent variable). This means that changes in a predictor variable are associated with proportional changes in the response variable.

-   **Independence of Observations** indicates that the data points in the dataset do not influence each other. Each observation's response is determined by its predictor values, free from the effects of other observations in the dataset.

-   **Homoscedasticity** refers to the requirement that the error terms (differences between observed and predicted values) maintain a consistent variance across all levels of the independent variables. This constant variance ensures that the model's accuracy does not depend on the value of the predictors.

-    **Normality of Errors** involves the assumption that for any fixed value of an independent variable, the error terms are normally distributed. This normal distribution is central to conducting various statistical tests on the model's coefficients to determine their significance.

(Statology, n.d.)
(Pennsylvania State University, n.d.)

### **B2. Describe two benefits of using Python for data analysis:**

- **Rich Libraries:** While R was specifically designed with statistics and data analysis in mind, Python distinguishes itself with its comprehensive suite of libraries that cater to virtually every phase of the data analysis process. Libraries such as Pandas for data manipulation allow for efficient handling and transformation of data, NumPy for numerical computations supports complex mathematical operations with ease, and Matplotlib along with Seaborn for visualization enable the creation of insightful and high-quality graphs and charts. Moreover, Scikit-learn offers a robust platform for applying machine learning algorithms, streamlining the development of predictive models. These libraries not only facilitate a wide range of data analysis tasks but also ensure that analysts have the tools needed to tackle complex data challenges effectively.

- **Versatility** Python's syntax is known for its intuitive and readable nature, making it an accessible choice for professionals across various domains, from data science to web development. This versatility extends Python's utility beyond data analysis to other applications such as web development, automation, and deep learning, through frameworks and libraries like Flask, Selenium, and TensorFlow respectively. For instance, an analyst can easily switch from analyzing data to deploying a machine-learning model as a web application within the same programming environment. This seamless integration across different tasks enables a smooth workflow and promotes a holistic approach to problem-solving in today's interconnected digital landscape.

### **B3. Explain why multiple linear regression is an appropriate technique for analyzing the research question summarized in part I:**

Multiple linear regression is particularly suited for addressing the research question at hand, as it facilitates the exploration of how several independent variables collectively influence a single continuous dependent variable, in this case, `Initial_days`. This analytical technique is adept at not only identifying but also quantifying the strength and nature of the relationships between Initial_days and various predictors, such as financial aspects, services rendered, and patient risk factors. By accounting for multiple factors simultaneously, multiple linear regression can provide nuanced insights into their combined effects on the length of a hospital stay. This comprehensive understanding is crucial for building robust predictive models that can inform decision-making processes.

# NEEDS EDIT
 Part III: Data Preparation

## C. Summarize the data preparation process for multiple linear regression analysis by doing the following:

### *C1. Describe your data cleaning goals and the steps used to clean the data to achieve the goals that align with your research question including your annotated code.**

*   **Importing the Data**: Use`pd.read_csv()` to import data into a Pandas DataFrame.
    
*   **Initial Data Examination**: Using `df.head()` provides a quick snapshot of the dataset, including a view of the first few rows. This helps in getting a preliminary understanding of the data's structure and content.
    
*   **Checking Data Types**: The `df.info()` method is used for assessing the dataset's overall structure, including the data types of each column and the presence of non-null values. 
    
*   **Identifying Duplicate Rows**: Utilizing `df.duplicated()` to find duplicate rows is an essential cleaning step. Duplicates can skew your analysis and lead to inaccurate models. Once identified, you can decide whether to remove these rows with `df.drop_duplicates()` depending on their relevance to your research question.
    
*   **Detecting Missing Values**: The `df.isnull().sum()` command is instrumental in identifying missing values across the dataset. Understanding where and how much data is missing is critical for deciding on imputation methods or if certain rows/columns should be excluded from the analysis.

*   **Outlier Management Strategy:**: In this dataset, outliers are important to detect and be aware of. Particularly when creating predictive regression models. For example outliers can have a detrimental effect on our regression assumption and the model itself(MIDDLETON VIDEO) If there are outliers present, make sure that they are real is important. However, in the context of medical data, outliers can have an extra level of nuance. This is because in medical data, outliers are often the very things that we are interested in. For example, a patient with a very high cholesterol level or a very low blood pressure. These values are not errors, but rather important indicators of health conditions.

- Therefore, in this analysis, we will look for outliers and pay close attention to the details of the variables themselves. Outliers will be noted, but not necessarily treated unless they are obvious data entry errors or if they hinder our model.

*    **Reviewing Unique Values**: Although `df.unique()` is used to explore unique values in a Series, for dataframes, you might consider `df.nunique()` to see the number of unique values in each column or use `df['column_name'].unique()` to check unique values in specific columns. This step is valuable for understanding the diversity of information within your dataset, particularly for categorical data.

*   **Drop Unnecessary Columns**: Any columns that are not relevant to the research question or the predictive model will be dropped from the dataset. 

*   **Categorical variable conversion**: Categorical variables will be transformed into numerical formats. Demographic data, which represents static information about patients and cannot be altered by the hospital, will be excluded from the analysis. We will identify and address any missing data, ensuring its proper mitigation. Additionally, any duplicate records identified in the dataset will be eliminated."



