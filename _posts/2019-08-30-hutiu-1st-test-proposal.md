---
layout: post
title: "Hutiu First Test Proposal"
date: 2019-08-30
---
Name of proposal: box-logo   
Date of creation: Friday, August 30, 2019  

json object:   

{   
  "end_epoch": 1571131570,    
  "name": "box-logo",     
  "payment_address": "yd5KMREs3GLMe6mTJYr3YrH1juwNwrFCfB",    
  "payment_amount": 500,        
  "start_epoch": 1568556090,        
  "type": 1,        
  "url": "https://bit.ly/30M4LSb"       
}      

<hr />NOTES      
<hr />      
       
With superblocks activated on AXE blockchain, I decided to see if I can submit a test proposal. There are currently no hosted proposal generator.  Below are the methods that I've used to create the test proposal manually.

--The data-hex field is comprised of a JSON object as described in GObject Deserialize which is serialized to hex. 

json object:           
     
{        
  "end_epoch": 1571131570,         
  "name": "box-logo",       
  "payment_address": "yd5KMREs3GLMe6mTJYr3YrH1juwNwrFCfB",         
  "payment_amount": 500,        
  "start_epoch": 1568556090,         
  "type": 1,        
  "url": "https://bit.ly/30M4LSb"         
}             

I removed the spaces from the json object to serialized the object

{"end_epoch":1571131570,"name":"box-logo","payment_address":"PBiQ7dFrQYVtYoQiGKrFZdhKWEKG1RGu44","payment_amount":500,"start_epoch":1568556090,"type":1,"url":"https://bit.ly/30M4LSb"}

****the url was arbitrary and did not resolve correctly to a page

I then used a strings to hex converter ( http://string-functions.com/string-hex.aspx ) to convert the serialized object to hex.
The resulting encoded string:

7b22656e645f65706f6368223a313537313133313537302c226e616d65223a22626f782d6c6f676f222c227061796d656e745f61646472657373223a22504269513764467251595674596f5169474b72465a64684b57454b47315247753434222c227061796d656e745f616d6f756e74223a3530302c2273746172745f65706f6368223a313536383535363039302c2274797065223a312c2275726c223a2268747470733a2f2f6269742e6c792f33304d344c5362227d

I then input the string below into the AXE core wallet via debug console:

gobject prepare 0 1 1567197515 7b22656e645f65706f6368223a313537313133313537302c226e616d65223a22626f782d6c6f676f222c227061796d656e745f61646472657373223a22504269513764467251595674596f5169474b72465a64684b57454b47315247753434222c227061796d656e745f616d6f756e74223a3530302c2273746172745f65706f6368223a313536383535363039302c2274797065223a312c2275726c223a2268747470733a2f2f6269742e6c792f33304d344c5362227d

where 0 = parent hash - Hash of the parent object, usually the root node which has a hash of 0.
where 1 = Object revision number
where 1567197515 = Create time (Unix epoch time)

The above input will result in the TX id:
fb19cee2c0df41c83ceba65416efe2f3cbe24cd901ef0071b43e85bca469aefa

I proceeded to submit the proposal by issuing the gobject sumbit command and appending the TX id to the previous string

gobject submit 0 1 1567197515 7b22656e645f65706f6368223a313537313133313537302c226e616d65223a22626f782d6c6f676f222c227061796d656e745f61646472657373223a22504269513764467251595674596f5169474b72465a64684b57454b47315247753434222c227061796d656e745f616d6f756e74223a3530302c2273746172745f65706f6368223a313536383535363039302c2274797065223a312c2275726c223a2268747470733a2f2f6269742e6c792f33304d344c5362227d fb19cee2c0df41c83ceba65416efe2f3cbe24cd901ef0071b43e85bca469aefa

The output was my own unique proposal hash:
df00b69f5646c72be3416bd1d9d27d49cf9cd825cfb443b1250e2e733024fb1c

I can view the current proposals on network with the command:  
gobject list

I can view specific information in regards to my proposal by issuing the following command along with my unique hash:
gobject get df00b69f5646c72be3416bd1d9d27d49cf9cd825cfb443b1250e2e733024fb1c




