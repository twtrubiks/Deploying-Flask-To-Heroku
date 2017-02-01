# Deploying-Flask-To-Heroku
Deploying a Flask App To Heroku Tutorial 📝  

* [Youtube Demo 待新增]()   

今天教大家如何佈署 Flask App 到 [Heroku](https://dashboard.heroku.com/) 

[Heroku](https://dashboard.heroku.com/) 免費版本

* 可以創造 5個 app。
* 24小時一定要休息6小時的規定。
* 支援很多種程式語言。
* 有SSL(https)。

更多說明請參考 [Heroku](https://dashboard.heroku.com/) 


## 教學

### 步驟一

先註冊 Heroku 帳號，請到 [Heroku](https://dashboard.heroku.com/)  註冊

### 步驟二

請安裝 [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli#download-and-install) (請選擇符合自己得作業系統，這裡用 Windows 介紹)

安裝過程，如果已經有安裝過 [Git](https://git-scm.com/) ，可以把勾勾拿掉，

![alt tag](http://i.imgur.com/A3QLRpA.jpg)

安裝完後，請使用你的 cmd (命令提示字元) 輸入以下指令

``` 
heroku --version
```

如果安裝正確，會跳出你安裝的 Heroku CLI 版本

![alt tag](http://i.imgur.com/UuWGUk1.jpg)


接著再請你使用你的 cmd (命令提示字元) 輸入你的 [Heroku](https://dashboard.heroku.com/) 帳號  和 密碼
``` 
heroku login
```
![alt tag](http://i.imgur.com/6vtoORM.jpg)

### 步驟三

請先 clone 我的簡單 flask 範例

``` 
git clone https://github.com/twtrubiks/Deploying-Flask-To-Heroku.git
```

在資料夾裡，有幾個比較重要的檔案，分別為 
* requirements.txt 
* Procfile
* runtime.txt

#### requirements.txt

這個檔案是要告訴 [Heroku](https://dashboard.heroku.com/) 你的環境需要那些其他的套件

你可以使用 cmd (命令提示字元) 輸入以下指令查看目前電腦所安裝的套件

p.s 請安裝你需要的套件即可

``` 
pip freeze
```
![alt tag](http://i.imgur.com/WxuORWB.jpg)

然後可以使用以下指令匯出文字檔 requirements.txt 
``` 
pip freeze > requirements.txt
```
![alt tag](http://i.imgur.com/mlhGXOk.jpg)

該目錄底下會多出 requirements.txt 

p.s 可以把不需要安裝的套件從 requirements.txt 裡移除

#### Procfile

Procfile 這個檔案是要告訴 [Heroku](https://dashboard.heroku.com/) 要如何啟動這個 web app

在 [Heroku](https://dashboard.heroku.com/) 裡，官方使用 [Gunicorn](http://gunicorn.org/) 來啟動 web server，請參考

[python-gunicorn Heroku](https://devcenter.heroku.com/articles/python-gunicorn)

所以在 <b>requirements.txt</b> 裡，請記得要輸入 [gunicorn](http://gunicorn.org/)

Procfile 檔案，基本使用方法如下
``` 
web gunicorn app_run:app
```
app_run 就是你的 app_run.py，請依照自己設定的名稱自行修改


#### runtime.txt

runtime.txt 檔案裡，只需要簡單的填入你想要指定的 python 版本
``` 
python-3.4.3
```
可參考 [Heroku python-runtimes](https://devcenter.heroku.com/articles/python-runtimes)

如果你不想指定 python 的版本，這個檔案可以忽略。

### 步驟四

#### 先創造 Heroku application

方法一 :

使用你的 cmd (命令提示字元) 輸入以下指令
``` 
heroku create
```
![alt tag](http://i.imgur.com/OJS8K3N.jpg)

p.s 你看到的網址會和我看到的不一樣，請輸入你看到的

方法二 :

到網頁上新增一個 [Heroku application](https://dashboard.heroku.com/new?org=personal-apps)
![alt tag](http://i.imgur.com/8KVzbfD.jpg)

#### 初始化

使用你的 cmd (命令提示字元) 切換到目錄底下，先著初始化
``` 
git init
```

#### 佈署
指定 remote
``` 
heroku git:remote -a tranquil-earth-29753
```
tranquil-earth-29753 這是我自己的，請輸入你的

這些指令你可以在 web app 裡的 deploy 看到

![alt tag](http://i.imgur.com/hQ5FN7A.jpg)

基本上就是 git 的操作，如不清楚什麼是 [Git](https://git-scm.com/)

可以參考我之前寫的 [Git-Tutorials](https://github.com/twtrubiks/Git-Tutorials)

``` 
git add .
git commit -am "make it better"
git push heroku master
```
![alt tag](http://i.imgur.com/pRC4WGW.jpg)

![alt tag](http://i.imgur.com/gPaK7kd.jpg)

佈署完畢，網址的格式為，如上面這張圖
``` 
https://[ 你的 app 名稱 ].herokuapp.com/
```
例如我的網址格式為
``` 
https://tranquil-earth-29753.herokuapp.com/
```

## 畫面

如果使用我的範例佈署成功，畫面應該如下

我的網址為 [https://tranquil-earth-29753.herokuapp.com/](https://tranquil-earth-29753.herokuapp.com/)

![alt tag](http://i.imgur.com/WGjBKEJ.jpg)

## LOG 資訊

<b>log 的資訊非常重要</b>，因為有時候本機端可以正常運行，但佈署上去就無法運行，

所以這時候就要看 log 資訊。

可以使用以下指令查看你在 heroku上 的 web app 的 log 

``` 
heroku logs
```
![alt tag](http://i.imgur.com/1Oe5rER.jpg)

或是可以從網頁端查看

![alt tag](http://i.imgur.com/NmyRvxs.jpg)

網址格式為
``` 
https://dashboard.heroku.com/apps/[ 你的 app 名稱 ]/logs
```


## Reference 
* [Heroku](https://dashboard.heroku.com/)


## License
MIT license
