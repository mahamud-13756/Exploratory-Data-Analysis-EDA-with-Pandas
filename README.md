# Exploratory-Data-Analysis-EDA-with-Pandas
## Ecommerce Purchases Data Analysis - Solutions

This repository contains solutions to 20 data analysis questions using Pandas on a synthetic ecommerce dataset. Below are the questions, code explanations, and outputs. 

---

### **Question 1: Import Pandas and Read the CSV File**
**Code and Explanation:**
```python
import pandas as pd
df = pd.read_csv('Cust_Purch_FakeData.csv')
```
- **Explanation:** Imports the Pandas library and loads the dataset into a DataFrame.

---

### **Question 2: 2. Its good idea to see how the data look like, display first 5 rows of your data-set.**
**Code and Explanation:**
```python
df.head(5)
```
- **Explanation:** Shows the first 5 rows of the dataset to inspect its structure.  
**Output:**  
![Head Output]([https://drive.google.com/file/d/1Tr1EplwNTGaxESLFvO0D9fIwmZb8bRHK/view?usp=sharing](https://drive.google.com/file/d/1Tr1EplwNTGaxESLFvO0D9fIwmZb8bRHK/view?usp=drive_link))


---

### **Question 3: How many entries your data have? Can you tell the no. of columns in your data?**
**Code and Explanation:**
```python
df.info()
```
- **Explanation:** Displays the total entries (30,000) and columns (20) along with data types.  
**Output:**
```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 30000 entries, 0 to 29999
Data columns (total 20 columns):
prefix        30000 non-null object
first         30000 non-null object
last          30000 non-null object
email         30000 non-null object
gender        30000 non-null object
age           30000 non-null int64
company       30000 non-null object
profession    30000 non-null object
phone         30000 non-null object
postal        30000 non-null object
province      30000 non-null object
cc_no         30000 non-null int64
cc_exp        30000 non-null object
cc_type       30000 non-null object
price(CAD)    30000 non-null float64
fav_color     30000 non-null object
ip            30000 non-null object
weekday       30000 non-null object
ampm          30000 non-null object
date          30000 non-null object
dtypes: float64(1), int64(2), object(17)
memory usage: 4.6+ MB
```

---

### **Question 4: What are the max and min ages of your customer? Can you find mean of your customer?**
**Code and Explanation:**
```python
print("Max. age of the customer is:  ", df['age'].max() )
print("Min. age of the customer is:  ", df['age'].min() )
print("Avg. age of the customer is:  ", df['age'].mean() )
```
- **Explanation:** Calculates and prints age statistics.  
**Output:**
```
Max. age of the customer is:   65
Min. age of the customer is:   18
Avg. age of the customer is:   41.550066666666666
```

---

### **Question 5: Three Most Common Customer Names**
**Code and Explanation:**
```python
df['first'].value_counts().head(3)
```
- **Explanation:** Counts occurrences of first names and returns the top 3.  
**Output:**  
```
Willie     130  
Francis    124  
Eula        86  
```

---

### **Question 6: Customers Sharing the Same Phone Number**
**Code and Explanation:**
```python
df[df['phone'] == '(263) 382-8004']
```
- **Explanation:** Filters rows where the phone number appears more than once.  
**Output:**
```
(263) 382-8004    2
(712) 247-7037    1
(876) 882-4110    1
(401) 747-5970    1
(708) 363-8240    1
                 ..
(334) 450-1716    1
(612) 692-8843    1
(773) 335-7703    1
(851) 360-7946    1
(841) 962-4087    1
Name: count, Length: 29999, dtype: int64
``` 
Two customers (Lilly Tyler and Peter Cain) share the same phone number.

---

### **Question 7: Count of Structural Engineers**
**Code and Explanation:**
```python
df[df['profession'] == 'Structural Engineer'].count()
```
- **Explanation:** Counts rows where the profession is "Structural Engineer".  
**Output:**  
87 customers.

---

### **Question 8: Male Structural Engineers**
**Code and Explanation:**
```python
df1 = df[df['profession'] == 'Structural Engineer']
df1[df1['gender'] == 'Male'].count()
```
- **Explanation:** Filters Structural Engineers and counts males.  
**Output:**  
43 male Structural Engineers.

---

### **Question 9: Female Structural Engineers in Alberta (AB)**
**Code and Explanation:**
```python
df2 = df1[df1['gender'] == 'Female']
df2[df2['province'] == 'AB']
```
- **Explanation:** Filters female Structural Engineers in Alberta.  
**Output:**  
4 female customers in AB.

---

### **Question 10: Max, Min, and Average Spending**
**Code and Explanation:**
```python
print("Max. spending:  ", df['price(CAD)'].max() )
print("Mai. spending:  ", df['price(CAD)'].min() )
print("Avg. spending:  ", df['price(CAD)'].mean() )
```
- **Output:**  
```
Max. spending:   100.0
Mai. spending:   0.0
Avg. spending:   49.990775
```

---

### **Question 11: Customers Who Spent 0 CAD**
**Code and Explanation:**
```python
df[df['price(CAD)'] == 0]
```
- **Explanation:** Finds customers with $0 spending.  
**Output:**  
2 customers (Bruce Bryan and Flora Clark).

---

### **Question 12: Customers Who Spent ≥100 CAD**
**Code and Explanation:**
```python
df[df['price(CAD)'] >= 100]
```
- **Output:**  
3 customers (Gregory Brown, Cody Christensen, Lizzie Dixon).

---

### **Question 13: Emails Linked to Credit Card 5020...0230**
**Code and Explanation:**
```python
df[df['cc_no'] == 5020000000000230]['email']
```
- **Output:**  
`sebvajom@kol.km` and `acu@jatsot.ug`.

---

### **Question 14: Cards Expiring in 2019**
**Code and Explanation:**
```python
df[df['cc_exp'].str.endswith('19')].count()
```
- **Output:**  
2,684 cards.

---

### **Question 15: Visa Card Users**
**Code and Explanation:**
```python
df[df['cc_type'] == 'Visa']['first'].count()
```
- **Output:**  
1,721 customers.

---

### **Question 16: Customer Spending 100 CAD with Visa**
**Code and Explanation:**
```python
df5 = df[df['cc_type'] == 'Visa']
df5[df5['price(CAD)'] == 100]
```
- **Output:**  
Gregory Brown (email: `hav@jek.gs`).

---

### **Question 17: Top 2 Professions**
**Code and Explanation:**
```python
df['profession'].value_counts().head(2)
```
- **Output:**  
```
Preschool Teacher       112  
Distribution Manager    107  
```

---

### **Question 18: Top 5 Email Providers**
**Code and Explanation:**
```python
df['email'].str.split('@').str[1].value_counts().head(5)
```
- **Output:**  
```
gmail.com      1687
me.com         1676
outlook.com    1664
live.com       1660
hotmail.com    1659 
```

---

### **Question 19: Customers with "am.edu" Email**
**Code and Explanation:**
```python
df[df['email'].str.endswith('am.edu')]
```
- **Output:**  
Loretta Fletcher (`barit@am.edu`).

---

### **Question 20: Busiest Day of the Week**
**Code and Explanation:**
```python
df['weekday'].value_counts().head()
```
- **Output:**  
Saturday (4,376 customers).

---

## 📹 Explanation Video  
For a detailed walkthrough, watch the video:  
[**YouTube Explanation**](https://www.youtube.com/watch?v=agbgpsbbaTQ)

---

Feel free to explore the code and dataset! 🚀
