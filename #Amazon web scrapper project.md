```python
#import libraries
from bs4 import BeautifulSoup
import requests
import matplotlib
import time
import datetime
import smtplib
```


```python
#connect to website and data
URL = 'https://www.amazon.com/Funny-Data-Systems-Business-Analyst/dp/B07FNW9FGJ/ref=sr_1_3?dchild=1&keywords=data%2Banalyst%2Btshirt&qid=1626655184&sr=8-3&customId=B0752XJYNL&th=1%27'
headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36", "Accept-Encoding":"gzip, deflate", "Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8", "DNT":"1","Connection":"close", "Upgrade-Insecure-Requests":"1"}
page = requests.get (URL, headers = headers)
soup1 = BeautifulSoup(page.content, "html.parser")
soup2 = BeautifulSoup(soup1.prettify(),"html.parser")
title = soup2.find(id = 'productTitle').get_text()
title = title.strip()
price = soup2.find(id = 'desktop_unifiedPrice').get_text()
price = price.strip()
print(title)
print(price)
```

    Funny Got Data MIS Data Systems Business Analyst T-Shirt
    
    


```python
today = datetime.date.today()
print(today)
```

    2024-09-17
    


```python
import csv
headers = ['Title','Price','Today']
data = [title,price,today]
with open('Amazonwebscrapperdataset.csv','w', newline='', encoding = 'UTF8') as f:
    writer = csv.writer(f)
    writer.writerow(headers)
    writer.writerow(data)

    
```


```python
import pandas as pd
df = pd.read_csv(r"C:\Users\sweet\Amazonwebscrapperdataset.csv")
print(df)
```

                                                   Title  Price       Today
    0  Funny Got Data MIS Data Systems Business Analy...    NaN  2024-09-17
    


```python
with open('Amazonwebscrapperdataset.csv','a+', newline='', encoding = 'UTF8') as f:
    writer = csv.writer(f)
    writer.writerow(data)
    
```


```python
def check_price():
    URL = 'https://www.amazon.com/Funny-Data-Systems-Business-Analyst/dp/B07FNW9FGJ/ref=sr_1_3?dchild=1&keywords=data%2Banalyst%2Btshirt&qid=1626655184&sr=8-3&customId=B0752XJYNL&th=1%27'
    headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36", "Accept-Encoding":"gzip, deflate", "Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8", "DNT":"1","Connection":"close", "Upgrade-Insecure-Requests":"1"}
    page = requests.get (URL, headers = headers)
    soup1 = BeautifulSoup(page.content, "html.parser")
    soup2 = BeautifulSoup(soup1.prettify(),"html.parser")
    title = soup2.find(id = 'productTitle').get_text()
    title = title.strip()
    price = soup2.find(id = 'desktop_unifiedPrice').get_text()
    price = price.strip()
    print(title)
    print(price)
    today = datetime.date.today()
    print(today)
    import csv
    headers = ['Title','Price','Today']
    data = [title,price,today]
    with open('Amazonwebscrapperdataset.csv','a+', newline='', encoding = 'UTF8') as f:
        writer = csv.writer(f)
        writer.writerow(data)
    if (price < 15):
        send_mail
```


```python
while(True):
    check_price()
    time.sleep(5)
```

    Funny Got Data MIS Data Systems Business Analyst T-Shirt
    
    2024-09-17
    Funny Got Data MIS Data Systems Business Analyst T-Shirt
    
    2024-09-17
    Funny Got Data MIS Data Systems Business Analyst T-Shirt
    
    2024-09-17
    Funny Got Data MIS Data Systems Business Analyst T-Shirt
    
    2024-09-17
    Funny Got Data MIS Data Systems Business Analyst T-Shirt
    
    2024-09-17
    

    
    KeyboardInterrupt
    
    


```python
import pandas as pd
df = pd.read_csv(r"C:\Users\sweet\Amazonwebscrapperdataset.csv")
print(df)
```

                                                   Title  Price       Today
    0  Funny Got Data MIS Data Systems Business Analy...    NaN  2024-09-17
    1  Funny Got Data MIS Data Systems Business Analy...    NaN  2024-09-17
    2  Funny Got Data MIS Data Systems Business Analy...    NaN  2024-09-17
    3  Funny Got Data MIS Data Systems Business Analy...    NaN  2024-09-17
    4  Funny Got Data MIS Data Systems Business Analy...    NaN  2024-09-17
    5  Funny Got Data MIS Data Systems Business Analy...    NaN  2024-09-17
    6  Funny Got Data MIS Data Systems Business Analy...    NaN  2024-09-17
    


```python
def send_mail():
    server = smtplib.SMTP_SSL('smtp.gmail.com',465)
    server.ehlo()
    #server.starttls()
    server.ehlo()
    server.login('sweetykannepalli@gmail.com','*********')
    
    subject = "The Shirt you want is below $15! Now is your chance to buy!"
    body = "Sri, This is the moment we have been waiting for. Now is your chance to pick up the shirt of your dreams. Don't mess it up! Link here: https://www.amazon.com/Funny-Data-Systems-Business-Analyst/dp/B07FNW9FGJ/ref=sr_1_3?dchild=1&keywords=data+analyst+tshirt&qid=1626655184&sr=8-3"
   
    msg = f"Subject: {subject}\n\n{body}"
    
    server.sendmail(
        'sweetykannepalli@gmail.com',
        msg
     
    )
```


```python

```
