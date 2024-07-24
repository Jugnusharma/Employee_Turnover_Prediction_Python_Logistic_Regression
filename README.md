# Turnover_Prediction_Python_Logistic_Regression
How to predict the turnover possibility of employees in a company

**Executive Summary:**
To express the relationship between non-linearly related dependent and independent variables, we use nonlinear regression analysis. Here, I will introduce one of the most popular nonlinear regression techniques: Logistic Regression, using Python. Logistic regression examines the relationship between dependent variables, which can only take one of a set of values, and independent variables, using probability theory. The response variable in logistic regression is always binary (e.g., 1 or 0), but the independent or predictor variables can be continuous or categorical.

**Business Case:**
Predicting employee turnover is crucial because it helps companies save on the costs associated with recruiting and training new employees, maintain productivity by retaining experienced staff, and improve employee morale. It aids in strategic workforce planning and enhances employee engagement by addressing issues leading to turnover. Additionally, companies that successfully retain top talent gain a competitive advantage through a stable and knowledgeable workforce, ultimately contributing to overall business success. By predicting employee turnover, organizations can implement targeted strategies to retain employees, improve workplace culture, and enhance overall organizational performance.


**Skills:**
SQL: CTEs, Joins, Case, aggregate functions
Python: Pandas, Matplotlib, Numpy, Writing functions, building a product funnel, statistics
Tableau: ETL, calculated columns, data visualization, data modeling


**Methodology:**
	1. SQL query that extracts, cleans, and transforms the data from the database.
	2. Conduct a more detailed Logistic regression in Python to
		○ explore the data
		○ pre-process the data
		○ train the model and evaluate the model
		○ predict with using test data
	3. Build a dashboard in Tableau



**Understanding and exploring train data**
 
 We can see some correlation between left and satisfaction Level also some relationship between left to average monthly avg 
