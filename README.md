### Will a Customer Accept the Coupon?

**Context**

Imagine driving through town and a coupon is delivered to your cell phone for a restaraunt near where you are driving. Would you accept that coupon and take a short detour to the restaraunt? Would you accept the coupon but use it on a sunbsequent trip? Would you ignore the coupon entirely? What if the coupon was for a bar instead of a restaraunt? What about a coffee house? Would you accept a bar coupon with a minor passenger in the car? What about if it was just you and your partner in the car? Would weather impact the rate of acceptance? What about the time of day?

Obviously, proximity to the business is a factor on whether the coupon is delivered to the driver or not, but what are the factors that determine whether a driver accepts the coupon once it is delivered to them? How would you determine whether a driver is likely to accept a coupon?

**Overview**

The goal of this project is to use what you know about visualizations and probability distributions to distinguish between customers who accepted a driving coupon versus those that did not.

**Data**

This data comes to us from the UCI Machine Learning repository and was collected via a survey on Amazon Mechanical Turk. The survey describes different driving scenarios including the destination, current time, weather, passenger, etc., and then ask the person whether he will accept the coupon if he is the driver. Answers that the user will drive there ‘right away’ or ‘later before the coupon expires’ are labeled as ‘Y = 1’ and answers ‘no, I do not want the coupon’ are labeled as ‘Y = 0’.  There are five different types of coupons -- less expensive restaurants (under \\$20), coffee houses, carry out & take away, bar, and more expensive restaurants (\\$20 - \\$50). 

**Deliverables**

Your final product should be a brief report that highlights the differences between customers who did and did not accept the coupons.  To explore the data you will utilize your knowledge of plotting, statistical summaries, and visualization using Python. You will publish your findings in a public facing github repository as your first portfolio piece. 

### Data Description
Keep in mind that these values mentioned below are average values.

The attributes of this data set include:
1. User attributes
    -  Gender: male, female
    -  Age: below 21, 21 to 25, 26 to 30, etc.
    -  Marital Status: single, married partner, unmarried partner, or widowed
    -  Number of children: 0, 1, or more than 1
    -  Education: high school, bachelors degree, associates degree, or graduate degree
    -  Occupation: architecture & engineering, business & financial, etc.
    -  Annual income: less than \\$12500, \\$12500 - \\$24999, \\$25000 - \\$37499, etc.
    -  Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
    -  Number of times that he/she buys takeaway food: 0, less than 1, 1 to 3, 4 to 8 or greater
    than 8
    -  Number of times that he/she goes to a coffee house: 0, less than 1, 1 to 3, 4 to 8 or
    greater than 8
    -  Number of times that he/she eats at a restaurant with average expense less than \\$20 per
    person: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
    -  Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
    

2. Contextual attributes
    - Driving destination: home, work, or no urgent destination
    - Location of user, coupon and destination: we provide a map to show the geographical
    location of the user, destination, and the venue, and we mark the distance between each
    two places with time of driving. The user can see whether the venue is in the same
    direction as the destination.
    - Weather: sunny, rainy, or snowy
    - Temperature: 30F, 55F, or 80F
    - Time: 10AM, 2PM, or 6PM
    - Passenger: alone, partner, kid(s), or friend(s)


3. Coupon attributes
    - time before it expires: 2 hours or one day

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