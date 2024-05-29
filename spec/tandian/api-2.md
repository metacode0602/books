1、用户信息

```
https://tdnewapp.qudao51.cn/rest/td/system/user/info
```

```json
 {
  "code": "200",
  "msg": "成功",
  "data": {
    "virtualVisit": null,
    "realVisit": null,
    "identityTypeName": "未认证",
    "memberTimeBegin": null,
    "orderReadNum": 0,
    "pageStatus": 1,
    "showIdentityTypeName": "未认证",
    "identityType": 0,
    "pckInfos": null,
    "invitedCode": "9DL9EV",
    "storeName": "",
    "id": 114957,
    "memberTimeEnd": null,
    "showIdentityType": 0,
    "avatarUrl": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1716216796324.jpg",
    "taskReadNum": 0,
    "workOrderReadNum": 0,
    "nickName": "用户8927890058",
    "mobile": "13681332236",
    "wechat": "",
    "earliestRegisterTime": "2024-05-20 22:53:20",
    "agentUserId": null,
    "publishType": null,
    "name": "",
    "idCardNum": "",
    "memberType": null,
    "memberIdentity": null
  }
}
```

2、个人账户

```
https://tdnewapp.qudao51.cn/rest/td/system/message/read/count/v2
```

```json
{
  "code": "200",
  "msg": "成功",
  "data": {
    "orderReadNum": 0,
    "unSignContractNum": 0,
    "taskReadNum": 0,
    "workOrderReadNum": 0,
    "messageNum": 0
  }
}
```

3、收入统计

```
https://tdnewapp.qudao51.cn/rest/td/platform/balance/statisticsIncome
```

```json
{
  "code": "200",
  "msg": "成功",
  "data": {
    "countingBalance": 0.0,
    "todayEarnings": 0.0,
    "todayNum": 0,
    "expectedEarnings": 0
  }
}
```

4、我的订单

```
https://tdnewapp.qudao51.cn/rest/td/mall/workOrder/list?getLastOne=true
```

```json
{
  "code": "200",
  "msg": "成功",
  "data": {
    "current": 1,
    "total": 0,
    "pages": 0,
    "size": 1,
    "records": [],
    "searchCount": true
  }
}
```

5、我的任务

```
https://tdnewapp.qudao51.cn/rest/td/platform/task/listMyTask?page=1&taskModel=
```

达人推 `taskModel = 2` 实地探店 `taskModel = 1`

```json
{
  "code": "200",
  "msg": "成功",
  "data": {
    "current": 1,
    "total": 0,
    "pages": 0,
    "size": 15,
    "records": [],
    "searchCount": true
  }
}
```

6、我的钱包

```
https://tdnewapp.qudao51.cn/rest/td/platform/balance/info
```

```json
{
  "code": "200",
  "msg": "成功",
  "data": {
    "minWithdrawAmount": null,
    "accountPhone": "13681332236",
    "countingBalance": 0.0,
    "countingFrozenBalance": 0.0,
    "withdrawalRate": {
      "rateStatus": 0,
      "rate": 6
    },
    "id": 113223,
    "userId": 114957,
    "account": "oCH604gtqW-vR0hANB6ee8aWl5mA",
    "gaodengName": ""
  }
}
```

7、金额纪录

```
https://tdnewapp.qudao51.cn/rest/td/platform/balance/transaction/list?page=1&pageSize=30
```

```json
{
  "code": "200",
  "msg": "成功",
  "data": {
    "current": 1,
    "total": 0,
    "pages": 0,
    "size": 30,
    "records": [],
    "searchCount": true
  }
}
```

8、商家会员 -- 分类

```
https://tdnewapp.qudao51.cn/rest/td/mall/goods/common/listSellerCategory?showType=1
```

