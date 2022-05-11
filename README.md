# sampling_data
Ini adalah tugas ke-4 SQL Shell tooling

#!/bin/bash

#1. Tambahkan data set weather_data.xlsx
if [[ ! -f "$FILE" ]];
then
        wget https://github.com/labusiam/dataset/raw/main/weather_data.xlsx
        echo "File $FILE has been downloaded"
else
        echo "File $FILE already exist"
fi

#2. Convert file weather_data.xlsx menjadi weather_2014.csv dan weather_2015.csv
if [[ ! -f "$FILE_2014" && "$FILE_2015" ]];
then
        in2csv $FILE --sheet "weather_2014" > $FILE_2014
        in2csv $FILE --sheet "weather_2015" > $FILE_2015
        echo "File weather_2014 dan weather_2015 has been converted"
else
        echo "File weather_2014 dan weather_2015 already exist"
fi

#3. Menggabungkan Data weather 2014 dan 2015 menjadi 1 csv kemudian diberi nama weather.csv. menghapus File weather_data.xlsx

csvstack weather_2014.csv weather_2015.csv > weather.csv

rm weather_data.xlsx

#4. sampling pada weather.csv

cat weather.csv | sample -r 0.3 > sample_weather.csv
