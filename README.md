# Summary

Acceptance rates for bar coupons is mostly predicated on how frequently patrons went to bars normally.  The best time to deliver a coupon for cheap takeout or delivery restaurants is around 2-6 pm.  More detailed analysis can be found below and in the [Jupyter Notebook](./Will%20the%20Customer%20Accept%20the%20Coupon%3F.ipynb).

### Problems

Use the prompts below to get started with your data analysis.  

## 1. Read in the `coupons.csv` file.

## 2. Investigate the dataset for missing or problematic data.
Computing the sum of the null values across the columns, it is apparent that the data for the 'car' column is significantly incomplete.  Some of the other categories, like 'Bar, 'CoffeeHouse', etc. are also missing data, but not to the same extent as the 'car' column.

## 3. Decide what to do about your missing data -- drop, replace, other...
Since there were so many missing values, I decided to drop the column altogether from the dataset.  I did this by using the dropna() and drop() functions on the dataframe in place to drop the null values and then the column altogether.

## 4. What proportion of the total observations chose to accept the coupon? 
56.93%

## 5. Use a bar plot to visualize the `coupon` column.

## 6. Use a histogram to visualize the temperature column.

**Investigating the Bar Coupons**

Now, we will lead you through an exploration of just the bar related coupons.  

## 1. Create a new `DataFrame` that contains just the bar coupons.

## 2. What proportion of bar coupons were accepted?
41.19%

## 3. Compare the acceptance rate between those who went to a bar 3 or fewer times a month to those who went more.
The acceptance rate for those who went to the bar over 3 times a month is 76.17% and the acceptance rate for those when went to the bar 3 times or fewer a month is 37.27%.

## 4. Compare the acceptance rate between drivers who go to a bar more than once a month and are over the age of 25 to the all others.  Is there a difference?
For those who are over 25 and go to the bar more than once a month, the acceptance rate is 68%.  This rate is about the same as those who are under 25 and go to the bar more than once a month.

## 5. Use the same process to compare the acceptance rate between drivers who go to bars more than once a month and had passengers that were not a kid and had occupations other than farming, fishing, or forestry. 
For the particular group named in the question, the acceptance rate is 71.43%.

## 6. Compare the acceptance rates between those drivers who:

- go to bars more than once a month, had passengers that were not a kid, and were not widowed **71.43%**
- go to bars more than once a month and are under the age of 30 **71.95%**
- go to cheap restaurants more than 4 times a month and income is less than 50K **45.65%**

## 7.  Based on these observations, what do you hypothesize about drivers who accepted the bar coupons?
Based on the fact that the acceptance rate of bar coupons among those who go to bars more than once a month was around 71-72% and the fact that the acceptance rate of bar coupons among those who go to cheap restaurants more than 4 times a month was 45-46%, we can say that a driver's demonstrated track record of going to bars is more predictive of accepting bar coupons.  This is demonstrated by the fact that even people who go out to eat a lot at cheap restaurants don't nearly have the same acceptance rate as those who go to bars even occasionally.  The fact that a driver is a demonstrated bar-goer is more predictive.

## Independent Investigation

Using the bar coupon example as motivation, you are to explore one of the other coupon groups and try to determine the characteristics of passengers who accept the coupons.

First, I grouped by the coupon type in order to see the acceptance rates of the different types of coupons.  I clearly saw that the coupons most likely to be accepted were for the coupon types: 'Carry out & Take away' and 'Restaurant(20-50)'.  I collectively refer to these coupons as the fast_and_cheap_restaurants and I plotted the relative acceptance rates just to visualize the data and present the difference in acceptance rates visually.

After isolating the universe of coupons to those that exhibited the highest acceptance rates, I wanted to cross-reference against different categories of contextual attributes.  We know from the earlier data on acceptance rates by coupon types that those for fast and cheap restaurants tended to get accepted at significantly higher rates.  I wanted to see if we could further increase that acceptance rate since it seemed like those coupon types tended to be successfully accepted.  What I found is that the time of day can further increase the odds that a coupon is accepted.  At 2 and 6 pm, the acceptance rates on these coupons were in the 82% range, which is around 10% higher than those coupons were accepted overall.  Thus, it would make sense to target these coupons to these drivers in the afternoon timeframe between 2 and 6 pm.  This insight is further supported by the fact that none of the other contextual attributes exhibited a similar significant positive difference over the group percentage acceptance rate.