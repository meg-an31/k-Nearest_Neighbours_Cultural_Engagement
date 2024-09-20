# k-Nearest Neighbours Cultural Engagement Analysis
Using the k-nearest neighbours algorithm (and cleansed, dimensionally structured data) to allow a prediction of how many people will engage with a type of culture based on multiple factors.
---

### Data cleaning + analysis
I began by combining multiple government datasets on participation in different aspects of culture (the arts, libraries, and heritage sites) which detailed facts about the percentage of people who visited these places in person and online, grouping these stats by demographic and location. I cleaned this data, and structured it in a dimensional database.

Below is an example of a visualisation of this locational data made in Power BI, in which you can filter data by year, location, and engagement type.

![image](https://github.com/user-attachments/assets/6d9bf92c-bda0-48ec-a0f6-d92eec2f93f3)

I also created a dimensional model to hold data about funding for these different aspects of culture. Below is a diagram of the star schema for these databases.

![image](https://github.com/user-attachments/assets/be6fb5c6-0cb3-4615-aeeb-49e4d5b09396)


### Machine learning 
Combining these two databases allows some inferences to be made with machine learning! My idea was to allow the user to input the location, current level of funding, and number of people engaging with one of the three aforementioned culture types.

Using google colab, and datasets generated using my dimensional database, I have created a k-nearest neighbours model which calculates the estimated percentage of people who will engage with that activity in person. It defines each existing data reccord as a point in space, and calculates the distance to the k-nearest points. Then, to estimate the percentage engagement for the user's given data, it averages the percentage engagement of the k-nearest points, _weighting them by their distance_. 

### Problems
As my dataset is relatively small, it often gives results that are illogical (predicting engagement goes down as funding goes up, for example). 

There is also no scaling mechanism for inputs that are very different to existing data points. As a catch-all attempt to mitigate this, I have included a warning message if the data inputted is very far from any existing records.
