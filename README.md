# download-files-with-python3
from bs4 import BeautifulSoup
import requests
import time
import urllib.request
import os

url='http://jandan.net/ooxx'
wb_data=requests.get(url)
time.sleep(2)
soup=BeautifulSoup(wb_data.text,'lxml')
links=soup.select('div > div > div.text > p > img')
meizhi=[]
for link in links:
meizhi.append(link.get('src'))
for ilink in meizhi:
save_path=r'/Users/usernanme/Desktop/downloading'
fileName=ilink.split('/')[-1]
if not os.path.exists(save_path):
os.makedirs(save_path)
urllib.request.urlretrieve(ilink,save_path+os.sep+fileName)
