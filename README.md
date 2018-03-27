# Deploying-Flask-To-Heroku

Deploying a Flask App To Heroku Tutorial 📝

* [Youtube Demo](https://youtu.be/fidKOYWWfkM)
* [How to use Heroku Postgres deploying](https://youtu.be/OvQetdMN88E)

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

```cmd
heroku --version
```

如果安裝正確，會跳出你安裝的 Heroku CLI 版本

![alt tag](http://i.imgur.com/UuWGUk1.jpg)

接著再請你使用你的 cmd (命令提示字元) 輸入你的 [Heroku](https://dashboard.heroku.com/) 帳號  和 密碼

```cmd
heroku login
```

![alt tag](http://i.imgur.com/6vtoORM.jpg)

### 步驟三

請先 clone 我的簡單 flask 範例

```cmd
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

```cmd
pip freeze
```

![alt tag](http://i.imgur.com/WxuORWB.jpg)

然後可以使用以下指令匯出文字檔 requirements.txt

```cmd
pip freeze > requirements.txt
```

![alt tag](http://i.imgur.com/mlhGXOk.jpg)

該目錄底下會多出 requirements.txt

p.s 可以把不需要安裝的套件從 requirements.txt 裡移除

#### Procfile

Procfile 這個檔案是要告訴 [Heroku](https://dashboard.heroku.com/) 要如何啟動這個 web app

在 [Heroku](https://dashboard.heroku.com/) 裡，官方使用 [Gunicorn](http://gunicorn.org/) 來啟動 web server，請參考

[python-gunicorn Heroku](https://devcenter.heroku.com/articles/python-gunicorn)

所以在 **requirements.txt** 裡，請記得要輸入 [gunicorn](http://gunicorn.org/)

Procfile 檔案，基本使用方法如下

```text
web gunicorn app_run:app
```

app_run 就是你的 app_run.py，請依照自己設定的名稱自行修改

#### runtime.txt

runtime.txt 檔案裡，只需要簡單的填入你想要指定的 python 版本

```text
python-3.4.3
```

可參考 [Heroku python-runtimes](https://devcenter.heroku.com/articles/python-runtimes)

如果你不想指定 python 的版本，這個檔案可以忽略。

### 步驟四

#### 先創造 Heroku application

方法一 :

使用你的 cmd (命令提示字元) 輸入以下指令

```cmd
heroku create
```

![alt tag](http://i.imgur.com/OJS8K3N.jpg)

p.s 你看到的網址會和我看到的不一樣，請輸入你看到的

方法二 :

到網頁上新增一個 [Heroku application](https://dashboard.heroku.com/new?org=personal-apps)
![alt tag](http://i.imgur.com/8KVzbfD.jpg)

#### 初始化

使用你的 cmd (命令提示字元) 切換到目錄底下，先著初始化

```cmd
git init
```

#### 佈署

指定 remote

```cmd
heroku git:remote -a tranquil-earth-29753
```

tranquil-earth-29753 這是我自己的，請輸入你的

這些指令你可以在 web app 裡的 deploy 看到

![alt tag](http://i.imgur.com/hQ5FN7A.jpg)

基本上就是 git 的操作，如不清楚什麼是 [Git](https://git-scm.com/)

可以參考我之前寫的 [Git-Tutorials](https://github.com/twtrubiks/Git-Tutorials)

```cmd
git add .
git commit -am "make it better"
git push heroku master
```

![alt tag](http://i.imgur.com/pRC4WGW.jpg)

![alt tag](http://i.imgur.com/gPaK7kd.jpg)

佈署完畢，網址的格式為，如上面這張圖

```url
https://[ 你的 app 名稱 ].herokuapp.com/
```

例如我的網址格式為

```url
https://tranquil-earth-29753.herokuapp.com/
```

commit ID [4a42e26aee2bff1b10247d7e8a75d4d86b0c83b8](https://github.com/twtrubiks/Deploying-Flask-To-Heroku/tree/4a42e26aee2bff1b10247d7e8a75d4d86b0c83b8)

## 畫面

如果使用我的範例佈署成功，畫面應該如下

我的網址為 [https://tranquil-earth-29753.herokuapp.com/](https://tranquil-earth-29753.herokuapp.com/)

![alt tag](http://i.imgur.com/WGjBKEJ.jpg)

## LOG 資訊

**log 的資訊非常重要** ，因為有時候本機端可以正常運行，但佈署上去就無法運行，

所以這時候就要看 log 資訊。

可以使用以下指令查看你在 heroku上 的 web app 的 log

```cmd
heroku logs
```

![alt tag](http://i.imgur.com/1Oe5rER.jpg)

或是可以從網頁端查看

![alt tag](http://i.imgur.com/NmyRvxs.jpg)

網址格式為

```url
https://dashboard.heroku.com/apps/[ 你的 app 名稱 ]/logs
```

## 如何在 heroku 上使用 database

請先到下列網址建立 database
[heroku addons](https://elements.heroku.com/addons)

你會看到很多 db ，這裡用 Heroku Postgres 當作範例

![alt tag](http://i.imgur.com/AxoKeka.jpg)

接著安裝就行了，如果你還沒有登入，他會請你先登入

![alt tag](http://i.imgur.com/FCaqoPB.jpg)

選擇你的 db 是要給哪個專案用的

![alt tag](http://i.imgur.com/BQZVgjc.jpg)

接著選擇方案，這裡選擇 FREE 方案

![alt tag](http://i.imgur.com/jleHgxw.jpg)

接下來你就會看到 DB 已經被建立了

![alt tag](http://i.imgur.com/aa1kX6o.jpg)

點擊他，就可以跳到下面的畫面

![alt tag](http://i.imgur.com/eGQKDg1.jpg)

接著按 View Credentials

![alt tag](http://i.imgur.com/HuHQUvm.jpg)

可以看到自己 db 的一些資料，包含 帳號、密碼 資訊

![alt tag](http://i.imgur.com/roGcz1i.jpg)

現在我們來建立 DB 的 TABLE

先將 URI 這個很長的連接字串，貼到 [dbModel.py](https://github.com/twtrubiks/Deploying-Flask-To-Heroku/blob/master/dbModel.py) 裡面

```python
app.config[
    'SQLALCHEMY_DATABASE_URI'] = 'postgres://XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
```

請貼自己的連接字串!!!

之後，我們使用 [Flask-Migrate-Tutorial](https://github.com/twtrubiks/Flask-Migrate-Tutorial) 來建立  DB 的 TABLE，

如果不懂，請參考  [Flask-Migrate-Tutorial](https://github.com/twtrubiks/Flask-Migrate-Tutorial) 範例。

P.S 假如你和我一樣是使用 PostgreSQL ， 需要額外安裝套件 [psycopg2](http://initd.org/psycopg/)

```cmd
pip install psycopg2
```

一切處理完畢之後，再進行部屬就完成了。

下圖為簡單的範例  [Demo](https://flask-demo-test.herokuapp.com/index)

commit ID [ce4c8ee68f58c861a5a8072793912b204c186906](https://github.com/twtrubiks/Deploying-Flask-To-Heroku/tree/ce4c8ee68f58c861a5a8072793912b204c186906)

![alt tag](http://i.imgur.com/j1JAKS4.jpg)

database information 就是將 db 的資料全部顯示出來

![alt tag](http://i.imgur.com/a6F14Aw.jpg)

## Heroku 注意事項

因為 heroku 的關係，有些人可能會遇到佈署失敗的問題，可以試著將 [runtime.txt](https://github.com/twtrubiks/Deploying-Flask-To-Heroku/blob/master/runtime.txt)  修改為 3.6.2

## 執行環境

* Windows 10

## Reference

* [Heroku](https://dashboard.heroku.com/)

## Donation

文章都是我自己研究內化後原創，如果有幫助到您，也想鼓勵我的話，歡迎請我喝一杯咖啡:laughing:

![alt tag](https://i.imgur.com/LRct9xa.png)

[贊助者付款](https://payment.opay.tw/Broadcaster/Donate/9E47FDEF85ABE383A0F5FC6A218606F8)

## License

MIT license
