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
```
```Python
from bs4 import BeautifulSoup
import requests
import pandas as pd
 
#ระบุตำแหน่งของเว็บปลายทาง
destination = requests.get("https://webscraper.io/test-sites/e-commerce/allinone/computers/laptops")
soup = BeautifulSoup(destination.content, 'html.parser')


#สร้างตัวแปรสำหรับเก็บข้อมูล Title
all_productname_raw = soup.find_all(class_ = "pull-right price")
all_productname = []

  
#ทำการดึงข้อมูลทั้งหมดใน Text มาแสดงผล
for i in all_productname_raw :
    print(i.text)
    p = i.text
    pp = p.replace("$","")
    all_productname.append(pp)
res = [eval(i) for i in all_productname]
print(res)
print("min price :",min(res))
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
    
```
```Python


