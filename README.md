# Web Scraping 
Web Scraping Laptop data from Flipkart

# Tools and Libraries used
 𝐁𝐞𝐚𝐮𝐭𝐢𝐟𝐮𝐥𝐒𝐨𝐮𝐩:parsing and navigating HTML
 
 𝐑𝐞𝐪𝐮𝐞𝐬𝐭𝐬:To fetch the website content
 
 𝐩𝐚𝐧𝐝𝐚𝐬: Data analysis

 # Process
 𝐈𝐧𝐬𝐭𝐚𝐥𝐥 𝐋𝐢𝐛𝐫𝐚𝐫𝐢𝐞𝐬: Installed libraries such Requests,BeautifulSoup and pandas. 

 𝐋𝐨𝐚𝐝 𝐓𝐡𝐞 𝐖𝐞𝐛 𝐏𝐚𝐠𝐞: I sent a get request to flipkart page using the  “Request” library to load web page and ensure a status code 200 to confirm  successful access.

 𝐏𝐚𝐫𝐬𝐞 𝐭𝐡𝐞 𝐇𝐓𝐌𝐋: using”BeautifulSoup” parsed the HTML into readable object like strings,tag.

 𝐄𝐱𝐭𝐫𝐚𝐜𝐭 𝐄𝐥𝐞𝐦𝐞𝐧𝐭𝐬: used find() and find_all() to locate elements such as product name,price,crossprice,rating and offer.
 

 𝐒𝐭𝐫𝐮𝐜𝐭𝐮𝐫𝐞 𝐭𝐡𝐞 𝐃𝐚𝐭𝐚: Extracted data was converted into pandas dataframe and pivot table for analysis.

# Insights

  This anlysis taught me how to gather insights from unstructured  web data effectively.
  
  This data can be used to analyse the price trends,rating and  customer preference
