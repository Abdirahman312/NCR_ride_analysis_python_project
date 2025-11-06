# 🚖 NCR Ride Bookings Analysis

## 📌 Project Overview
This project analyzes ride booking data from NCR to uncover key insights such as ride patterns, popular routes, booking status trends, and customer/driver ratings.  
It was completed as part of my data analysis portfolio using **Python (pandas, matplotlib, seaborn)** in Jupyter Notebook.  

---

## 🧹 Data Cleaning
Steps taken:
- Removed duplicates and irrelevant rows  
- Handled missing values in columns like ratings  
- Converted date and time columns into proper datetime format  
- Created new features such as `day_of_week`, `hour`, and `ride_duration`  

---

## 🛠️ Tools Used
- 🐍 **Python** – Main programming language for data analysis  
- 📊 **Pandas** – Data manipulation and cleaning  
- 📈 **Matplotlib & Seaborn** – Data visualization  
- 🔢 **NumPy** – Numerical computations  
- 📓 **Jupyter Notebook** – Analysis environment  

---

## 💻 Code Used

### Importing Libraries
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

### Loading the Dataset
```python
df = pd.read_csv('NCR_Ride_Bookings.csv')
df.head()
```

### Data Cleaning
```python
# Remove duplicates and missing values
df.drop_duplicates(inplace=True)
df.dropna(subset=['Driver_Rating', 'Customer_Rating'], inplace=True)

# Convert to datetime
df['Request_Time'] = pd.to_datetime(df['Request_Time'])
df['Drop_Time'] = pd.to_datetime(df['Drop_Time'])

# Feature Engineering
df['day_of_week'] = df['Request_Time'].dt.day_name()
df['hour'] = df['Request_Time'].dt.hour()
df['ride_duration'] = (df['Drop_Time'] - df['Request_Time']).dt.total_seconds() / 60
```

### Analysis Example
```python
# Booking status distribution
booking_status = df['Booking_Status'].value_counts()

# Average booking value by payment method
avg_value = df.groupby('Payment_Method')['Booking_Value'].mean().sort_values(ascending=False)
```

### Visualization Example
```python
plt.figure(figsize=(8,5))
sns.countplot(x='Booking_Status', data=df, palette='Blues')
plt.title('Booking Status Distribution')
plt.xlabel('Status')
plt.ylabel('Number of Rides')
plt.show()
```

---

## 📊 Analysis & Insights
Key findings:
- Total records analyzed: **150,000**.  
- Booking outcomes: Completed **93,000**, Cancelled (or variants) **37,500** (~**25.0%**).  
- Top vehicle types: Auto, Go Mini, Go Sedan, Bike, Premier Sedan, eBike, Uber XL.  
- Total revenue: **51.8M**, average booking value: **508.30**.  
- Average distance: **24.6 km**, median: **23.7 km**.  
- Average ratings: Customer **4.40/5**, Driver **4.23/5**.  
- Top payment methods: **UPI, Cash, Wallet, Credit Card, Debit Card.**  
- Peak hours: **16:00–20:00**, Most active days: **Monday & Saturday.**  

---

## 📑 Reports
You can view the full report in:  
- [📄 PDF Report](reports/NCR_Ride_Bookings_Analysis.pdf)  
- [🌐 HTML Report](reports/NCR_Ride_Bookings_Analysis.html)  

---

## 📬 Contact Me
📧 **Email:** [abdirahmanahmed2728@email.com](mailto:abdirahmanahmed2728@email.com)  
💼 **LinkedIn:** [linkedin.com/in/abdirahman-ahmed-b7841a343](https://www.linkedin.com/in/abdirahman-ahmed-b7841a343)  
💻 **GitHub:** [github.com/Abdirahman312](https://github.com/Abdirahman312)  

---

⭐ **Author:** _Abdirahman Ahmed_  
🗓️ **Year:** 2025
