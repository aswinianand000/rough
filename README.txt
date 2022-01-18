Summer 2022 Data Science Intern Challenge 

Please complete the following questions, and provide your thought process/work. You can attach your work in a text file, link, etc. on the application page. Please ensure answers are easily visible for reviewers!


Question 1: Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 
What metric would you report for this dataset?
What is its value?

Answer 1: Looking at the dataset and conducting an initial analysis, we can see that AOV is calculated by:
AOV = Total Order Amount / Total Number of Orders 
 which is $3145.128. However, if we look at order details carefully, there are few bulk orders(items count in each order as 2000) hence these it is not fair that these order amounts be added along with single item orders.
 A) Since we know that the data is of sneaker shops only, we can calculate the Average Order Value for small and bulk orders separately, having 2 averages and then take a weighted average to arrive at final AOV. We may also find average value per order per item as a useful metric for evaluation in this scenario to get the price of single sneaker pair (Revenue per order per item).
 B)Out of 5000 orders, only 17 are bulk orders that messes with the AOV values, hence a simple average can't be used as metric. On further analysis, we find that all these are placed by one customer,user_id 607. Hence we can treat this customer as an outlier, ignore the value and find AOV for others which would be more close to reality. We also need to take into acocunt that one customer may come and buy multiple times in multiple orders, hence grouping the orders by user id would also provide interesting results. We could also find average order value per day (by grouping them on created_by date) and then take the mean over 30 days period. But this also doesnot address the problem of bulk order. Hence, a better metric would be to find the average order value per day (since the questrion mentions analysis on AOV) and take the mode of it as it will reflect the most common order value. If AOV is not to be considered, mean of amount per item would serve as better metric as it will tell as how much value an order of one item would generate.
 C) Mode is : 


Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

How many orders were shipped by Speedy Express in total?
What is the last name of the employee with the most orders?
What product was ordered the most by customers in Germany?

