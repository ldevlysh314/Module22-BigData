# Module22-BigData

In this challenge, I used acquired knowledge of SparkSQL to determine key metrics about home sales data. Then I used Spark to create temporary views, partition the data, cache and uncache a temporary table, and verify that the table has been uncached.

Average price for 4 bedroom house sold in each year:
+--------------------+----------+
|round(avg(price), 2)|year(date)|
+--------------------+----------+
|           296363.88|      2022|
|           301819.44|      2021|
|           298353.78|      2020|
|            300263.7|      2019|
---------------------------------

Average price of homes with 3 bedrooms, 3 bathrooms:
+--------------------+----------+
|round(avg(price), 2)|date_built|
+--------------------+----------+
|           290555.07|      2016|
|           293683.19|      2012|
|           292676.79|      2017|
|           290852.27|      2014|
|           295962.27|      2013|
|           291117.47|      2011|
|            288770.3|      2015|
|           292859.62|      2010|
+--------------------+----------+

Average price of a home for each year built that have 3 bedrooms, 3 bathrooms, with two floors,
and are greater than or equal to 2,000 square feet:
+--------------------+----------+
|round(avg(price), 2)|date_built|
+--------------------+----------+
|            293965.1|      2016|
|           307539.97|      2012|
|           280317.58|      2017|
|           298264.72|      2014|
|           303676.79|      2013|
|           276553.81|      2011|
|           297609.97|      2015|
|           285010.22|      2010|
+--------------------+----------+

The "view" rating for the average price of a home, where the homes are greater than
or equal to $350,000?
+----+--------------------+
|view|round(avg(price), 2)|
+----+--------------------+
|  51|           788128.21|
|  54|           798684.82|
|  69|           750537.94|
|  87|           1072285.2|
|  73|           752861.18|
|  64|           767036.67|
|  59|            791453.0|
|  85|          1056336.74|
|  52|           733780.26|
|  71|            775651.1|
|  98|          1053739.33|
|  99|          1061201.42|
|  96|          1017815.92|
| 100|           1026669.5|
|  70|           695865.58|
|  61|           746877.59|
|  75|          1114042.94|
|  78|          1080649.37|
|  89|          1107839.15|
|  77|          1076205.56|
+----+--------------------+
only showing top 20 rows

Using the cached data, the view ratings with average price less than $350,000. 
+----+--------------------+
|view|round(avg(price), 2)|
+----+--------------------+
|   7|           288929.09|
|  15|           284907.04|
|  11|           280356.07|
|  29|           283881.72|
|  42|           289225.45|
|   3|           284314.53|
|  30|           281085.62|
|  34|           286124.07|
|   8|           279099.78|
|  22|           284908.42|
|  28|           285474.25|
|  16|           291990.83|
|  35|           281767.41|
|   0|           285069.21|
|  47|           292925.62|
|  43|           282606.92|
|   5|           278096.94|
|  31|           287988.84|
|  18|           287532.36|
|  27|            281702.6|
+----+--------------------+
only showing top 20 rows


The query that filters out the view ratings with average price of greater than or equal to $350,000 with the parquet DataFrame. 
----+--------------------+
|view|round(avg(price), 2)|
+----+--------------------+
|   7|           288929.09|
|  15|           284907.04|
|  11|           280356.07|
|  29|           283881.72|
|  42|           289225.45|
|   3|           284314.53|
|  30|           281085.62|
|  34|           286124.07|
|   8|           279099.78|
|  22|           284908.42|
|  28|           285474.25|
|  35|           281767.41|
|  16|           291990.83|
|   0|           285069.21|
|  47|           292925.62|
|  43|           282606.92|
|   5|           278096.94|
|  31|           287988.84|
|  18|           287532.36|
|  27|            281702.6|
+----+--------------------+
only showing top 20 rows

The original runtime is 1.351 seconds. The cashe runtime is 0.801 seconds. The cashe time is faster by 0.550 seconds.
The parquet runtime is 1.123 seconds, which is 0.322 seconds slower than cashe runtime.

In the end, the home_sales was no longer cached.

Please use google colab to tun the code.