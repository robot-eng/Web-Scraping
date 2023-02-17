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
<p> OUTPUT </p>

```
Asus VivoBook X4...
Prestigio SmartB...
Prestigio SmartB...
Aspire E1-510
Lenovo V110-15IA...
Lenovo V110-15IA...
Hewlett Packard...
Acer Aspire 3 A3...
Acer Aspire A315...
Acer Aspire ES1-...
Acer Aspire 3 A3...
Acer Aspire 3 A3...
Asus VivoBook Ma...
.............
```
<p>Code 2 modify from code 1</p>

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
    all_productname.append(i.text.replace("$",""))
res = [eval(i) for i in all_productname]
print(res)
print("min price :",min(res))
print("max price :",max(res))
```
<p> OUTPUT </p>

```
[295.99, 299.0, 299.0, 306.99, 321.94, 356.49, 364.46, 372.7, 379.94, 379.95, 391.48, 393.88, 399.0, 399.99, 404.23, 408.98, 409.63, 410.46, 410.66, 416.99, 433.3, 436.29, 436.29, 439.73, 454.62, 454.73, 457.38, 465.95, 468.56, 469.1, 484.23, 485.9, 487.8, 488.64, 488.78, 494.71, 497.17, 498.23, 520.99, 564.98, 577.99, 581.99, 609.99, 679.0, 679.0, 729.0, 739.99, 745.99, 799.0, 809.0, 899.0, 999.0, 1033.99, 1096.02, 1098.42, 1099.0, 1099.0, 1101.83, 1102.66, 1110.14, 1112.91, 1114.55, 1123.87, 1123.87, 1124.2, 1133.82, 1133.91, 1139.54, 1140.62, 1143.4, 1144.2, 1144.4, 1149.0, 1149.0, 
1149.73, 1154.04, 1170.1, 1178.19, 1178.99, 1179.0, 1187.88, 1187.98, 1199.0, 1199.0, 1199.73, 1203.41, 1212.16, 1221.58, 1223.99, 1235.49, 1238.37, 1239.2, 1244.99, 1259.0, 1260.13, 1271.06, 1273.11, 1281.99, 1294.74, 1299.0, 1310.39, 1311.99, 1326.83, 1333.0, 1337.28, 1338.37, 1341.22, 1347.78, 1349.23, 1362.24, 1366.32, 1381.13, 1399.0, 1399.0, 1769.0, 1769.0, 1799.0]
min price : 295.99
max price : 1799.0
```

<p>Code 3</p>

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
```
Asus VivoBook X441NA-GA190
Prestigio SmartBook 133S Dark Grey
Prestigio SmartBook 133S Gold
Aspire E1-510
Lenovo V110-15IAP
Lenovo V110-15IAP
Hewlett Packard 250 G6 Dark Ash Silver
.............
```

<p>Code 4</p>

```Python
from bs4 import BeautifulSoup
import requests
import pandas as pd
from time import sleep
def stock_price():
    url = "https://www.google.com/finance/quote/RJH:BKK?sa=X&ved=2ahUKEwii0_S0-Jv9AhXlRmwGHQ64CJYQ3ecFegQIIhAY"
    res = requests.get(url)
    soup = BeautifulSoup(res.text,"html.parser")
    price = soup.find("div",{"class":"YMlKec fxKbKc"}).text
    return price
price = stock_price()
print("\nRJH : "+str(price))
while 1:
    new_price = stock_price()
    if new_price != price:
        price = stock_price()
        print("\nRJH : "+str(price))
    sleep(1)
```

