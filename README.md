# sampling_data
Ini adalah tugas ke-4 SQL Shell tooling

#!/bin/bash

#1. Tambahkan data set weather_data.xlsx

wget https://github.com/labusiam/dataset/raw/main/weather_data.xlsx

#2. Convert file weather_data.xlsx menjadi weather_2014.csv dan weather_2015.csv

in2csv weather_data.xlsx --sheet "weather_2014" > weather_2014.csv
in2csv weather_data.xlsx --sheet "weather_2015" > weather_2015.csv

#3. Menggabungkan Data weather 2014 dan 2015 menjadi 1 csv kemudian diberi nama weather.csv. menghapus File weather_data.xlsx

csvstack weather_2014.csv weather_2015.csv > weather.csv

rm weather_data.xlsx

#4. sampling pada weather.csv

cat weather.csv | sample -r 0.3 > sample_weather.csv
