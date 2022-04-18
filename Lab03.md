# 自動化股市爬蟲

# 情境

逢甲科技自2020年成立，從事資訊服務行業，近期顧客委託建立一個股市爬蟲機器人，請協助逢甲科技進行分析、設計與實體的建置。
顧客只有一個要求，就是可以每天可以定時至證交所網站抓取”台積電”股票資料並存入資料庫裡，方便他們做後續視覺化與資料探勘的應用。


範例：109年03月 2330 台積電 各日成交資訊
![image](https://user-images.githubusercontent.com/103306835/163771493-315812ab-20b2-44ad-990e-1b717120ab0e.png)


# 實施架構

![image](https://user-images.githubusercontent.com/103306835/163771871-e8de0142-a42a-4c9b-bff4-4b8b64138023.png)

# 實施步驟

![image](https://user-images.githubusercontent.com/103306835/163771846-b8c15e04-76bd-497b-9960-cafeae8400c9.png)

登入AWS Management Console
![image](https://user-images.githubusercontent.com/103306835/163772880-3b1afe3d-b8e8-4e30-993e-8b4a741a50dc.png)


# 步驟1：建立S3 Bucket
用途：存放股票資料網頁用

1.點選[Create bucket]
![image](https://user-images.githubusercontent.com/103306835/163773393-86b7b2db-53e3-4c27-9d54-af72cfeb2f48.png)

2.輸入Bucket name(為唯一值；只能輸入英文跟數字)
![image](https://user-images.githubusercontent.com/103306835/163773430-2ad99458-84b3-4315-9ddd-fa89d017987a.png)

3.取消勾選[Block all public access]
![image](https://user-images.githubusercontent.com/103306835/163773652-23395212-4bf7-48c5-858b-c72a87c7c238.png)

4.勾選[I acknowledge that….]
![image](https://user-images.githubusercontent.com/103306835/163773683-a42209d6-c090-4ad8-b39e-9cca568b7740.png)

5.點選[Create bucket]
![image](https://user-images.githubusercontent.com/103306835/163773724-fedb26cb-29ad-43ba-ba2a-561c0c56a00c.png)

6.完成bucket的新增
![image](https://user-images.githubusercontent.com/103306835/163773776-8d4045c0-1710-4dcc-950c-c66c0e4301d3.png)
