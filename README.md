### TABLE OF CONTENTS
[ Dano-Airlines-Satisfaction-Analysis](#dano-airlines-satisfaction-analysis)

[Project Overview](#project_overview)

[Tools Used](#tools_used)

[Dataset Description](#dataset_Description)

[Key Questions Explored](#key_questions_explored)

[Dashboard](#dashboard)

[QUERIES](#queries)

[Key Business Questions and Insights](#key_business_questions_and_insights)

[CONCLUSION](#conclusion)

# Dano-Airlines-Satisfaction-Analysis
Data driven analysis of airline passenger satisfaction using SQL Server and Power BI, with insights to help Dano Airlines improve customer experience.
### Project Overview
This project analyzes customer satisfaction data from Dano Airlines, a UK based airline, using SQL Server for data exploration and Power BI for interactive visualizations.
The goal is to uncover key factors affecting passenger satisfaction such as delays, class of service, and inflight experience and to recommend actionable strategies for improving the airline's overall customer satisfaction rate, which recently dropped below 50%.

---
### Tools Used
SQL Server
  - Data Cleaning
  - Data Querying
    
Power BI
  - Calculated Columns
  - DAX calculations
  - Data Modeling
  - Data Visualization
    
GITHUB
  - Documentation

---
### Dataset Description
 The goal of this project is to analyze customer satisfaction data from over 120,000 passengers and uncover the key drivers influencing satisfaction and dissatisfaction. Based on the findings, strategic recommendations will be made to help Dano Airlines enhance the overall passenger experience and improve their satisfaction score.
 
 The dataset includes responses from passengers and covers variables such as:

- Demographics (e.g., Gender, Age)

- Flight characteristics (e.g., Class, Distance, Delays)

- Service ratings (e.g., Online Booking, In-flight Service, Food & Drink)

- Overall Satisfaction

---
### Key Questions Explored

- How does satisfaction vary by gender, age, class, and type of travel?

- What impact do delays have on passenger satisfaction?

- Which in-flight services are most strongly associated with dissatisfaction?

- What KPIs should Dano Airlines track to monitor improvement?
  
- Service Rating Performance

---
### Dashboard

Here's a visual overview of the Dano Airlines passenger satisfaction dashboard:

![Dano Airlines Dashboard](./Dano_Airlines_Dashboard.png)

---
### QUERIES
1) ### Satisfaction by Gender
```
SELECT Gender, Satisfaction, COUNT(*) AS Count
FROM Airline_Data
GROUP BY Gender, Satisfaction;
```
2) ### Satisfaction by Age Group
```
SELECT 
  CASE 
    WHEN Age < 20 THEN 'Under 20'
    WHEN Age BETWEEN 20 AND 34 THEN '20–34'
    WHEN Age BETWEEN 35 AND 49 THEN '35–49'
    WHEN Age BETWEEN 50 AND 64 THEN '50–64'
    ELSE '65+' 
  END AS AgeGroup,
  Satisfaction,
  COUNT(*) AS Count
FROM Airline_Data
GROUP BY 
  CASE 
    WHEN Age < 20 THEN 'Under 20'
    WHEN Age BETWEEN 20 AND 34 THEN '20–34'
    WHEN Age BETWEEN 35 AND 49 THEN '35–49'
    WHEN Age BETWEEN 50 AND 64 THEN '50–64'
    ELSE '65+' 
  END,
  Satisfaction;
```

3) ### Satisfactio by Type of Travel
  ```
 SELECT Type_of_Travel, Satisfaction, COUNT(*) AS Count
FROM Airline_Data
GROUP BY Type_of_Travel, Satisfaction;
```

4) ### Satisfaction by Class
```
SELECT Class, Satisfaction, COUNT(*) AS Count
FROM Airline_Data
GROUP BY Class, Satisfaction;
```

5) ### Satisfaction by Flight Distance Category
```
SELECT 
  CASE 
    WHEN Flight_Distance < 500 THEN '<500 km'
    WHEN Flight_Distance BETWEEN 500 AND 1500 THEN '500–1500 km'
    ELSE '>1500 km' 
  END AS DistanceCategory,
  Satisfaction,
  COUNT(*) AS Count
FROM Airline_Data
GROUP BY 
  CASE 
    WHEN Flight_Distance < 500 THEN '<500 km'
    WHEN Flight_Distance BETWEEN 500 AND 1500 THEN '500–1500 km'
    ELSE '>1500 km' 
  END,
  Satisfaction;
```

6) ### Satisfaction by Departure Delay
```
SELECT 
  CASE WHEN Departure_Delay > 15 THEN 'Delayed' ELSE 'On Time' END AS DepartureStatus,
  Satisfaction,
  COUNT(*) AS Count
FROM Airline_Data
GROUP BY 
  CASE WHEN Departure_Delay > 15 THEN 'Delayed' ELSE 'On Time' END,
  Satisfaction;
```
 7) ### Satisfaction by Arrival Delay
 ```
SELECT 
  CASE WHEN Arrival_Delay > 15 THEN 'Delayed' ELSE 'On Time' END AS ArrivalStatus,
  Satisfaction,
  COUNT(*) AS Count
FROM Airline_Data
GROUP BY 
  CASE WHEN Arrival_Delay > 15 THEN 'Delayed' ELSE 'On Time' END,
  Satisfaction;
```

8) ### Average Ratings of Services
```
SELECT 
  CASE WHEN Arrival_Delay > 15 THEN 'Delayed' ELSE 'On Time' END AS ArrivalStatus,
  Satisfaction,
  COUNT(*) AS Count
FROM Airline_Data
GROUP BY 
  CASE WHEN Arrival_Delay > 15 THEN 'Delayed' ELSE 'On Time' END,
  Satisfaction;
```

---
### Key Business Questions and Insights
### Passengers Satisfaction Across Demographics
1. ****How does satisfaction vary across Gender, Age, and Customer Type****?
- Gender Insights: Female passengers showed slightly higher satisfaction levels than male passengers.

- Age Group Insights:  Passengers aged 41–60 reported the highest satisfaction levels, while those aged 60 and above showed notably lower satisfaction.

- Customer Type: Loyal customers (frequent fliers) consistently showed higher satisfaction than disloyal or first-time travelers.

### Recommendations
 Introduce comfort-driven services for senior passengers, such as priority assistance and better seat options. Focus marketing campaigns on the 41–60 age segment who are already more satisfied.
 
-  Loyalty Program Optimization: Invest in loyalty schemes. Reward frequent flyers with points, upgrades, or perks to retain high value customers.

-  Targeted Marketing: Customize campaigns for middle aged travelers and loyal customers, as they are your most satisfied segments. For younger passengers, offer personalized travel experiences (e.g., digital check ins, entertainment features).

2. ****Impact of Travel Type and Class on Satisfaction****

Insight: Business class and business travel recorded the highest satisfaction scores. In contrast, Economy plus class passengers, especially those on personal  trips, were notably less satisfied.

Implication: Higher paying customers are experiencing better services, while the bulk of passengers (Economy class) feel underserved.

### Recommendation:

- Service Rebalancing: Improve Economy class experience. Enhance seat comfort, food service, and boarding experience.

- Value Up Promotions: Offer bundled upgrades (e.g., priority boarding + extra legroom) for Economy passengers to improve perception at a reasonable cost.

3. ****Satisfaction vs. Flight Delays****

Insight: Both departure and arrival delays beyond 16 minutes significantly reduce satisfaction. Punctuality plays a major role in customer perception.

Implication: Delays reflect operational inefficiencies and directly hurt satisfaction, regardless of service quality.

Recommendation:

Delay Mitigation: Implement real time delay tracking and predictive scheduling to reduce disruptions.

Proactive Communication: Notify customers early of delays, offer lounge access, or small compensations (e.g., meal vouchers) to manage dissatisfaction.

4.****Flight Distance and Satisfaction****: 

Insight:
Passengers on long-distance flights (over 1500 km) reported higher satisfaction, while those on short flights (under 500 km) were the least satisfied.

Why this happens (Implication):
You’d think short flights would be easier to manage and lead to fewer complaints but that’s not always true.

Here’s why:

- On short haul flights, passengers expect things to move quickly fast check in, boarding, minimal delays. When these are inefficient, it frustrates them more because the total flight time is short.

- There’s less room for error. A 30 minute delay on a 1 hour flight feels much worse than on a 6 hour flight.

- On long haul flights, passengers tend to have lower expectations for speed but higher ones for comfort and airlines usually provide more services like meals, in flight entertainment, and better seating, which improves satisfaction.

### Recommendation:

For Short Flights (under 500 km):

- Make the pre flight process smoother: shorter wait times, faster check-in, and priority boarding.

- Ensure flights leave on time people are very sensitive to delays on short routes.

- Keep things simple but efficient.

- For Long Flights (over 1500 km):

- Highlight the comfort, meals, and in flight services in your marketing.

- Show potential customers that they’ll be well taken care of—this is attractive to business travelers and long-distance tourists.

- Maintain or improve service quality to retain loyalty.

5.****Key Drivers of Satisfaction: Service Ratings****

 Insight:
When looking at what makes passengers feel satisfied, a few services stand out as the biggest influences:

- Inflight WiFi

- Seat Comfort

- Cleanliness

- Onboard Service (e.g., meals, staff attitude, etc.)

These services consistently align with the highest satisfaction scores, meaning when they are rated well, overall satisfaction is also high.

 Why it matters (Implication):
This tells us something important:
- Passengers care most about what happens during the flight not so much about things like airport check in or baggage claims.

In other words, the in air experience is where airlines either win or lose customer loyalty. If you want to improve satisfaction, focus on what people actually feel while seated on the plane.

### Recommendation:

###  Cabin Investment:

- Upgrade seats more legroom, better cushioning, ergonomic designs in other word make them confortable while on air.

- Keep cabins spotless,cleanliness plays a big role in perceived quality.

- Train and support cabin crew to deliver consistently friendly and professional service.

### Wi-Fi & Entertainment:

- In today's world, passengers expect to stay connected even in the air.

- Especially for business travelers or long haul passengers, good Wi Fi and engaging inflight entertainment are not luxuries they’re expectations.

Slow, unreliable connections or outdated movie options leave a bad impression.

So, in summary:
To boost satisfaction, improve what passengers feel during the flight. That means cleaner cabins, comfier seats, smoother service, and good WiFi. These little comforts leave lasting impressions. They all had 5 to 6 ratings which is fair but it can also be better when we look into what could be wrong and provide solutions.

---
### CONCLUSION
This analysis of Dano Airlines passenger satisfaction reveals that in flight experience, travel class, flight punctuality, and targeted demographic engagement are the key levers influencing customer perception. While long haul and business class passengers tend to be more satisfied, short haul and economy travelers report lower satisfaction, highlighting areas for operational and service improvement. By focusing on the most impactful service areas like onboard comfort, cleanliness, reliable WiFi, and punctual departures Dano Airlines can significantly uplift its overall satisfaction rate. Also  segmenting initiatives by age, gender, and flight type ensures that efforts are both effective and customer centric.
With data driven strategies and thoughtful service enhancements, Dano Airlines is well positioned to rebuild trust, retain loyal customers, and improve its competitive standing in the airline industry.

 What to Do:

- Invest in Cabin Comfort & Reliable Wi-Fi

- Reduce Boarding/Departure Delays

 - Target Marketing to Satisfied Demographics (41–60 yrs, Business Travelers)

 - Elevate Economy Class Experience

  - Goal: Win back customer trust & push satisfaction above 80%!
















  







