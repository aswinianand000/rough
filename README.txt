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
 A) As can be seen from  count plot(refer jupyter notebook), there are 17 orders which having 'total_items' of value 2000. Earlier in boxplot also shown the same as outliers in the dataset. In this case, we can calculate the Average Order Value for small and bulk orders separately, having 2 averages and then take a weighted average to arrive at final AOV. We may also find average value per order per item as a useful metric for evaluation in this scenario to get the price of single sneaker pair (Revenue per order per item).
Out of 5000 orders, only 17 are bulk orders that messes with the AOV values, hence a simple average can't be used as metric. On further analysis, we find that all these are placed by one customer,user_id 607. Hence we can treat this customer as an outlier, ignore the value and find AOV for others which would be more close to reality. We also need to take into account that one customer may place multiple orders, hence grouping the orders by user id would also provide interesting results. We could also find average order value per day (by grouping them on created_by date) and then take the mean over 30 days period. But this also does not address the problem of bulk order.A better metric would be to find the AOV after treating these outliers, ie, replace outlier values to lower side of 1st quartile with value of 1st quartile and to higher side of 3rd quartile to value on 3rd quartile , so as to have little impact to our data distribtion due to outliers. This is better than ignoring the outliers since the value of outliers is huge and ignoring them would affect the total revenue generated through them. 

B) After analysing the data, we can find that a better metric would be calculating AOV after treating the outliers as above .That is,  replace outlier values to lower side of 1st quartile with value of 1st quartile and to higher side of 3rd quartile to value on 3rd quartile , so as to have little impact to our data distribtion due to outliers. This is better than ignoring the outliers since the value of outliers is huge and ignoring them would affect the total revenue generated through them.  And then we can find AOV as Total revenue/No of orders

 C) AOV value after treatment of outliers is $306.03 which seems a fair average of AOV.

Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

How many orders were shipped by Speedy Express in total? 54
What is the last name of the employee with the most orders? Peacock
What product was ordered the most by customers in Germany? Boston Crab Meat

