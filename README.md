# EDUCATION FOR ALL FUNDRAISING

### PROJECT OVERVIEW

This project aims to show the donors insight and donation rate for the Education for all Charity based on the donors frequency, number of donors in the datadase etc.

### DATA SOURCE

Education for all data used for this analysis is the Donation_Data.sql and Donor_Data.sql containing donors and donations record about fundraising made by the Charity Education for all.

### DATA CLEANING/PREPARATION

- Created a database
- Data loading
- Created a table

### EXPLORATORY DATA ANALYSIS

The exploratory data analysis executed in the fundrasing data to answer key questions include the following:
- Increase the number of donors in your database.
- Increase the donation frequency of your donors.
- Increase the value of donations in your database.

### DATA ANALYSIS

This invovle some coding with SQL as follows:
- How much is the total donation?

``` sql

SELECT  SUM ("donation") AS "total_donation" 
FROM donation_data;

```
  
![SQL Question 1 Capture](https://github.com/marrieth/FUNDRAISING/assets/138234128/8b3abe5d-aca3-4479-82dd-2f782611b849)


- What is the total donation by gender?

``` sql

SELECT gender,SUM("donation") AS "gender_total_donation"
FROM donation_data
GROUP BY gender;

```


![SQL Question 2 Capture](https://github.com/marrieth/FUNDRAISING/assets/138234128/61ab4ecb-7ca8-4d94-86e9-f3ebe72cf4be)


- Show the total donation and number of donations
    by gender

``` sql

SELECT gender,SUM ("donation") AS "total_donation",COUNT("donation") AS "no_of_donation"
FROM donation_data
GROUP BY gender;

```



![SQL Question 3 Capture](https://github.com/marrieth/FUNDRAISING/assets/138234128/ca109170-4a6a-4be8-9cfc-4b10d076511a)

- Total donation made by frequency of donation

``` sql

SELECT donation_data.id,donation_frequency,SUM("donation") AS "total_donation"
FROM donation_data
LEFT JOIN donor_data
ON donation_data.id = donor_data.id
GROUP BY donation_data.id,donation_frequency;

```


![SQL Question 4 Capture (2)](https://github.com/marrieth/FUNDRAISING/assets/138234128/3099b445-9ad2-44c2-9902-3cdddfab4de4)

- Total donation and number of donation by Job field

``` sql

SELECT job_field,SUM ("donation") AS "total_donation",COUNT ("donation") AS "no_of_donation"
FROM donation_data
GROUP BY job_field;

```


![SQL Qestion 5 Capture (2)](https://github.com/marrieth/FUNDRAISING/assets/138234128/7526138d-597c-4992-8bf2-4fb741262bc4)


- Total donation and number of donations above
    $200

``` sql

SELECT SUM ("donation") AS "total_donation",COUNT("donation") AS no_of_donation
FROM donation_data
WHERE donation < 200;

```


![SQL Question 6 Capture](https://github.com/marrieth/FUNDRAISING/assets/138234128/833eee85-f4e2-4d4f-b105-a95536c2860f)


- Total donation and number of donations below
   $200

``` sql

SELECT SUM ("donation") AS "total_donation",COUNT("donation") AS no_of_donation
FROM donation_data
WHERE donation > 200;

```


![SQL Question 7 Capture](https://github.com/marrieth/FUNDRAISING/assets/138234128/d24267db-6db5-47df-ae93-3b81fac1b824)

- Which top 10 states contributes the highest
   donations

``` sql

SELECT  state,SUM ("donation") AS "total_state_donation"
FROM donation_data
GROUP BY state
ORDER BY total_state_donation desc
LIMIT 10;

```


![SQL Question 8 Capture](https://github.com/marrieth/FUNDRAISING/assets/138234128/710a37f7-e9c1-4b55-920a-e3b59fdc1932)

- Which top 10 states contributes the least donations

``` sql

SELECT  state,SUM ("donation") "total_state_donation"
FROM donation_data
GROUP BY state
ORDER BY total_state_donation asc
LIMIT 10;

```


![SQL Question 9 Capture](https://github.com/marrieth/FUNDRAISING/assets/138234128/53679d57-9ac5-444c-bdaf-192ef43ac250)


- What are the top 10 cars driven by the highest
   donors.

``` sql

SELECT donation_data.id,car, SUM("donation") AS total_donor_donation
FROM donation_data
LEFT JOIN donor_data
ON donation_data.id=donor_data.id
GROUP BY donation_data.id,car
ORDER BY total_donor_donation desc
LIMIT 10;

```


![SQL Question 10 Capture](https://github.com/marrieth/FUNDRAISING/assets/138234128/76c329d6-ef9c-4953-8709-1d936720a253)



### RESULTS AND INSIGHTS

From the insights derived it shows that more men in the Human Resources department in the city of California donate more.

### RECOMMENDATION

Enlighten people more on the need for the fundraising and how their regular support/donations will help to achieve the aim of the fundraising.
