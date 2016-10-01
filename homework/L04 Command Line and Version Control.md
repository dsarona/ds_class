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
  
  * $ grep "Steak Burrito" chipotle.tsv > steakburrito.csv
  * $ wc steakburrito.csv = 368  5621 38547 steakburrito.csv
  
  * $ grep "Chicken Burrito" chipotle.tsv > chickenburrito.csv$ 
  * $ wc chickenburrito.csv = 553  8168 56987 chickenburrito.csv
 #2 
  * $ awk '/Burrito/ {print $1,$2,$3}' chipotle.tsv > burritoinfo.tsv
  * $ grep 'Chicken Burrito' chipotle.tsv > ChickBur.tsv
  * $ awk '{s+=$2} END {print s}' ChickBur.tsv
  * then repeat for 'Steak'

4. Do chicken burritos more often have black beans or pinto beans?
  * Black Beans are more popular
  * $ grep "Pinto Beans" chickenburrito.csv > chickenburrito_pinto.csv | wc chickenburrito_pinto.csv = 105  1745 12304 chickenburrito_pinto.csv
  * $ grep "Black Beans" chickenburrito.csv > chickenburrito_black.csv | wc chickenburrito_black.csv = 282  4416 30725 chickenburrito_black.csv

5. Make a list of all of the CSV or TSV files in the our class repo. repo (using a single command). You will be working on your local repo on your laptop. Think about how wildcard characters can help you with this task.
6. Count the approximate number of occurrences of the word "dictionary" (regardless of case) across all files of our class repo.

* Optional: Use the the command line to discover something "interesting" about the Chipotle data. Try using the commands from the "advanced" section!
