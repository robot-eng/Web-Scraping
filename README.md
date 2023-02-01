# Web-Scraping

<p>Code 1</p>

```Python
from bs4 import BeautifulSoup
import requests
import pandas as pd
 
#ระบุตำแหน่งของเว็บปลายทาง
destination = requests.get("https://webscraper.io/test-sites/e-commerce/allinone/computers/laptops")
soup = BeautifulSoup(destination.content, 'html.parser')


#สร้างตัวแปรสำหรับเก็บข้อมูล Title
all_productname_raw = soup.find_all(class_ = "title")
all_productname = []


#ทำการดึงข้อมูลทั้งหมดใน Text มาแสดงผล
for i in all_productname_raw :
    print(i.text)
    all_productname.append(i.text)
    
# ขั้นตอนต่อมาเราก็ทำการเพิ่มคำสั่งในการค้นหา title ที่เป็น class ที่เอาไว้สำหรับแสดงชื่อของสินค้าทั้งหมดของเว็บนี้นั่นเอง
หากสงสัยว่ารู้ได้อย่างไรว่าชื่อ "title" ให้ทำการดูข้อมูล HTML เพียว ๆ ของเว็บดังกล่าวจะพบว่าใช้ class ชื่อ title
```

```Python
from bs4 import BeautifulSoup
import requests
import pandas as pd
 
#ระบุตำแหน่งของเว็บปลายทาง
destination = requests.get("https://webscraper.io/test-sites/e-commerce/allinone/computers/laptops")
soup = BeautifulSoup(destination.content, 'html.parser')


#สร้างตัวแปรสำหรับเก็บข้อมูล Title
all_productname_raw = soup.find_all(class_ = "title")
all_productname = []


#ทำการดึงข้อมูลทั้งหมดใน Text มาแสดงผล
for i in all_productname_raw :
    print(i.get("title"))
    all_productname.append(i.get("title"))
    
#  โดยการใส่สิ่งที่เราต้องการ (Attribute ที่ต้องการไปดึงข้อมูล) ลงไปแทนที่จะใส่ .text เพื่อดึงข้อความแบบธรรมดา
ในกรณีนี้เราจะใช้ .get("title") แทน เพื่อดึงข้อมูลภายใน title ออกมา ไม่ใช่ text ที่แสดงนั่นเอง
```
```Python


