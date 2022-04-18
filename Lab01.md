#  Lab01-建立雲端上的資料庫

建立雲端資料庫(MSSQL)


# 情境

逢甲科技自2020年成立，從事資訊服務行業，近期顧客委託建立一個股市爬蟲機器人，請協助逢甲科技進行分析、設計與實體的建置。
顧客只有一個要求，就是可以每天可以定時至證交所網站抓取”台積電”股票資料並存入資料庫裡，方便他們做後續視覺化與資料探勘的應用。
資訊團隊評估專案後，決定採用AWS雲端平台建置股市爬蟲機器人。
主管小王請你先嘗試在雲端上建立資料庫。

# 實施架構

![image](https://user-images.githubusercontent.com/103306835/163801264-6e21b6ee-5fd6-4d29-9299-ce325e50b463.png)


# 實施步驟

![image](https://user-images.githubusercontent.com/103306835/163802973-d8e2b636-f525-43f6-92cd-ffab8469f31b.png)

1.點選[RDS]

![image](https://user-images.githubusercontent.com/103306835/163803017-e1549f7c-5797-45a9-b95b-9d983d68f74a.png)

2.點選[Create database]

![image](https://user-images.githubusercontent.com/103306835/163803047-09733678-90da-4267-9647-d5de43f809f9.png)

3.選擇[Standard create]

![image](https://user-images.githubusercontent.com/103306835/163803092-e27c6bfd-f82f-484a-a42d-922539a348a4.png)

4.點選[MariaDB]

![image](https://user-images.githubusercontent.com/103306835/163803434-ecadcb9d-c670-48d4-aa4d-84ad7764bda5.png)

5.點選[Free tier]

![image](https://user-images.githubusercontent.com/103306835/163803458-9381f738-449e-40a4-a33f-8ada024320c9.png)

6.輸入[Master password]

![image](https://user-images.githubusercontent.com/103306835/163803490-85aa8c9e-91ef-4e07-8c36-093c38a77057.png)

7.點選[Create new VPC]與[Create new DB Subnet Group]

![image](https://user-images.githubusercontent.com/103306835/163803552-e2d51cc8-cf81-4ccd-8bd2-fce73b71c926.png)

8.點選[YES]

![image](https://user-images.githubusercontent.com/103306835/163803587-87e11f82-e3e0-4a95-93a0-276f6390bf13.png)

9.選擇[Password authentication]

![image](https://user-images.githubusercontent.com/103306835/163803616-4bb8530c-d9bf-49a0-97e9-d869ce4d88ca.png)

10.點選[Create database]

![image](https://user-images.githubusercontent.com/103306835/163803655-d7b37a11-acde-42d2-b2eb-bf147814c053.png)

11.等待database status為Available

![image](https://user-images.githubusercontent.com/103306835/163805846-ff2a4e5a-22b9-4274-bf4d-b36cc501bba0.png)

12.點選[database-1]

![image](https://user-images.githubusercontent.com/103306835/163805884-d51d092d-bef0-4069-a411-e24d53ed1ef5.png)

13.點選Type為[EC2 Security Group-Inbound]
更改Security group 輸入規則Port，預設RDS只有EC2可以連進來
![image](https://user-images.githubusercontent.com/103306835/163805949-dae8beaa-858c-40a5-bbf2-462373723b19.png)

14.點選輸入規則

![image](https://user-images.githubusercontent.com/103306835/163805981-32c3c012-a487-4851-ac25-be143120fecc.png)


15.複製Endpoint(資料庫連線網址)

![image](https://user-images.githubusercontent.com/103306835/163806013-ea73e308-5de7-49c3-96c7-73f7b0df2138.png)




