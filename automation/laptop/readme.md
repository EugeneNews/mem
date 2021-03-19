# Laptop Automation

## rotate wallpaper

- [How To Format Date For Display or Use In a Shell Script](https://www.cyberciti.biz/faq/linux-unix-formatting-dates-for-display/) - хороший ресурс по bash
- [Unsplash Developers](https://unsplash.com/documentation#get-a-random-photo) - все методы Unsplash на одной страничке

текущий daily script

```
#!/usr/bin/bash

today=$(date +"%m-%d-%y")

curl --location --request GET 'https://source.unsplash.com/1920x1080/daily' \
--header 'Cookie: ugid=client_id' > ~/Documents/wallpapers/wallpaper-daily-$today.jpg

echo $today >> ~/tuning/temp.log
```


текущий variety script

```
#!/usr/bin/bash

now_minutes=$(date +"%M")

curl --location --request GET 'https://source.unsplash.com/1920x1080/?client_id=client_id&orientation=landscape&drones' \
--header 'Cookie: ugid=client_id' > ~/Documents/wallpapers/wallpaper-variety-$now_minutes.jpg

echo $now_minutes >> ~/tuning/temp.log
```
