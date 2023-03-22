## USER
From now on, you will act as my python3 adviser. Always follow these instructions:
* Only write the code required.
* Give working examples in code blocks using the data I provide.
* Only use real and accurate solutions.
* Ensure string formatting is correct.
* Use only well known and documented flags and options.

- Do NOT provide any extra words or commentary.
- Do NOT invent new flags.
- Do NOT use flags that conflict.
- Do NOT invent tools, functions or methods

## ASSISTANT
Understood. Please provide the data and task you'd like me to solve.

## USER
Make this script multi-threaded:

#!/usr/bin/python3

import os
import datetime
import requests
import json
import re

#website = "@@@DOMAIN@@@"
website = "zip2.com"
yr = "1995"

def download_url(url, ts):
    try:    
        original_url = url
        url = "http://web.archive.org/web/"+ts+"id_/"+url
        print("Downloading "+url+" @ "+ts)
        r2 = requests.get(url, headers=headers)
        url = url.replace("http://", "")
        url = url.replace("-", "_")
        url = re.sub('[^0-9a-zA-Z]+', '_', url)
        file = open(url+".cont.js", "w")
        print(file)
        for x,y in r2.headers.items():
            file.write(x+": "+y+"\n")
        file.write("\n")
        file.write(r2.content.decode())
        file.close()
        file = open(url+".url.txt", "w")
        file.write(original_url)
        file.close()
    except:
        print("download_url -> !!CONN_FAILED!! Retrying..")
        download_url(original_url, ts)

def get_snapshots(url):
    try: 
        r = requests.get("http://web.archive.org/__wb/calendarcaptures?url="+url+"&selected_year="+yr)
        print("Loading snapshots from "+"http://web.archive.org/__wb/calendarcaptures?url="+url+"&selected_year="+yr)
        data = json.loads(r.text)
        for arr in data:
            for arr2 in arr:
                for arr3 in arr2:
                    if arr3==None or 'ts' not in arr3:
                        continue
                    ts = str(arr3["ts"][0])
                    download_url(url, ts)
    except:
        print("get_snapshots -> !!CONN_FAILED!! Retrying..")
        get_snapshots(url)

print("web.archive")

r = requests.get('http://web.archive.org/cdx/search?url='+website+'&matchType=prefix&collapse=urlkey&output=json&fl=original,mimetype,timestamp,endtimestamp,groupcount,uniqcount&filter=!statuscode:[45]..&limit=100000&_=1529584262506')
print("got", str(r.status_code))
#print r.text
data = json.loads(r.text)

headers = {'User-Agent': 'Mozilla/5.0 (Linux; Android 7.1.1; en-bw; Moto E (4) Build/NCQ26.69-46;) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/55.0.2883.91 Mobile Safari/537.36'}

#Access outer array
for arr in data:
    url = arr[0]
#    if url.startswith("http://"):
#        print(url)
    get_snapshots(url)


## ASSISTANT
```
#!/usr/bin/python3

import os
import datetime
import requests
import json
import re
import concurrent.futures

#website = "@@@DOMAIN@@@"
website = "zip2.com"
yr = "1995"

def download_url(url, ts):
    try:    
        original_url = url
        url = "http://web.archive.org/web/"+ts+"id_/"+url
        print("Downloading "+url+" @ "+ts)
        r2 = requests.get(url, headers=headers)
        url = url.replace("http://", "")
        url = url.replace("-", "_")
        url = re.sub('[^0-9a-zA-Z]+', '_', url)
        file = open(url+".cont.js", "w")
        print(file)
        for x,y in r2.headers.items():
            file.write(x+": "+y+"\n")
        file.write("\n")
        file.write(r2.content.decode())
        file.close()
        file = open(url+".url.txt", "w")
        file.write(original_url)
        file.close()
    except:
        print("download_url -> !!CONN_FAILED!! Retrying..")
        download_url(original_url, ts)

def get_snapshots(url):
    try: 
        r = requests.get("http://web.archive.org/__wb/calendarcaptures?url="+url+"&selected_year="+yr)
        print("Loading snapshots from "+"http://web.archive.org/__wb/calendarcaptures?url="+url+"&selected_year="+yr)
        data = json.loads(r.text)
        for arr in data:
            for arr2 in arr:
                for arr3 in arr2:
                    if arr3==None or 'ts' not in arr3:
                        continue
                    ts = str(arr3["ts"][0])
                    download_url(url, ts)
    except:
        print("get_snapshots -> !!CONN_FAILED!! Retrying..")
        get_snapshots(url)

print("web.archive")

r = requests.get('http://web.archive.org/cdx/search?url='+website+'&matchType=prefix&collapse=urlkey&output=json&fl=original,mimetype,timestamp,endtimestamp,groupcount,uniqcount&filter=!statuscode:[45]..&limit=100000&_=1529584262506')
print("got", str(r.status_code))
#print r.text
data = json.loads(r.text)

headers = {'User-Agent': 'Mozilla/5.0 (Linux; Android 7.1.1; en-bw; Moto E (4) Build/NCQ26.69-46;) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/55.0.2883.91 Mobile Safari/537.36'}

#

## USER
Continue

## ASSISTANT
import os
import datetime
import requests
import json
import re
import concurrent.futures

#website = "@@@DOMAIN@@@