```json
{
  "code": "200",
  "msg": "成功",
  "data": [
    {
      "sellIdentityType": "2",
      "iconStatus": 1,
      "categoryImage": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1666677302337.jpeg",
      "createTime": "2022-10-25 13:55:13",
      "showType": 1,
      "pid": 0,
      "remark": "单店团购",
      "showStatus": 1,
      "updateTime": "2024-05-02 19:08:46",
      "id": 6,
      "sort": 0,
      "categoryName": "新店开业套餐"
    },
    {
      "sellIdentityType": "2",
      "iconStatus": 1,
      "categoryImage": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1683187614102.png",
      "createTime": "2023-05-04 16:06:59",
      "showType": 1,
      "pid": 0,
      "remark": "商家会员",
      "showStatus": 1,
      "updateTime": "2024-05-02 19:08:51",
      "id": 9,
      "sort": 1,
      "categoryName": "新品发布套餐"
    },
    {
      "sellIdentityType": "2",
      "iconStatus": 1,
      "categoryImage": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1685073832487.png",
      "createTime": "2023-05-26 12:03:53",
      "showType": 1,
      "pid": 0,
      "remark": "商家自选流量包",
      "showStatus": 1,
      "updateTime": "2024-05-02 19:08:59",
      "id": 11,
      "sort": 3,
      "categoryName": "活动促销套餐"
    },
    {
      "sellIdentityType": "2",
      "iconStatus": 0,
      "categoryImage": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1671514503365.png",
      "createTime": "2022-10-25 16:52:22",
      "showType": 1,
      "pid": 0,
      "remark": "连锁总部",
      "showStatus": 1,
      "updateTime": "2024-05-02 19:09:22",
      "id": 7,
      "sort": 5,
      "categoryName": "连锁品牌长效运营套餐"
    },
    {
      "sellIdentityType": "2",
      "iconStatus": 0,
      "categoryImage": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1700301445211.png",
      "createTime": "2023-11-18 17:57:26",
      "showType": 1,
      "pid": 0,
      "remark": "699会员",
      "showStatus": 1,
      "updateTime": "2024-05-03 09:20:31",
      "id": 13,
      "sort": 5,
      "categoryName": "商家会员"
    },
    {
      "sellIdentityType": "2",
      "iconStatus": 0,
      "categoryImage": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1654505139169.jpg",
      "createTime": "2022-06-06 16:45:47",
      "showType": 1,
      "pid": 0,
      "remark": "服务套餐",
      "showStatus": 1,
      "updateTime": "2024-05-02 19:09:32",
      "id": 4,
      "sort": 6,
      "categoryName": "团购基建服务包"
    }
  ]
}
```

9、商家会员 -分类产品

```
https://tdnewapp.qudao51.cn/rest/td/mall/goods/common/listGoods?categoryId=6&page=1&pageSize=20
```

