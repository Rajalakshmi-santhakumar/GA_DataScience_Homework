# Lesson 4 Homework: Command Line Chipotle


## Command Line Tasks

1. Look at the head and the tail of chipotle.tsv in the data subdirectory of this repo. Think for a minute about how the data is structured. What do you think each column means? What do you think each row means? Tell me! (If you're unsure, look at more of the file contents.)

> Look at the head and the tail of chipotle.tsv in the data subdirectory of this repo


``` Assuming that the current working directory is our class repo ('DS-SEA-08')

cd data
head chipotle.tsv

order_id        quantity        item_name       choice_description      item_price
1       1       Chips and Fresh Tomato Salsa    NULL    $2.39
1       1       Izze    [Clementine]    $3.39
1       1       Nantucket Nectar        [Apple] $3.39
1       1       Chips and Tomatillo-Green Chili Salsa   NULL    $2.39
2       2       Chicken Bowl    [Tomatillo-Red Chili Salsa (Hot), [Black Beans, Rice, Cheese, Sour Cream]]      $16.98
3       1       Chicken Bowl    [Fresh Tomato Salsa (Mild), [Rice, Cheese, Sour Cream, Guacamole, Lettuce]]     $10.98
3       1       Side of Chips   NULL    $1.69
4       1       Steak Burrito   [Tomatillo Red Chili Salsa, [Fajita Vegetables, Black Beans, Pinto Beans, Cheese, Sour Cream, Guacamole, Lettuce]]      $11.75
4       1       Steak Soft Tacos        [Tomatillo Green Chili Salsa, [Pinto Beans, Cheese, Sour Cream, Lettuce]]       $9.25

tail chipotle.tsv

1831    1       Carnitas Bowl   [Fresh Tomato Salsa, [Fajita Vegetables, Rice, Black Beans, Cheese, Sour Cream, Lettuce]]       $9.25
1831    1       Chips   NULL    $2.15
1831    1       Bottled Water   NULL    $1.50
1832    1       Chicken Soft Tacos      [Fresh Tomato Salsa, [Rice, Cheese, Sour Cream]]        $8.75
1832    1       Chips and Guacamole     NULL    $4.45
1833    1       Steak Burrito   [Fresh Tomato Salsa, [Rice, Black Beans, Sour Cream, Cheese, Lettuce, Guacamole]]       $11.75
1833    1       Steak Burrito   [Fresh Tomato Salsa, [Rice, Sour Cream, Cheese, Lettuce, Guacamole]]    $11.75
1834    1       Chicken Salad Bowl      [Fresh Tomato Salsa, [Fajita Vegetables, Pinto Beans, Guacamole, Lettuce]]      $11.25
1834    1       Chicken Salad Bowl      [Fresh Tomato Salsa, [Fajita Vegetables, Lettuce]]      $8.75
1834    1       Chicken Salad Bowl      [Fresh Tomato Salsa, [Fajita Vegetables, Pinto Beans, Lettuce]] $8.75

```

> What do you think each column means? 

Each column represents the Order ID, Quantity, Item Name, Choice description and Item Price respectively for various items in the same/ different orders taken at Chipotle

> What do you think each row means?


Each row represents the item name, choices of ingredients and price of that particular item in the order. Note: Items with identical 'Order ID' probably belong to the same order 

2. How many orders do there appear to be?

From the column 'Order ID', it looks like there are a total of 1834 orders.

3. How many lines are in this file?

```
 wc -l chipotle.tsv
 
```

There a a total of 4623 lines in the file 'chipotle.tsv'

4. Which burrito is more popular, steak or chicken?

| Burrito_type| Code | Result|
|---|---|---|
| Steak Burrito|```grep -i "Steak Burrito" chipotle.tsv > SBchipotle.tsv | wc -l SBchipotle.tsv```| 368 |
| Chicken Burrito | ```grep -i "Chicken Burrito" chipotle.tsv > CBchipotle.tsv | wc -l CBchipotle.tsv``` | 553 |

Therefore, it appears that the Chicken burrito is popular than Steak burrito

5. Do chicken burritos more often have black beans or pinto beans?

| Chicken Burrito_choice| Code | Result|
|---|---|---|
| Black Beans|``` grep -i "Chicken Burrito" chipotle.tsv > CBchipotle.tsv | grep -i "Black Beans" CBchipotle.tsv > CBBBchipotle.tsv |wc -l CBBBchipotle.tsv```| 282 |
| Pinto beans | ```grep -i "Chicken Burrito" chipotle.tsv > CBchipotle.tsv | grep -i "Pinto Beans" CBchipotle.tsv > CBPBchipotle.tsv |wc -l CBPBchipotle.tsv``` | 105 |

Therefore, it appears that the Chicken burrito often have Black beans as compared to Pinto beans

6. Make a list of all of the CSV or TSV files in the [our class repo] (https://github.com/ga-students/DS-SEA-08). repo (using a single command)

```
cd ..
find . -name "*.csv" -o -name "*.tsv"

./data/airlines.csv
./data/Airline_on_time_west_coast.csv
./data/bank-additional.csv
./data/bikeshare.csv
./data/CBBBchipotle.tsv
./data/CBchipotle.tsv
./data/CBPBchipotle.tsv
./data/chipotle.tsv
./data/citibike_feb2014.csv
./data/drinks.csv
./data/drones.csv
./data/hitters.csv
./data/icecream.csv
./data/imdb_1000.csv
./data/mtcars.csv
./data/NBA_players_2015.csv
./data/ozone.csv
./data/pronto_cycle_share/2015_station_data.csv
./data/pronto_cycle_share/2015_trip_data.csv
./data/pronto_cycle_share/2015_weather_data.csv
./data/rossmann.csv
./data/rt_critics.csv
./data/SBchipotle.tsv
./data/sms.tsv
./data/stores.csv
./data/syria.csv
./data/time_series_train.csv
./data/titanic.csv
./data/ufo.csv
./data/vehicles_test.csv
./data/vehicles_train.csv
./data/yelp.csv
./notebooks/GMapJson.csv

```

7. Count the approximate number of occurrences of the word "dictionary" (regardless of case) across all files of [our class repo] (https://github.com/ga-students/DS-SEA-8).

```
grep -ir dictionary . | wc -l

```

The word "dictionary' occurs 61 times.

8. Optional: Use the the command line to discover something "interesting" about the Chipotle data. Try using the commands from the "advanced" section!

```
uniq -c chipotle.tsv | wc -l

```

There are 4589 unique items in the total orders