在Windows有WAMP可管理server，在Mac上則要用MAMP
下載MAMP之後需要改幾個設定檔
Macintosh HD-->應用程式-->MAMP-->conf-->apache-->httpd.conf

在httpd.conf加上Include /Applications/MAMP/etc/apache2/alias/*.conf
指令(請一層一層建立)
sudo mkdir /Applications/MAMP/etc/apache2/alias
sudo touch /Applications/MAMP/etc/apache2/alias/app.conf

打開app.conf，並加上

Alias /app "/Users/wen/xxx"(Alias /alias-name "/source/of/original/folder")

<Directory "/Users/wen/xxx">
    Options Indexes FollowSymLinks MultiViews
    AllowOverride all
    Order allow,deny
    Allow from all
</Directory>

另外，如果想要在同一台主機能夠有一個以上的獨立網站，可以利用Virtual Host的設定
同樣在httpd.conf裏面把"#"拿掉
Include /Applications/MAMP/conf/apache/extra/httpd-vhosts.conf
之後到httpd-vhosts.conf所在位置，就可做編輯