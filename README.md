# **Employee Sentiment Analysis — Summary** 

Analysis of 2,191 workplace emails from 10 employees (Jan 2010 – Dec 2011), covering sentiment labeling, monthly employee scoring and ranking, flight-risk identification, and a predictive model of sentiment score. 

## **Top 3 Positive & Negative Employees** 

Ranked by **total sentiment score** (sum of +1/Positive, -1/Negative, 0/Neutral per message) across the full two-year period: 

### **Most positive** 

|Rank|Employee|Total|Score|
|---|---|---|---|
|1|lydia.delgado@enron.com|182||
|2|john.arnold@enron.com|177||
|3|patti.thompson@enron.com|150||



### **Most negative** 

|Rank|Employee|Total|Score|
|---|---|---|---|
|1|kayne.coulter@enron.com|99||
|2|rhonda.denton@enron.com|110||
|3|bobette.riner@ipgdirect.com|122||



Looking at monthly rankings gives us these conclusions: **john.arnold@enron.com** appears in the monthly Top 3 most often (13 of 24 months), and **kayne.coulter@enron.com** appears in the monthly Bottom 3 most often (12 of 24 months) - highlighting that kayne.coulter@enron.com’s tone is the most consistently negative of the group, not just a low two-year total. 

## **Flight Risk - Employees Flagged** 

**Criteria:** 4 or more negative messages within any rolling 30-day window. 

Six of ten employees were flagged: 

- bobette.riner@ipgdirect.com 

- don.baughman@enron.com 

- john.arnold@enron.com 

- johnny.palmer@enron.com 

- kayne.coulter@enron.com 

- sally.beck@enron.com 

Notably, **sally.beck@enron.com** crossed the threshold with the largest margin (5 negative messages in a single 30-day window) despite not ranking among the most consistently negative employees overall. ‘Flight risk’ captures a short, concentrated burst of negativity, a different signal from the employee’s overall tone. 

## **Key Insights & Recommendations** 

- **Overall tone from employees is positive.** 69.6% of messages were labeled Positive under VADER, largely because polite, transactional workplace language (“thanks,” “please,” “sounds good”) scores as mildly positive. “Positive” is seen as “not negative or contentious” rather than genuine enthusiasm when interpreting scores. 

- **Message volume drives raw score more than tone does.** Since score is a running sum, not an average, high-volume communicators accumulate larger positive or negative totals. When comparing employees, consider normalizing by message count alongside the raw total. 

• **Flight-risk and ranking signals disagree in one important case (sally.beck@enron.com)** - a reminder that a single sharp negative burst can be a real early-warning sign even for an employee whose overall tone looks fine. Recommend a manager check-in for all six flagged employees, prioritizing sally.beck@enron.com and kayne.coulter@enron.com given the strength of their respective signals (largest 30-day spike; most consistent negative ranking). 

- **The predictive model (R² = 0.670) shows message behavior alone explains a meaningful, but not complete, share of monthly sentiment.** message_count was the dominant driver, message length mattered little. This model is a reasonable first pass but not the best for full decisions, especially given that a small sample (here it’s 10 employees) limits confidence. 

- **Recommended next steps:** 

   1. Validate VADER’s labels against a transformer-based sentiment model, since VADER struggles with sarcasm and forwarded-email structure. 

   2. Recalibrate the ‘flight-risk’ threshold against real HR outcomes if available, since 60% flagged suggests the current threshold may be too sensitive. 

   3. Expand the model with richer features (timing, thread/recipient context, lagged prior-month score) as more data becomes available. 

