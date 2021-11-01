# webdriver



### 1. 安装python库

```shell
# python version 3.7+

pip install selenium 
```





### 2. 安装Chromedriver

* 查看Chrome版本号（设置 --> 关于Chrome）
* 访问[淘宝源](http://npm.taobao.org/mirrors/chromedriver/)或[官网](https://chromedriver.chromium.org/downloads)，下载相应版本的Chromedriver驱动
* 将其放置在系统路径下（如：D:\python38\scripts\）



### 3.  获取网页中某个元素的内容

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

browser = webdriver.Chrome()
browser.get('https://qq.com')
browser.implicitly_wait(1)

# 获取所有class='nav-item'的所有元素，并打印出其text内容
items = browser.find_elements(By.CLASS_NAME,'nav-item')

for item in items:
    print(item.text)

browser.close()
```



