# 股市爬蟲

# 情境

逢甲科技自2020年成立，從事資訊服務行業，近期顧客委託建立一個股市爬蟲機器人，請協助逢甲科技進行分析、設計與實體的建置。
顧客只有一個要求，就是可以每天可以定時至證交所網站抓取”台積電”股票資料並存入資料庫裡，方便他們做後續視覺化與資料探勘的應用。


範例：109年03月 2330 台積電 各日成交資訊
![image](https://user-images.githubusercontent.com/103306835/163771493-315812ab-20b2-44ad-990e-1b717120ab0e.png)


# 實施架構

![image](https://user-images.githubusercontent.com/103306835/163771871-e8de0142-a42a-4c9b-bff4-4b8b64138023.png)

# 實施步驟

![image](https://user-images.githubusercontent.com/103306835/166086659-f3d7e19e-fbb6-4c42-be26-9d155be0fec4.png)

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


# 步驟5：建立第二個Lambda

1.點選[Create Function]

![image](https://user-images.githubusercontent.com/103306835/167234671-ad021e9f-38fc-408f-95c4-4f5f9d03dc31.png)


2.輸入Function name

輸入Function name![image](https://user-images.githubusercontent.com/103306835/167234682-fe18449c-28e0-4197-bafc-9cf39dbd1771.png)

3.選擇Runtime

![image](https://user-images.githubusercontent.com/103306835/167234692-10500e7d-8a59-47b7-a3b7-f7ba45d8d943.png)

4.選擇既有的角色(Lab Role)

![image](https://user-images.githubusercontent.com/103306835/167234705-dd99886f-d5b1-48f2-9a5f-f9b28327dc83.png)

5.點選[+Add trigger]

![image](https://user-images.githubusercontent.com/103306835/167234717-7e50da2f-8b43-4039-953f-b8c61e03e869.png)

6.選擇[S3]

![image](https://user-images.githubusercontent.com/103306835/167234727-394f2727-c0e7-4877-88ac-6b644e502bab.png)

7.選擇步驟1新建的S3

![image](https://user-images.githubusercontent.com/103306835/167234738-2aaa87e8-b8cd-40c7-82ff-6e965a9923d9.png)

8.點選[Add]

![image](https://user-images.githubusercontent.com/103306835/167234744-919860e6-0534-4f48-bce0-270d243f6ebf.png)

9.完成Trigger設定

![image](https://user-images.githubusercontent.com/103306835/167234751-fc26fb78-9af9-4f78-a9d0-a60dde050a3a.png)

# 步驟7：新增Dynamodb

1.回到第二個Lambda Code source

![image](https://user-images.githubusercontent.com/103306835/167237065-9515cac6-cea9-4ccf-b5d6-ee3389553a8f.png)

2.點選[Upload from]

![image](https://user-images.githubusercontent.com/103306835/167237076-7ae7909f-b891-4304-9f70-107f51834119.png)

3.點選[Upload] 選取Lambda2.zip

![image](https://user-images.githubusercontent.com/103306835/167237090-48623757-c6f4-4bd0-ae65-908ddaa9c5d4.png)

4.點選[Save]

![image](https://user-images.githubusercontent.com/103306835/167237101-f437abd7-a731-452a-913e-46bdf50fd8d6.png)

5.完成上傳

![image](https://user-images.githubusercontent.com/103306835/167237110-e0091736-7528-4098-b342-387113616690.png)

6.打開lambda_function.py

![image](https://user-images.githubusercontent.com/103306835/167237116-1e963ffc-611d-4763-a627-bbeac17d4fa0.png)

7.更改Table name與Region

![image](https://user-images.githubusercontent.com/103306835/167237121-b1818418-2ee9-493a-bc0a-60348438ac81.png)

8.複製主控台測試語法

![image](https://user-images.githubusercontent.com/103306835/167237134-752c6c99-87f1-4264-9a19-cd1fe3c93048.png)

9.點選[Test]

![image](https://user-images.githubusercontent.com/103306835/167237149-a63bfc9b-6adb-46da-ab17-be9cce8832ec.png)

10.輸入Event name

![image](https://user-images.githubusercontent.com/103306835/167237160-b1797922-2342-453c-8ddb-43946058db17.png)

11.貼上測試語法

'''
{
  "Records": [
    {
      "eventVersion": "2.0",
      "eventSource": "aws:s3",
      "awsRegion": "us-east-1",
      "eventTime": "1970-01-01T00:00:00.000Z",
      "eventName": "ObjectCreated:Put",
      "userIdentity": {
        "principalId": "EXAMPLE"
      },
      "requestParameters": {
        "sourceIPAddress": "127.0.0.1"
      },
      "responseElements": {
        "x-amz-request-id": "EXAMPLE123456789",
        "x-amz-id-2": "EXAMPLE123/5678abcdefghijklambdaisawesome/mnopqrstuvwxyzABCDEFGH"
      },
      "s3": {
        "s3SchemaVersion": "1.0",
        "configurationId": "testConfigRule",
        "bucket": {
          "name": "my-s3-bucket",
          "ownerIdentity": {
            "principalId": "EXAMPLE"
          },
          "arn": "arn:aws:s3:::example-bucket"
        },
        "object": {
          "key": "HappyFace.jpg",
          "size": 1024,
          "eTag": "0123456789abcdef0123456789abcdef",
          "sequencer": "0A1B2C3D4E5F678901"
        }
      }
    }
  ]
}

'''
![image](https://user-images.githubusercontent.com/103306835/167237168-7cba1a16-1436-476b-b8cc-a792fbcc9c85.png)


12.更改S3 bucketname 跟key

![image](https://user-images.githubusercontent.com/103306835/167237179-4e63d2e3-5418-4e8c-b852-283bc8c6d5b0.png)

13.回到S3查看Bucketname

![image](https://user-images.githubusercontent.com/103306835/167237186-3dca2022-5dc1-44d9-900a-8dc97d13c41d.png)

14.以及object的名稱 進行複製

![image](https://user-images.githubusercontent.com/103306835/167240544-fa468c23-8b2b-42aa-b4c7-079ed95c1661.png)

15.進行S3 Bucketname 與 Key的更換

![image](https://user-images.githubusercontent.com/103306835/167240556-f0e0e76b-3ddf-4d03-a0fc-9801d69d5f9b.png)

16.點選[Create]

![image](https://user-images.githubusercontent.com/103306835/167240568-5fe04d7c-bf7e-452e-a8ab-c187d2a2f7f7.png)

17.剛更新的語法沒有部署 點選[Deploy]

![image](https://user-images.githubusercontent.com/103306835/167240601-2eefe9b8-cd3b-400b-9a80-dcbb7c2357d2.png)

18.完成部署

![image](https://user-images.githubusercontent.com/103306835/167240611-505be458-a4bb-4329-a4a0-634f5dc804fe.png)

19.點擊[Test]

![image](https://user-images.githubusercontent.com/103306835/167240676-3bcac4eb-1f3c-4965-a7cf-dac74637d6e3.png)

20.測試結果呈現

![image](https://user-images.githubusercontent.com/103306835/167240696-fe161034-c58c-45bf-bce4-f022b3d40411.png)

# 步驟8：查看DynamoDB是否產生資料

1.進入Dyamodb主頁

![image](https://user-images.githubusercontent.com/103306835/167240729-3831c177-21a9-456b-8447-2c35c5a084eb.png)

2.點選[Tables]

![image](https://user-images.githubusercontent.com/103306835/167240741-8f9841c2-c7e2-4547-aac4-28189225cc8a.png)

3.點選步驟7新增的資料表

![image](https://user-images.githubusercontent.com/103306835/167240754-18f2bd53-99da-44f4-8e3a-ec33b62a26ea.png)

4.點選[Item]

![image](https://user-images.githubusercontent.com/103306835/167240769-6e7fed20-0e41-4454-ae96-328f3c904ac4.png)

5.結果呈現

![image](https://user-images.githubusercontent.com/103306835/167240774-fa3d892b-f134-4662-83da-91b3dcff2224.png)

# 步驟9：正式進行爬蟲、解析資料並存到DynamoDB

1.清除資料表


2.設定串流

![image](https://user-images.githubusercontent.com/103306835/167240822-00bd2b45-a56a-43c2-8320-9ad38be68f25.png)

3.開通串流

![image](https://user-images.githubusercontent.com/103306835/167240825-a057eef5-3bc7-4448-8c91-78c9020d72af.png)

4.完成資料表新增

![image](https://user-images.githubusercontent.com/103306835/167240832-0bec5c8d-efa7-43ee-8f54-714a762fdcc7.png)

5.回到第一個lambda


6.點選[Test]



7.點擊更新鍵


8.

