
# Healthcare SQL Analytics Project – SK

## 📌 Project Overview
This project analyzes a real-world healthcare dataset (Diabetes 130-US hospitals) using SQL for querying and Excel for visualization.  
The focus is on uncovering **patterns in patient readmissions, demographics, and hospital stay durations**.  

✅ SQL queries for 5 business questions  
✅ Visualizations created in Excel (saved as images)  
✅ Insights for each analysis  

---

## 🔍 Business Questions & Insights

## 🔍 Business Questions & Insights

### Q1. Which age group has the highest readmission rate?
```sql
SELECT age, COUNT(*) AS readmission_count
FROM newhospitaldata
WHERE readmitted <> 'NO'
GROUP BY age
ORDER BY readmission_count DESC;

💡 Insights

Middle-aged and elderly patients tend to have higher readmissions.

Younger patients (<30) show fewer readmissions.

Targeted care plans for 50+ could reduce re-hospitalizations.



Q2. What is the average hospital stay across age groups?
SELECT age, AVG(time_in_hospital) AS avg_stay
FROM newhospitaldata
GROUP BY age
ORDER BY avg_stay DESC;

💡 Insights

Average stay increases with age.

Patients over 70 have the longest hospital stays.

This highlights resource planning needs for elderly care.


Q3. Do male or female patients take more medications on average?
SELECT gender, AVG(num_medications) AS avg_meds
FROM newhospitaldata
GROUP BY gender;
📊 Chart:


💡 Insights

Female patients slightly edge out males in average medications.

Differences are not very large but could inform prescription monitoring.

A deeper breakdown by age + gender could be insightful.

Q4. Which gender has higher readmission rates?
SELECT gender, COUNT(*) AS readmission_count
FROM newhospitaldata
WHERE readmitted <> 'NO'
GROUP BY gender
ORDER BY readmission_count DESC;

💡 Insights

Female patients have slightly higher readmission counts.

Gender difference is smaller compared to age-driven readmissions.

Suggests age > gender as the stronger predictor.

Q5. Does longer hospital stay reduce readmission rates?
SELECT time_in_hospital, COUNT(*) AS readmission_count
FROM newhospitaldata 
WHERE readmitted <> 'NO'
GROUP BY time_in_hospital
ORDER BY time_in_hospital;

💡 Insights

Shorter stays (1–3 days) show higher readmissions.

Moderate stays (~5–7 days) lower readmissions.

Very long stays (10+) don’t guarantee lower readmissions → may point to complex conditions.


---

