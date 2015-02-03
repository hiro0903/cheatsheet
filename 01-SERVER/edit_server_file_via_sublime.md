RSUB
====

### 設定

1. 開啟sublime, 安裝rsub  
    *  `ctrl` + `shift` + `p`  
    *  install packages  
    * rsub  

2. 開啟putty, 選一個常用的設定  
    * (先另存一個版本, 例如RSUB DEV21)  
    * 選項左邊Category - Connection - SSH - Tunnels  
    * **Source Port**輸入自己sandbox, 例如`1234`  
    * **Destination**輸入`127.0.0.1:52698`  
    * 下方選**remote**  
    * 按下`Add`, 會多一個Forwarded ports, 長相類似`R1234  127.0.0.1:52698`
    * 儲存設定, 連線  

3. 連線到dev server後, 火速從愛可大大那兒抓回來最新版本: 
    * `cp ~/../ichen.tw/bin/rsubl ~/bin/edit`


### 使用

1. 先利用Dictionary或Joseph的command-line tool把要修改的template存到local
2. edit {file}, 例如: `edit profile-ffadult-english`


---

