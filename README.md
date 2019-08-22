# LinuxUbuntuJupyter


安裝目的:完成jupyter note book於GCP Linux Ubuntu的安裝，與架站並從本地端連接

jupyter介紹:可寫Python、Markdown等多功能，以及將所有服務架設置雲端的功能


步驟: 資料來源-https://blog.csdn.net/jenyzhang/article/details/73275232

首先要先更新-

sudo apt-get update

sudo apt-get update

之後安裝pip

sudo apt-get install python-pip

升級一下pip

sudo pip install --upgrade pip

安装Jupyter

sudo pip install jupyter

安裝完後就可以利用以下命令執行jupyter

jupyter notebook

但是!利用以上方式執行只能給"本地端使用"，它所產生的Token都只能給本地端用，無法給遠端使用，

因此我們要另外假設密碼!

參考來源-https://blog.csdn.net/miss_snow_m/article/details/53093465

首先要產生sha1

sha1產生方式:
from notebook.auth import passwd 

passwd()

以上兩個指令直接在Python就可以跑!!其實PHP也有類似的功能，將密碼例如123，轉換成SHA1

再來是要產生一個默認檔案-jupyter notebook --generate-config

直接打在指令即可執行，他會再~/.jupyter/產生

註:~/前面波浪就是指root的資料夾

之後去修改jupyter_notebook_config.py檔案!去修改一下，並把前面井字號拿掉

c.NotebookApp.ip='*'

c.NotebookApp.password = u'...' # 輸入產生的sha1，ex:sha1:21b39ab9102b:fc8d26b44d62f35dbbcde4af779f09715e911383  包含sha1

c.NotebookApp.open_browser = False

c.NotebookApp.port = 8888 #改成這個port，然後請務必記得!!GCP防火牆一定要記得調整，並將範圍設定成"適用全部執行個體"

最後再jupyter notebook執行

打上虛擬機網址-

http://34.74.163.147:8888/tree   然後輸入之前打進sha1的密碼，即大功告成


