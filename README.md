# Russian-Cybercrime-Correlation
My goal is to find a correlation between the volume of Russian ransomware attacks and a downturn in the Russian economy

Almost all other crime has a correlation to economic factors, however the research on this phenomenon and cyber crime is very sparse

I'm using 2 data sets: Russian Quarterly economic data (GDP, Oil Price, Exchange rate, inflation, etc) and Bitcoin Ransomware Attacks (I cut out only the Russian ransomware for this project). 

Using Jupyter Labs, I was able to find the following correlation coefficients:
![C2](https://user-images.githubusercontent.com/111456743/278826442-ede86f84-99ed-4b3f-900c-98572e54d9e0.png)

Taking the 4 highest C2 values (GDP growth, Oil price per barrel, EUR-RUB exchange rate, Interest Rate), I use the following model:
![Model1](https://user-images.githubusercontent.com/111456743/278826650-91b6b4ec-8e4d-4f98-bf4f-fbe5ba78935c.png)

I then get the following (terrible) Mean Squared Error:
![MSE1](https://user-images.githubusercontent.com/111456743/278826444-eaa4bec1-4b73-4b3a-81d4-a06af55cb0f5.png)

This is good though! It made me realize that, since there are so many factors into ransomware incidents, making my model try to guess the EXACT number is near impossible with the amount of data I have right now. So I need to dumb down the predicition from a precise number (I think there's going to be 536 of incidents in Q1 of 2020) into a vague but still useful window (I think there's going to be a HIGH amount of incidents in Q1 of 2020)

I'm going to try doing this by:
1) Making an "average incident" value by measuring that quarter's crime rate against a 3 year average (the year before, during, and after that quarter)
2) Make another "Incident score" value ranging that will either be "HIGH" "AVERAGE" or "LOW", based on that quarters crime rate compared to the 'average incident' value

I can then have my model try to predict if that quarter will have "HIGH" "AVERAGE" or "LOW" number of incidents, based on the economic data of the previous quarter
