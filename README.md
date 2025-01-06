# Web-Scraping
# install request
import requests
from bs4 import BeautifulSoup

l_name=[]
l_price=[]
l_rating=[]
l_cross_price=[]
l_offer=[]

page_num=input("Enter the page number")
for i in range(1,int(page_num)+1):
    
# url
    url='https://www.flipkart.com/search?q=laptop+under+100000+rupees&sid=6bo%2Cb5g&as=on&as-show=on&otracker=AS_QueryStore_OrganicAutoSuggest_1_19_na_na_na&otracker1=AS_QueryStore_OrganicAutoSuggest_1_19_na_na_na&as-pos=1&as-type=HISTORY&suggestionId=laptop+under+100000+rupees%7CLaptops&requestId=f9492b31-f8af-4420-b62b-f3bfea3ef413&as-backfill=on&page='+str(i)
    req=requests.get(url)
    content=BeautifulSoup(req.content,'html.parser')
# Html export
    name=content.find_all('div',{'class':"KzDlHZ"})
    price=content.find_all('div',{'class':'Nx9bqj _4b5DiR'})
    rating=content.find_all('div',{'class':'XQDdHH'})
    cross_price=content.find_all('div',{'class':'yRaY8j ZYYwLA'})
    offer=content.find_all('div',{'class':'UkUFwK'})
    print("Laptop_in_page"+str(i))
    print(len(name))

# append
    for i in name:
         l_name.append(i.text)

    for i in price:
        l_price.append(i.text.replace("₹"," ").replace(",",""))

    for i in rating:
        l_rating.append(i.text)

    for i in cross_price:
        l_cross_price.append(i.text.replace("₹", " ").replace(",",""))
        
    
    for i in offer:
        l_offer.append(i.text.replace("off", " ").replace("%",""))

  # name
for i in l_name:
    print(i)
