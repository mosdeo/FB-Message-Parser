# Facebook Message Export Parser (目前only for 繁體中文)

Facebook 允許使用者使下載自己的 Message 對話紀錄，在下載後的 zip 檔案中以 html 檔案保存。
這樣方便在瀏覽器中點選檢視，但是很難給程式讀取做為資料分析用，所以有了專門將對話內容 parser 出來的程式。

由於時間格式不同，原本的版本無法 parser 繁體中文的對話紀錄。

- 原作者時間格式：
```python
dtFormat = '%A, %B %d, %Y at %I:%M%p %Z'
dt.strptime(y.find(class_='meta').string.replace("+01", ""), dtFormat),
```

- 可 parser 繁體中文格式
```python
dtFormat = "%Y年%m月%d日 %H:%M"
dt.strptime(y.find(class_='meta').string[0:-7], dtFormat), # 用 [0:-7] 去除掉繁體中文無法 parser 的 UTC
```

目前這個 fork 暫時只讓繁體中文可以被 parser，和原作者的功能會衝突，日後會想辦法讓這些功能相容。

=======

Facebook has a feature that allows users to download a copy of their data as a zip archive containing htm files with their data. The aim of this parser is to take this archive and to extract a user's Facebook Messages from it; to transfer them into a more useful format, as well as performing some analysis to produce interesting data.


#### Running the Code
The Facebook Export can be downloaded from  the [Facebook Settings](https://www.facebook.com/settings) menu. 

Run "python fb_parser.py" with the 'messages.htm' file in the same directory to export to JSON as proof of concept.

#### Dependencies
The code is written in Python 3+. The parser uses [BeautifulSoup](http://www.crummy.com/software/BeautifulSoup/) to do the bulk of the capture from the htm file.

[Anaconda Python](https://store.continuum.io/cshop/anaconda/) for scientific computing is a simple and easy way to install all the dependencies for the code, alongside many other useful libraries. It can be downloaded [here](http://continuum.io/downloads).
