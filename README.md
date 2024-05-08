## EXNO-3-DS
# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.
# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.
# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.
# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method
# CODING AND OUTPUT:
~~~
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[['ord_2']])
df['bo2']=e1.fit_transform(df[['ord_2']])
l=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=l.fit_transform(dfc['ord_2'])
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
dfs=pd.concat([df2,enc],axis=1)
pd.get_dummies(df2,columns=['nom_0'])
pip install --upgrade category_encoders
from category_encoders import BinaryEncoder
import pandas as pd
df=pd.read_csv("/content/data.csv")
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb=df.copy()
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc['City'],y=cc['Target'])
cc=pd.concat([cc,new],axis=1)
import pandas as pd
df=pd.read_csv("/content/Data_to_Transform.csv")
import numpy as np
from scipy import stats
np.log(df['Highly Positive Skew'])
np.reciprocal(df['Moderate Negative Skew'])
np.sqrt(df['Highly Positive Skew'])
np.square(df['Highly Positive Skew'])
df['Highly Positive skew_boxcox'],parameters=stats.boxcox(df['Highly Positive Skew'])
df.skew()
df['Moderate Negative Skwe_yeojohnson'],parameters=stats.yeojohnson(df['Moderate Negative Skew'])
df.skew()
import seaborn as sns
import matplotlib.pyplot as plt
import statsmodels.api as sn
import scipy.stats as stats
sn.qqplot(df['Moderate Negative Skew'],line='45')
plt.show()
sn.qqplot(df['Highly Negative Skew'],line='45')
plt.show()
sn.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
~~~
## OUTPUT:
![321273041-de4abe46-97f3-40f5-9bca-3edabfe5d0cc](https://github.com/RuchitraThiyagaraj/EXNO-3-DS/assets/154776996/25f1a30c-c38f-40d1-a7e7-53fd22f4d409)
![321273041-de4abe46-97f3-40f5-9bca-3edabfe5d0cc](https://github.com/RuchitraThiyagaraj/EXNO-3-DS/assets/154776996/c529c675-6da8-4e78-b651-99aea276b8ad)
![321273243-f25b7603-fb6e-4e04-a161-cd873a55a65e](https://github.com/RuchitraThiyagaraj/EXNO-3-DS/assets/154776996/2829ad9f-8c38-4f53-9494-aa6e9515bec7)
![321273372-7c780a63-766e-42ab-bd00-d807c3ad26da](https://github.com/RuchitraThiyagaraj/EXNO-3-DS/assets/154776996/16c0a042-66ea-4a83-b49e-b78414d847d6)
![321273451-7e8cc484-0b89-40fa-9c92-a32dd05bfaf2](https://github.com/RuchitraThiyagaraj/EXNO-3-DS/assets/154776996/8a25beb5-f224-4af0-b2e9-9d664e7e489f)
![321273552-28a3fc55-52fe-431b-99ac-53bac58b4b41](https://github.com/RuchitraThiyagaraj/EXNO-3-DS/assets/154776996/ac4b02d6-71b4-4ec3-ad7e-7b842b21e035)
![321273631-ac3d4944-7c26-4804-a241-0c212d1495cd](https://github.com/RuchitraThiyagaraj/EXNO-3-DS/assets/154776996/3e307ae4-7c52-4f6b-af6d-a8604c5bfd26)
![321273961-5a4f1365-86c9-4411-9aa2-22fae6cdfd94](https://github.com/RuchitraThiyagaraj/EXNO-3-DS/assets/154776996/7f717c87-2dde-4551-b1ef-1845c23bc556)
![321274184-0ae95324-377d-4484-989b-bba6795fe78e](https://github.com/RuchitraThiyagaraj/EXNO-3-DS/assets/154776996/5c35f4f0-9d1b-4a93-a50c-6e991df6e9a3)
# RESULT:
This code successfully performs feature encoding and transformation on the given data and saves the encoded data to a file
       