![image](https://github.com/user-attachments/assets/6abf90ef-b568-4a4c-8fe2-e37807b5c9e6)



# Draw a count plot that shows the count of employees per department
![image](https://github.com/user-attachments/assets/a67307b2-69c3-4599-92f0-e1cf64a73ae5)


# Check to see if more employees in lower salary have left
![image](https://github.com/user-attachments/assets/072a400a-3573-4c8f-bd0c-70ca83843121)

# Visualize the effect employees left against number of projects worked
![image](https://github.com/user-attachments/assets/cf08cfd4-d031-46ad-81bf-2e40ffb7f63e)


# Factor Plot/Distribution plot
![image](https://github.com/user-attachments/assets/303594b5-c364-436b-9ab7-7f149f2640f1)

# Pseudo R Sq: is 1.94 and upon scaling the data model is 76.61% accurate
logmodel = LogisticRegression()
logmodel.fit(X,y) #model calculation

logmodel.score(X, y)

glm.summary()
<table class="simpletable">
<caption>Logit Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>         <td>left</td>       <th>  No. Observations:  </th>  <td> 15000</td> 
</tr>
<tr>
  <th>Model:</th>                 <td>Logit</td>      <th>  Df Residuals:      </th>  <td> 14990</td> 
</tr>
<tr>
  <th>Method:</th>                 <td>MLE</td>       <th>  Df Model:          </th>  <td>     9</td> 
</tr>
<tr>
  <th>Date:</th>            <td>Mon, 22 Jul 2024</td> <th>  Pseudo R-squ.:     </th>  <td>0.1917</td> 
</tr>
<tr>
  <th>Time:</th>                <td>12:59:11</td>     <th>  Log-Likelihood:    </th> <td> -6655.2</td>
</tr>
<tr>
  <th>converged:</th>             <td>True</td>       <th>  LL-Null:           </th> <td> -8233.8</td>
</tr>
<tr>
  <th>Covariance Type:</th>     <td>nonrobust</td>    <th>  LLR p-value:       </th>  <td> 0.000</td> 
</tr>
</table>
<table class="simpletable">
<tr>
            <td></td>               <th>coef</th>     <th>std err</th>      <th>z</th>      <th>P>|z|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>             <td>   -0.0156</td> <td>    0.134</td> <td>   -0.116</td> <td> 0.907</td> <td>   -0.278</td> <td>    0.246</td>
</tr>
<tr>
  <th>satisfaction_level</th>    <td>   -4.1312</td> <td>    0.097</td> <td>  -42.746</td> <td> 0.000</td> <td>   -4.321</td> <td>   -3.942</td>
</tr>
<tr>
  <th>number_project</th>        <td>   -0.3100</td> <td>    0.021</td> <td>  -14.872</td> <td> 0.000</td> <td>   -0.351</td> <td>   -0.269</td>
</tr>
<tr>
  <th>last_evaluation</th>       <td>    0.7643</td> <td>    0.146</td> <td>    5.243</td> <td> 0.000</td> <td>    0.479</td> <td>    1.050</td>
</tr>
<tr>
  <th>average_monthly_hours</th> <td>    0.0044</td> <td>    0.001</td> <td>    8.630</td> <td> 0.000</td> <td>    0.003</td> <td>    0.005</td>
</tr>
<tr>
  <th>exp_in_company</th>        <td>    0.2294</td> <td>    0.015</td> <td>   15.444</td> <td> 0.000</td> <td>    0.200</td> <td>    0.259</td>
</tr>
<tr>
  <th>work_accident</th>         <td>   -1.4986</td> <td>    0.088</td> <td>  -16.980</td> <td> 0.000</td> <td>   -1.672</td> <td>   -1.326</td>
</tr>
<tr>
  <th>promotion_last_5years</th> <td>   -1.7617</td> <td>    0.256</td> <td>   -6.892</td> <td> 0.000</td> <td>   -2.263</td> <td>   -1.261</td>
</tr>
<tr>
  <th>role_new</th>              <td>    0.0369</td> <td>    0.008</td> <td>    4.809</td> <td> 0.000</td> <td>    0.022</td> <td>    0.052</td>
</tr>
<tr>
  <th>salary_new</th>            <td>    0.0131</td> <td>    0.035</td> <td>    0.374</td> <td> 0.709</td> <td>   -0.056</td> <td>    0.082</td>
</tr>
</table>

#Step 6: Prediction
df_test = pd.read_excel("C:\Python\Test_Turnover.xlsx")

df_test.head()
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>names</th>
      <th>satisfaction_level</th>
      <th>last_evaluation</th>
      <th>number_project</th>
      <th>average_monthly_hours</th>
      <th>exp_in_company</th>
      <th>work_accident</th>
      <th>promotion_last_5years</th>
      <th>role</th>
      <th>salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2237</td>
      <td>Kimmy Walczynski</td>
      <td>0.74</td>
      <td>0.72</td>
      <td>4</td>
      <td>176</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
    </tr>
    <tr>
      <th>1</th>
      <td>8127</td>
      <td>Ignatius Springett</td>
      <td>0.72</td>
      <td>0.88</td>
      <td>3</td>
      <td>224</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>technical</td>
      <td>low</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8146</td>
      <td>Corbie Bittlestone</td>
      <td>0.52</td>
      <td>0.67</td>
      <td>4</td>
      <td>216</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>support</td>
      <td>medium</td>
    </tr>
    <tr>
      <th>3</th>
      <td>14441</td>
      <td>Baxy Matton</td>
      <td>0.42</td>
      <td>0.47</td>
      <td>2</td>
      <td>159</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>marketing</td>
      <td>low</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11909</td>
      <td>Terrell Suff</td>
      <td>0.85</td>
      <td>0.58</td>
      <td>4</td>
      <td>186</td>
      <td>7</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
    </tr>
  </tbody>
</table>
</div>


#drop ID and Name cols from live/test dataset 
df_test2 = df_test.drop(['id', 'names'], 1)
obj_df_test = df_test2.select_dtypes(include=['object']).copy()

from sklearn import preprocessing
lb_make = preprocessing.LabelEncoder()
for col in obj_df_test.columns.values:
  df_test2[f'{col}_new'] = lb_make.fit_transform(df_test2[f'{col}'])

df_test2.drop(['role', 'salary'], 1, inplace=True)

df_test2.head()

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>satisfaction_level</th>
      <th>last_evaluation</th>
      <th>number_project</th>
      <th>average_monthly_hours</th>
      <th>exp_in_company</th>
      <th>work_accident</th>
      <th>promotion_last_5years</th>
      <th>role_new</th>
      <th>salary_new</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.74</td>
      <td>0.72</td>
      <td>4</td>
      <td>176</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>7</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.72</td>
      <td>0.88</td>
      <td>3</td>
      <td>224</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>9</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.52</td>
      <td>0.67</td>
      <td>4</td>
      <td>216</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>8</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.42</td>
      <td>0.47</td>
      <td>2</td>
      <td>159</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.85</td>
      <td>0.58</td>
      <td>4</td>
      <td>186</td>
      <td>7</td>
      <td>0</td>
      <td>0</td>
      <td>7</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>

#scale data 
X_test = df_test2[feature_cols]
X_test = preprocessing.scale(X_test)

predictions = logmodel.predict(X_test) #make predictions based on test dataa

df_test['left_predict'] = predictions #add "left_predict" column to the imported test data

# we can see the prediction if an employee is likely to leave, with the col left_predict we can now take necessary action to prevent the employee from leaving 
df_test.head(50)

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>names</th>
      <th>satisfaction_level</th>
      <th>last_evaluation</th>
      <th>number_project</th>
      <th>average_monthly_hours</th>
      <th>exp_in_company</th>
      <th>work_accident</th>
      <th>promotion_last_5years</th>
      <th>role</th>
      <th>salary</th>
      <th>left_predict</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2237</td>
      <td>Kimmy Walczynski</td>
      <td>0.74</td>
      <td>0.72</td>
      <td>4</td>
      <td>176</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>8127</td>
      <td>Ignatius Springett</td>
      <td>0.72</td>
      <td>0.88</td>
      <td>3</td>
      <td>224</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>technical</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8146</td>
      <td>Corbie Bittlestone</td>
      <td>0.52</td>
      <td>0.67</td>
      <td>4</td>
      <td>216</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>support</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>14441</td>
      <td>Baxy Matton</td>
      <td>0.42</td>
      <td>0.47</td>
      <td>2</td>
      <td>159</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>marketing</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11909</td>
      <td>Terrell Suff</td>
      <td>0.85</td>
      <td>0.58</td>
      <td>4</td>
      <td>186</td>
      <td>7</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>8792</td>
      <td>Kacie Offiler</td>
      <td>0.71</td>
      <td>0.87</td>
      <td>4</td>
      <td>238</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>11144</td>
      <td>Sandro Admans</td>
      <td>0.89</td>
      <td>0.97</td>
      <td>4</td>
      <td>147</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>technical</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2458</td>
      <td>Eugene Lehrahan</td>
      <td>0.18</td>
      <td>0.75</td>
      <td>4</td>
      <td>170</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>1</td>
    </tr>
    <tr>
      <th>8</th>
      <td>11417</td>
      <td>Wainwright Corfield</td>
      <td>0.16</td>
      <td>0.46</td>
      <td>6</td>
      <td>240</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>product_mng</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1974</td>
      <td>Dyann Isoldi</td>
      <td>0.36</td>
      <td>0.48</td>
      <td>2</td>
      <td>152</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>product_mng</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>4409</td>
      <td>Grantley Oret</td>
      <td>0.86</td>
      <td>0.66</td>
      <td>4</td>
      <td>191</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>technical</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>13805</td>
      <td>Elmore Worner</td>
      <td>0.83</td>
      <td>0.55</td>
      <td>3</td>
      <td>271</td>
      <td>7</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>5367</td>
      <td>Dud Brain</td>
      <td>0.92</td>
      <td>0.58</td>
      <td>3</td>
      <td>261</td>
      <td>3</td>
      <td>1</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13902</td>
      <td>Aguie Conford</td>
      <td>0.22</td>
      <td>0.62</td>
      <td>3</td>
      <td>180</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>support</td>
      <td>low</td>
      <td>1</td>
    </tr>
    <tr>
      <th>14</th>
      <td>11969</td>
      <td>Katerina Rosborough</td>
      <td>0.60</td>
      <td>0.85</td>
      <td>3</td>
      <td>242</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>IT</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>8328</td>
      <td>Alida Longley</td>
      <td>0.75</td>
      <td>0.84</td>
      <td>4</td>
      <td>195</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>marketing</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>16</th>
      <td>3009</td>
      <td>Laraine Petre</td>
      <td>0.95</td>
      <td>0.71</td>
      <td>3</td>
      <td>251</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>hr</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>12905</td>
      <td>Gareth MacCook</td>
      <td>0.97</td>
      <td>0.90</td>
      <td>5</td>
      <td>262</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>18</th>
      <td>5243</td>
      <td>Scottie Chestney</td>
      <td>0.67</td>
      <td>0.64</td>
      <td>5</td>
      <td>248</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>support</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>19</th>
      <td>792</td>
      <td>Christophorus Boseley</td>
      <td>0.90</td>
      <td>0.83</td>
      <td>5</td>
      <td>259</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>accounting</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>20</th>
      <td>3304</td>
      <td>Arleyne Froome</td>
      <td>0.80</td>
      <td>0.54</td>
      <td>5</td>
      <td>261</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21</th>
      <td>14764</td>
      <td>Todd Cashen</td>
      <td>0.79</td>
      <td>1.00</td>
      <td>5</td>
      <td>257</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>22</th>
      <td>23</td>
      <td>Elmo McNee</td>
      <td>0.46</td>
      <td>0.57</td>
      <td>2</td>
      <td>139</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>23</th>
      <td>3906</td>
      <td>Regen Nafzger</td>
      <td>0.98</td>
      <td>0.99</td>
      <td>5</td>
      <td>141</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>24</th>
      <td>1650</td>
      <td>Penelope Wenman</td>
      <td>0.77</td>
      <td>0.98</td>
      <td>4</td>
      <td>238</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>support</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>25</th>
      <td>12599</td>
      <td>Rudolf Reichardt</td>
      <td>0.11</td>
      <td>0.92</td>
      <td>7</td>
      <td>307</td>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>IT</td>
      <td>low</td>
      <td>1</td>
    </tr>
    <tr>
      <th>26</th>
      <td>12171</td>
      <td>Tobiah Fruchon</td>
      <td>0.41</td>
      <td>0.46</td>
      <td>2</td>
      <td>160</td>
      <td>3</td>
      <td>0</td>
      <td>1</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>27</th>
      <td>5426</td>
      <td>Fay Monnelly</td>
      <td>0.77</td>
      <td>0.89</td>
      <td>3</td>
      <td>142</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>marketing</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>28</th>
      <td>4415</td>
      <td>Lola Burrells</td>
      <td>0.65</td>
      <td>0.55</td>
      <td>5</td>
      <td>215</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>IT</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>29</th>
      <td>8330</td>
      <td>Hamel Edgeler</td>
      <td>0.51</td>
      <td>0.54</td>
      <td>4</td>
      <td>166</td>
      <td>4</td>
      <td>1</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>30</th>
      <td>5428</td>
      <td>Shalne Berntssen</td>
      <td>0.57</td>
      <td>0.43</td>
      <td>3</td>
      <td>167</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>31</th>
      <td>11768</td>
      <td>Nefen Russan</td>
      <td>0.80</td>
      <td>0.84</td>
      <td>4</td>
      <td>242</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>marketing</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>32</th>
      <td>7036</td>
      <td>Woodie Hayhow</td>
      <td>0.97</td>
      <td>0.82</td>
      <td>4</td>
      <td>176</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>33</th>
      <td>14891</td>
      <td>L;urette Stango</td>
      <td>0.85</td>
      <td>0.87</td>
      <td>5</td>
      <td>246</td>
      <td>5</td>
      <td>1</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>34</th>
      <td>13518</td>
      <td>Claude Ales0</td>
      <td>0.72</td>
      <td>0.62</td>
      <td>3</td>
      <td>243</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>hr</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>35</th>
      <td>13064</td>
      <td>Virginia Teligin</td>
      <td>0.58</td>
      <td>0.38</td>
      <td>4</td>
      <td>203</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>36</th>
      <td>14410</td>
      <td>Starr Yitzhok</td>
      <td>0.77</td>
      <td>0.94</td>
      <td>5</td>
      <td>226</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>support</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>37</th>
      <td>8699</td>
      <td>Perla Durrand</td>
      <td>0.65</td>
      <td>0.66</td>
      <td>6</td>
      <td>240</td>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>RandD</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>38</th>
      <td>12809</td>
      <td>Mahala McTrustie</td>
      <td>0.52</td>
      <td>0.98</td>
      <td>4</td>
      <td>265</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>product_mng</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>39</th>
      <td>4879</td>
      <td>Hobart Bertrand</td>
      <td>0.43</td>
      <td>0.62</td>
      <td>2</td>
      <td>180</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>RandD</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>40</th>
      <td>8509</td>
      <td>Nobe Leathe</td>
      <td>0.60</td>
      <td>0.98</td>
      <td>4</td>
      <td>192</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>technical</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>41</th>
      <td>7784</td>
      <td>Peta Gosson</td>
      <td>0.64</td>
      <td>0.85</td>
      <td>3</td>
      <td>250</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>marketing</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>42</th>
      <td>2575</td>
      <td>Ninnette Batter</td>
      <td>0.89</td>
      <td>0.83</td>
      <td>5</td>
      <td>267</td>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>technical</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>43</th>
      <td>1021</td>
      <td>Bibbie Matteoli</td>
      <td>0.80</td>
      <td>0.95</td>
      <td>3</td>
      <td>146</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>hr</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>44</th>
      <td>158</td>
      <td>Averell Paintain</td>
      <td>0.39</td>
      <td>0.50</td>
      <td>2</td>
      <td>136</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>management</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>45</th>
      <td>1778</td>
      <td>Marcel Fowkes</td>
      <td>0.85</td>
      <td>0.90</td>
      <td>2</td>
      <td>168</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>46</th>
      <td>8027</td>
      <td>Artus Cawcutt</td>
      <td>0.86</td>
      <td>0.79</td>
      <td>3</td>
      <td>106</td>
      <td>6</td>
      <td>1</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>47</th>
      <td>1082</td>
      <td>Emili Cowl</td>
      <td>0.87</td>
      <td>0.88</td>
      <td>5</td>
      <td>231</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>medium</td>
      <td>0</td>
    </tr>
    <tr>
      <th>48</th>
      <td>7193</td>
      <td>Edeline Painten</td>
      <td>0.66</td>
      <td>0.98</td>
      <td>4</td>
      <td>163</td>
      <td>3</td>
      <td>1</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
    <tr>
      <th>49</th>
      <td>7733</td>
      <td>Meggi Mc Ilory</td>
      <td>0.92</td>
      <td>0.80</td>
      <td>3</td>
      <td>211</td>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>sales</td>
      <td>low</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>


