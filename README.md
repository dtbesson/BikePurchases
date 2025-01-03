# BikePurchases
Another quick Excel project designed by Alex the Analyst on Youtube (https://www.youtube.com/@AlexTheAnalyst). It uses some made-up data on some subjects, including properties such as their gender, marital status, distance of commute to work, and whether or not they have purchased a bike or not. After cleaning the data, we create a dashboard in PowerBI:
![image](https://github.com/user-attachments/assets/6ad2c485-1cc3-4476-be65-875df5c479e4)

Much of this project was completed on my own. I occassionally referred to Alex the Analyst's videos to see what his dashboard looked like, just as a guide for my own.

## The Data
Each data entry has the following attributes:
- ID
- Marital Status
- Gender
- Income
- Children
- Education
- Occupation
- Home Owner
- Cars
- Commute Distance
- Region
- Age
- Purchased Bike

Dataset before pre-processing:
![image](https://github.com/user-attachments/assets/b8c106c9-88ad-4ad4-80ed-8dc4653071be)


## The Process:
- Convert to table.
- Highlight and remove duplicates in the ID column using conditional formatting. 26 in total.
- Change currencies in Income column to numbers without decimal places. Currency formatting sometimes cause problems with graphs.
- Add an Age Bracket column. Instead of making visualisations using 60+ different values in the Age column, we can use just 3 age 'brackets'.
- Switch to PowerBI to create various graphs.

Dataset after pre-processing:
![image](https://github.com/user-attachments/assets/5d6d08bb-8e66-4480-97dc-cd8f0aeec4fb)


## Adding 'Order' Columns:
After creating some visualisations, a problem arose. The entries in the Commute Distance and Age Bracket columns are considered strings. Therefore, when creating visualisations using them, they were appearing in an incorrect order:
![image](https://prod-files-secure.s3.us-west-2.amazonaws.com/0cf2143b-007e-4d2f-91da-9db35b0507e0/f4619f5d-a03a-42f1-aec0-c8fb3c3e4651/image.png)

One way to fix this is to return to Excel and create new columns called Commute Distance Order and Age Bracket Order, which have integer values corresponding to the order in which we want the values to appear. e.g. for entries with "0-1 Miles" in the Commute Distance column, we have a 1 in the Commute Distance Order column. For entries with "1-2 Miles" in the Commute Distance column, we have a 2 in the Commute Distance Order column, and so on. This is done using nested IF statements. Then, in PowerBI, we use the 'Sort by Column' feature, to sort the Commute Distance column by the Commute Distance Order column. By doing so, the visualisation now appears in the correct order.
![image](https://prod-files-secure.s3.us-west-2.amazonaws.com/0cf2143b-007e-4d2f-91da-9db35b0507e0/104ea6f1-5c3d-41cb-a6e1-e4bc7debde94/image.png)

## Points of Learning / Reflection:
- One tip I have picked up is to create a 'working sheet' in your Excel files. In the past, I have always saved a copy of the original dataset, then created a new Excel file with my working on it. Instead of having two separate files, we can create a working sheet within the same file, so we can still keep the original dataset, as well as the modified one.
- I also learnt how to reorder the string columns in a better way, by using the 'Order' columns discussed above.
- Finally, I have realised that cleaning data in Excel, then creating dashboards in PowerBI, is not a very complex process. The complexity of the process comes from understanding what your business questions are, what visualisations to make, and whether your data truly answers these questions. Of course, with fake sample data like this, it is hard to do so.