```json
{
  "code": "200",
  "msg": "成功",
  "data": {
    "current": 1,
    "total": 2,
    "pages": 1,
    "size": 20,
    "records": [
      {
        "commentLabel": null,
        "platformType": null,
        "geekMentorDiscount": null,
        "type": 1,
        "caseType": null,
        "customerServiceInfo": null,
        "geekDiscount": null,
        "cover": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1709201396692.jpg",
        "contractTId": null,
        "mallUserInfo": null,
        "commission": null,
        "id": 54,
        "goodsName": "新店开业团购达人包【100条】",
        "staging": 0,
        "sold": 3433,
        "goodsDetailStyle": 1,
        "goodsDetails": "<img src=\"https://qdwy-ice.oss-cn-shanghai.aliyuncs.com/pro/imgs/tandian-anno/1713409077813.jpg\" alt=\"\" /><br />",
        "serviceQrCodeIdGoods": 3,
        "soldBase": 1987,
        "templates": null,
        "specification": {
          "lowestPrice": 3980.0,
          "originalPrice": 3980.0,
          "promotionPrice": null,
          "goodsId": 54,
          "discount": 10.0,
          "memberName": null,
          "stockQuantity": 1553,
          "tailPayment": null,
          "promotionStatus": false,
          "sellingPrice": 3980.0,
          "contractImage": null,
          "attribute": "[{\"value\":\"达人包100\",\"key\":\"达人包100\"}]",
          "id": 69,
          "headPayment": null,
          "staging": 0,
          "sold": 1446,
          "goodsLimit": 0,
          "memberPrice": null,
          "promotionStartTime": null,
          "headPrice": null,
          "attributeArray": [
            {
              "value": "达人包100",
              "key": "达人包100"
            }
          ],
          "giftDay": null,
          "promotionHeadPayment": null,
          "tailPrice": null,
          "minimumSellingQuantity": null,
          "giftMember": null,
          "previewImage": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1709258933755.jpg",
          "promotionEndTime": null,
          "promotionTailPayment": null,
          "cid": "0",
          "promotion": 0,
          "status": 1
        },
        "updateTime": "2024-04-29 18:44:34",
        "agentDiscount": null,
        "sort": 2,
        "contractTTemplateId": "3165511763852570743",
        "giftDay": null,
        "otherFeeTemplatesId": 1,
        "commentInfo": null,
        "goodsStatus": 1,
        "createTime": "2023-11-18 17:34:50",
        "documentList": null,
        "giftWorkNum": null,
        "sellerDiscount": null,
        "favoritesStatus": null,
        "qRCode": null,
        "giftMember": null,
        "goodsCode": "M00001",
        "serviceQrCodeIdOrder": 4,
        "categoryId": 6,
        "taskId": null
      },
      {
        "commentLabel": null,
        "platformType": null,
        "geekMentorDiscount": null,
        "type": 1,
        "caseType": null,
        "customerServiceInfo": null,
        "geekDiscount": null,
        "cover": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1709201427368.jpg",
        "contractTId": null,
        "mallUserInfo": null,
        "commission": null,
        "id": 55,
        "goodsName": "新店开业团购达人包【200条】",
        "staging": 0,
        "sold": 434,
        "goodsDetailStyle": 1,
        "goodsDetails": "<img src=\"https://qdwy-ice.oss-cn-shanghai.aliyuncs.com/pro/imgs/tandian-anno/1713409101498.jpg\" alt=\"\" /><br />",
        "serviceQrCodeIdGoods": 3,
        "soldBase": 397,
        "templates": null,
        "specification": {
          "lowestPrice": 6980.0,
          "originalPrice": 6980.0,
          "promotionPrice": null,
          "goodsId": 55,
          "discount": 10.0,
          "memberName": null,
          "stockQuantity": 962,
          "tailPayment": null,
          "promotionStatus": false,
          "sellingPrice": 6980.0,
          "contractImage": null,
          "attribute": "[{\"value\":\"达人包200\",\"key\":\"达人包200\"}]",
          "id": 70,
          "headPayment": null,
          "staging": 0,
          "sold": 37,
          "goodsLimit": 0,
          "memberPrice": null,
          "promotionStartTime": null,
          "headPrice": null,
          "attributeArray": [
            {
              "value": "达人包200",
              "key": "达人包200"
            }
          ],
          "giftDay": null,
          "promotionHeadPayment": null,
          "tailPrice": null,
          "minimumSellingQuantity": null,
          "giftMember": null,
          "previewImage": "https://qudaowuyou.oss-cn-shenzhen.aliyuncs.com/pro/imgs/tandian-anno/1709259099849.jpg",
          "promotionEndTime": null,
          "promotionTailPayment": null,
          "cid": "0",
          "promotion": 0,
          "status": 1
        },
        "updateTime": "2024-04-30 15:52:05",
        "agentDiscount": null,
        "sort": 4,
        "contractTTemplateId": "3165511763852570743",
        "giftDay": null,
        "otherFeeTemplatesId": 1,
        "commentInfo": null,
        "goodsStatus": 1,
        "createTime": "2023-11-18 17:37:52",
        "documentList": null,
        "giftWorkNum": null,
        "sellerDiscount": null,
        "favoritesStatus": null,
        "qRCode": null,
        "giftMember": null,
        "goodsCode": "M00002",
        "serviceQrCodeIdOrder": 4,
        "categoryId": 6,
        "taskId": null
      }
    ],
    "searchCount": true
  }
}
```
