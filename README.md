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

![image](https://github.com/user-attachments/assets/661b74a2-9bc1-46bd-a2d2-5a0333c5b632)

# price
for i in l_price:
    print(i)

![image](https://github.com/user-attachments/assets/df660d05-b9cf-444c-a586-6bc458c2eb3f)

# Rating
for i in l_rating:
    print(i)

![image](https://github.com/user-attachments/assets/eab21e65-6068-4c79-95b7-a78eedf3148a)

# cross price
for i in l_cross_price:
    print(i)
![image](https://github.com/user-attachments/assets/fcecbed2-8599-4309-969d-490c795b3a55)

# offer
for i in l_offer:
    print(i)
  ![image](https://github.com/user-attachments/assets/8398c498-a1e3-4b8c-b7bb-3169f9429932)

# pandas
import pandas as pd
#Data Frame
data=({"Name":l_name},{"price":l_price},{"Rating":l_rating},{"Crossprice":l_cross_price},{"Offer":l_offer})
df=pd.DataFrame(data)
print(df)

![image](https://github.com/user-attachments/assets/5351d5f5-b4a1-48e5-a882-090a6eedc45f)

min_length = min(len(l_name), len(l_price), len(l_rating), len(l_cross_price), len(l_offer))
l_name = l_name[:min_length]
l_price = l_price[:min_length]
l_rating = l_rating[:min_length]
l_cross_price = l_cross_price[:min_length]
l_offer = l_offer[:min_length]

data = {
    "Name": l_name,
    "Price": l_price,
    "Rating": l_rating,
    "Crossprice": l_cross_price,
    "Offer": l_offer,
}
df = pd.DataFrame(data)
df

![image](https://github.com/user-attachments/assets/aca03af7-5ac8-49a7-8597-05bcdfbd2e76)



#  Based on crossprice
df['Crossprice'] = pd.to_numeric(df['Crossprice'].str.strip(), errors='coerce')


pivot_table = pd.pivot_table(
    df,
    index=['Name'],        
    columns=['Rating'],   
    values=['Crossprice'],      
    aggfunc='mean'         
)

pivot_table = pivot_table.reset_index()

print("\nPivot Table:")
print(pivot_table)

![image](https://github.com/user-attachments/assets/b65e1b43-a639-45ec-b84f-1e2aa95c6ab4)

df = pd.DataFrame(data)

# Based on price
df['Price'] = pd.to_numeric(df['Price'].str.strip(), errors='coerce')

pivot_table = pd.pivot_table(
    df,
    index=['Name'],       
    columns=['Rating'],   
    values=['Price'],     
    aggfunc='mean'         
)

pivot_table = pivot_table.reset_index()

print("\nPivot Table:")
print(pivot_table)

![image](https://github.com/user-attachments/assets/2085a8f5-e16e-4f11-a959-4d6fe0307d3b)

# Based  on offer
df['Offer'] = pd.to_numeric(df['Offer'].str.strip(), errors='coerce')

pivot_table = pd.pivot_table(
    df,
    index=['Name'],        # Rows (index)
    columns=['Rating'],    # Columns
    values=['Offer'],      # Values to aggregate
    aggfunc='mean'         # Aggregation function
)

pivot_table = pivot_table.reset_index()

print("\nPivot Table:")
print(pivot_table)

![image](https://github.com/user-attachments/assets/18ff227b-3405-46fe-8f3d-586a76206fd0)

    
    
