# Appendix A: SQL Data Quality Queries

## 1. Duplicate Well IDs
```sql
SELECT Well_ID, COUNT(*) 
FROM well_production
GROUP BY Well_ID
HAVING COUNT(*) > 1;
```
**Results:**
- 1002 | Beta-2 | OK | 2020-03-12 | 2020-05-22 | 2023-06-01 | Unknown | Inactive  
- 1005 | Echo-5 | CO | 2022-09-10 | 2022-10-01 | 2022-10-01 | 130000.0 | Active

---

## 2. Negative Production Volume
```sql
SELECT * FROM well_production
WHERE Volume_Produced < 0;
```
**Result:**
- 1004 | Delta-4 | TX | 2022-05-20 | 2022-07-01 | 2023-05-10 | -500.0 | Chevron | Inactive

---

## 3. Production End Before Start
```sql
SELECT * FROM well_production
WHERE Prod_End < Prod_Start;
```
**Result:**
- 1003 | Gamma-3 | NM | 2021-07-08 | 2021-09-15 | 2021-09-01 | 200000.0 | Conoco | Active

---

## 4. Summary Statistics
```sql
SELECT 
    MIN(Volume_Produced) AS Min_Production,
    MAX(Volume_Produced) AS Max_Production,
    AVG(Volume_Produced) AS Avg_Production,
    COUNT(*) AS Total_Records
FROM well_production;
```
**Results:**
- Min Production: -500  
- Max Production: 200,000  
- Average Production: 128,625  
- Total Records: 5
