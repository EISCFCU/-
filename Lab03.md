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


# 步驟2：建立第一個Lambda

用途：抓證交所網頁資料並存入S3

1.點選[Create Lambda]

![image](https://user-images.githubusercontent.com/103306835/166085927-3cb7469d-6840-4094-8fb7-3cc2ea760bf8.png)

2.輸入Function name(名稱自訂)

![image](https://user-images.githubusercontent.com/103306835/166085938-bb9ef4e5-ad17-4ff0-ac8f-af8c42518af8.png)

3.點選[Use an existing role]

![image](https://user-images.githubusercontent.com/103306835/166085946-1aac2014-6dc3-4ba5-b512-72f7722522a2.png)

4.點選[Create function]

![image](https://user-images.githubusercontent.com/103306835/166085952-c4b3e795-6088-4115-b5e9-dd210e4c149d.png)

5.點選[Upload from]

![image](https://user-images.githubusercontent.com/103306835/166086001-c128a89a-d223-4252-bffd-95daa5dae595.png)

6.點選[Upload]

![image](https://user-images.githubusercontent.com/103306835/166085993-74a981b5-c6cc-4802-94ed-184f706de2e4.png)

7.點選[Save]

![image](https://user-images.githubusercontent.com/103306835/166086009-5ca951d9-9d2c-439d-96a8-539c8d7770c7.png)

8.點選[Configuration]

![image](https://user-images.githubusercontent.com/103306835/166086018-5aa9587a-b13f-4003-a514-870c3399aee2.png)

9.點選[Edit]

![image](https://user-images.githubusercontent.com/103306835/166086033-b38f88f3-600b-4c9c-9e7e-c1f9d44702f4.png)

10.輸入描述

![image](https://user-images.githubusercontent.com/103306835/166086066-4d8709ce-2a9f-4356-8a72-cacb0e82d0a5.png)

11.更改Timeout為1分鐘

![image](https://user-images.githubusercontent.com/103306835/166086071-fd54ce6b-2c52-49a7-9e8c-09f53c3a2c51.png)

12.點選[Save]

![image](https://user-images.githubusercontent.com/103306835/166086091-9888175d-19be-46a6-98a6-cd93e514aa08.png)

13.點選[Code]

![image](https://user-images.githubusercontent.com/103306835/166086101-075d9fed-46c3-4d3f-a0ce-b8996e6808cd.png)

14.更換S3 Bucketname

![image](https://user-images.githubusercontent.com/103306835/166086116-9fccb38d-b584-4d8f-b182-acfda48f9e2f.png)

15.點選[Deploy]

![image](https://user-images.githubusercontent.com/103306835/166086129-dc4b6e39-8f87-48cf-97c7-474e10204191.png)

16.點選[Test]

![image](https://user-images.githubusercontent.com/103306835/166086139-28bee0ae-865c-44d0-89fb-7b1d3cdc77a6.png)

17.新增測試事件與名稱

![image](https://user-images.githubusercontent.com/103306835/166086143-13f7f3ca-c2c3-44e4-b605-575f86337ead.png)

18.點選[Create]

![image](https://user-images.githubusercontent.com/103306835/166086156-55990a01-59e9-4fd0-89fd-3605c1f3bf37.png)

完成Lambda的程式部署


# 步驟3：Lambda測試

1.點選[Test]

![image](https://user-images.githubusercontent.com/103306835/166086196-6ca67490-f250-478a-ad75-134a052525c4.png)

2.成功抓取股票資料 並存放在S3

![image](https://user-images.githubusercontent.com/103306835/166086240-265c66ef-10ad-47ba-babb-7891141db7f3.png)

# 步驟4：查看S3是否已有股票資料

1.點選[S3] 點選步驟1新增的S3
![image](https://user-images.githubusercontent.com/103306835/166086258-764eba9d-31a0-4f42-8b8b-e456cc99eec3.png)

2.已經新增的股票資料

![image](https://user-images.githubusercontent.com/103306835/166086268-82a09c37-906d-40ae-be8a-06cc4a017b7f.png)

