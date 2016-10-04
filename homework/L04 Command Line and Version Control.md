### Homework Info

####Command Line Tasks
Look at the head and the tail of chipotle.tsv in the data subdirectory of this repo. Think for a minute about how the data is structured. What do you think each column means? What do you think each row means? Tell me! (If you're unsure, look at more of the file contents.)

1. How many orders do there appear to be? 
  * 1834 based on a 'tail' of the file and reviewing the 'Order ID' column 
2. How many lines are in this file?
  * $ wc -l chipotle.tsv
  * 4623 chipotle.tsv
3. Which burrito is more popular, steak or chicken?
  * Chicken burritos are more popular (591 to 386 for Steak)
    * First Attempt
      * $ grep "Steak Burrito" chipotle.tsv > steakburrito.csv
      * $ wc steakburrito.csv = 368  5621 38547 steakburrito.csv
      * $ grep "Chicken Burrito" chipotle.tsv > chickenburrito.csv$ 
      * $ wc chickenburrito.csv = 553  8168 56987 chickenburrito.csv
    * Second Attempt
      * $ awk '/Burrito/ {print $1,$2,$3}' chipotle.tsv > burritoinfo.tsv
      * $ grep 'Chicken Burrito' chipotle.tsv > ChickBur.tsv
      * $ awk '{s+=$2} END {print s}' ChickBur.tsv
      * then repeat for 'Steak'

4. Do chicken burritos more often have black beans or pinto beans?
  * Black Beans are more popular
  * $ grep "Pinto Beans" chickenburrito.csv > chickenburrito_pinto.csv | wc chickenburrito_pinto.csv = 105  1745 12304 chickenburrito_pinto.csv
  * $ grep "Black Beans" chickenburrito.csv > chickenburrito_black.csv | wc chickenburrito_black.csv = 282  4416 30725 chickenburrito_black.csv

5. Make a list of all of the CSV or TSV files in the our class repo. repo (using a single command). You will be working on your local repo on your laptop. Think about how wildcard characters can help you with this task.
  * $ find . -name *.*sv
  
     ./data/airlines.csv
     ./data/Airline_on_time_west_coast.csv
     ./data/bank-additional.csv
     ./data/bikeshare.csv
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
     ./data/sms.tsv
     ./data/stores.csv
     ./data/syria.csv
     ./data/time_series_train.csv
     ./data/titanic.csv
     ./data/ufo.csv
     ./data/vehicles_test.csv
     ./data/vehicles_train.csv
     ./data/yelp.csv

6. Count the approximate number of occurrences of the word "dictionary" (regardless of case) across all files of our class repo.

  * $ grep -r -i "dictionary" ~/Downloads/git/DS-SEA-4/ > dictionary.csv
  * $ wc -w dictionary.csv  =1174 dictionary.csv


* Optional: Use the the command line to discover something "interesting" about the Chipotle data. Try using the commands from the "advanced" section!
  * Using AWK, SORT and UNIQ commands the following were noted:
    * The following items only showed up once the data - Carnitas Salad, Chips and Mild Fresh Tomato Salsa, and Veggie Crispy Tacos
    * The most popular item on the menu seems to be 'Chicken Bowl'
    
    
