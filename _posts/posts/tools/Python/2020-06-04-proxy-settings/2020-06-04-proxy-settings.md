---
layout: post
title: Python | Crawling proxy 설정이 필요한 경우
date: 2020-06-04 11:58:47 +09:00
modified: 
category: [posts, tools]
tags: [crawling]
image: "/assets/img/python_logo.png"
cover: ""
---

### proxy 설정이 필요한 경우

- **requests 사용 시**<br>

```python
import requests
from bs4 import BeautifulSoup

proxies = {'https':'000.000.000.0:9999',
           'http':'000.000.000.0:9999'  
          }

req = requests.get('', proxies=proxies)

```

- **selenium 사용 시**<br>

```python
from selenium import webdriver
from selenium.webdriver.common.proxy import Proxy, ProxyType

import proxy
import mongoDB

def setProxyDriver(driverPath):
    
    options = webdriver.ChromeOptions()
    options.add_argument('--headless')
    options.add_argument('--no-sandbox')
    
    p = proxy.Proxy()
    ip, port = p.getRandomProxyIP('yes')
    proxy_ = str(ip)+':'+str(port)

    prox = Proxy()

    prox.proxy_type = ProxyType.MANUAL
    prox.http_proxy = proxy_
    proxy.socks_proxy = proxy_
    proxy.ssl_proxy = proxy_

    capabilities = webdriver.DesiredCapabilities.CHROME
    prox.add_to_capabilities(capabilities)

    driver = webdriver.Chrome(driverPath, options=options, desired_capabilities=capabilities)

    return driver
```
