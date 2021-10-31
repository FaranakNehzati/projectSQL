# ProjectSQL
## Introduction
In this project we worked with a mobile game company dataset. We need to calculate retention rate for each given day of the year so we can graph them and get insights about the Company performance.  Retention rate is a common metric in e-commerce and service industry. For this particular dataset we are going to roll a 30 retention. The rate is calculated by dividing the players retained for 30 days with players joined on each given day. Based on this rate we can make better decisions about company policies.
## Description
For creating our retention table to find the rate we need to know how many players played this game 30 days or more after the join date.  I used joins and nested queries to refine the results(Query no.1) I uploaded the chart on Sheets and made a graph..Retention rate looks more or less stable till the last days of the period.
there's a small part of the table: 

<img width="338" alt="retentionTableDemo" src="https://user-images.githubusercontent.com/59418722/139507201-29b01c88-7133-4d14-9929-e093691ed373.png">
to see the whole table you can check [this link](https://docs.google.com/spreadsheets/d/1sIoAwZYjOvSxGNlQqi5jZi-XbUfp5vBVthGqkuW1CiM/edit?usp=sharing)

### Retention Rate by Day

![Fractional Retention Rate by Day](https://user-images.githubusercontent.com/59418722/139507991-49083fa1-50d2-4207-b449-1add5f50578a.png)

After this I wanted to know if players on retention period spent more money than the ones who played 30 days and lower. I used joins and nested queries to find the average spending for both groups. The results were higher for players in the retention period. (Query no.2)
here is the result table:

<img width="154" alt="spentByRetention" src="https://user-images.githubusercontent.com/59418722/139508355-dbf513c6-dda8-4766-9410-46e129cdffbf.png">

Also I looked at location to be able to find out if any particular location had the most players in the 30 day retention period. South America had the most players and the most money spent. (Query no.3)
here is the table:

<img width="230" alt="spentByLocation" src="https://user-images.githubusercontent.com/59418722/139508607-3c54b689-e07f-41d6-968b-cc1723889769.png">

To see which region has the most players I made the graph below: 

![Number of players by location](https://user-images.githubusercontent.com/59418722/139508793-b00179cc-12f3-44bf-8ba0-2014b1b1e35f.png)

And for each region I graphed the average spending:

![Average Spending for each Region (1)](https://user-images.githubusercontent.com/59418722/139597035-9fedb108-38c8-4ef9-a3f6-a990316c4efa.png)

In finding out the retention rate I had an issue with putting players joined each day  next to players retained therefore I used nested queries. And it is slightly long because I didn't use any CASE statement. But my partner Jason could write a shorter query for this which I think can be another way of getting to the table.
After studying the graph for the retention table I observed that the retention rate decreased dramatically through the last few days. I believe it is because of the lack of data for the months after. As for me we can ignore the part in the visualization. With further data we can have a better understanding of it.

## Conclusion

Retention rate is stable and we are not losing more than we retain most of the time. As mentioned before, most players are from the South America region. They made the most purchases as well. Europe and Oceania are among the lowest regions but it can be due to less population in those two continents. In my opinion we need to work more on Asia. It's one of the most populated regions but it doesn't have a high number of players.




