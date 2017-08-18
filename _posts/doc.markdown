---
layout: post
title:  "Welcome to Jekyll!"
date:   2017-08-18 15:31:00
categories: alps
---

# postman使用

## js代码

```js
var randomInt = (min, max) => parseInt(Math.random() * (max - min + 1) + min, 10); // 随机整数

// 生成随机身份证
var getId_no = () => {
    let coefficientArray = ["7", "9", "10", "5", "8", "4", "2", "1", "6", "3", "7", "9", "10", "5", "8", "4", "2"];
    let lastNumberArray = ["1", "0", "X", "9", "8", "7", "6", "5", "4", "3", "2"];
    let address = "420101";
    let birthday = randomInt(1980,2000)+"0101";
    let s = randomInt(100, 999)+"";
    let array = (address + birthday + s).split("");
    let total = 0;
    for (let i in array) {
        total = total + parseInt(array[i]) * parseInt(coefficientArray[i]);
    }
    let lastNumber = lastNumberArray[parseInt(total % 11)];
    return address + birthday + s + lastNumber;
};

// 生成随机姓名
var getName = () => {
    let familyNames = new Array("赵", "钱", "孙", "李", "周", "吴", "郑", "王", "冯", "陈", "褚", "卫", "蒋", "沈", "韩", "杨", "朱", "秦", "尤", "许", "何", "吕", "施", "张", "孔", "曹", "严", "华", "金", "魏", "陶", "姜", "戚", "谢", "邹", "喻", "柏", "水", "窦", "章", "云", "苏", "潘", "葛", "奚", "范", "彭", "郎", "鲁", "韦", "昌", "马", "苗", "凤", "花", "方", "俞", "任", "袁", "柳", "酆", "鲍", "史", "唐", "费", "廉", "岑", "薛", "雷", "贺", "倪", "汤", "滕", "殷", "罗", "毕", "郝", "邬", "安", "常", "乐", "于", "时", "傅", "皮", "卞", "齐", "康", "伍", "余", "元", "卜", "顾", "孟", "平", "黄", "和", "穆", "萧", "尹");

    let middleNames = new Array("子","佳","紫","瑞","昕","明","水","泽","观","佳","佳","晨","钟","运","汝","淑","晶","润","榕","佳","佳","晓","一","语","添","添","雨","雅","雅","清","诗","嘉","晨","天","玥","佳","夏","萌","若","文","暄","顺","思","舞","夜","逸","灵","尔","曼","彦","幻","寒","雁","寻","安","书","施","盼","秦","欣","立","真");

    let lastNames = new Array("嘉","璇","淼","栋","子","堂","甜","敏","尚","贤","祥","涛","轩","辰","帆","冉","春","昆","齐","杨","昊","东","霖","晨","涵","溶","枫","丙","豪","慧","政","闵","元","顾","杰","源","林","润","汝","城","建","花","菲","画","洁","合","光","祝","美","观","洋","越","丽","翔","华","钗","晶","溪","罗","怡","毅","思","琪","钟","霞","蕊","栾","呈","宜","远","屏","怡","惠","茜","璐","园","鑫","君","滢","莎","汕","钰","玉","庆","鸣","里","池","昊","泽","晗","落","妍","悦","乐","苗","赫","傲","瓜","东","萌","臻","华","莹","慈","松","月","卉","致","洪","伽","音","醒","梅","天","菡","巧","国","琴","诗","晴","青","彤","果","冰");

    let f = randomInt(0, familyNames.length-1);
    let familyName = familyNames[f];

    let m = randomInt(0, middleNames.length-1);
    let middleName = middleNames[m];

    let  last = randomInt(0, lastNames.length-1);
    let lastName = lastNames[last];

    return familyName + middleName + lastName;
};

// 生成随机银行卡号
var getBank_account=(bank_no)=>{let prefix="";switch(bank_no){case"0102":prefix="622202";break;case"0103":prefix="622848";break;case"0105":prefix="622700";break;case"0301":prefix="622262";break;case"104":prefix="621661";break;case"0303":prefix="622666";break;case"305":prefix="622622";break;case"0306":prefix="622556";break;case"0308":prefix="622588";break;case"0410":prefix="622155";break;case"302":prefix="622689";break;case"304":prefix="622630";break;case"309":prefix="622908";break;case"310":prefix="621717";break;case"315":prefix="622323";break;case"316":prefix="622309";break;default:prefix="622556"}for(var j=0;j<13;j++){prefix=prefix+Math.floor(Math.random()*10)}return prefix+1111};

// 计数累加器
let counter = parseInt(postman.getEnvironmentVariable("test-counter"));
// 生成随机客户名称
const custName =  getName();
// 生成随机身份证号码
const idNo = getId_no();
// 自定义身份证号码
// const idNo = "11010119870101061X";

// 生成随机手机号码
const mobile = `17${randomInt(100000000,999999999)}`;
// 身份证到期日期
const idValidityEnd = postman.getEnvironmentVariable("idValidityEnd");
//出生日期
const birthday = postman.getEnvironmentVariable("birthday");
// 地址1
const addr1 = postman.getEnvironmentVariable("addr1");
// 地址
const addr = postman.getEnvironmentVariable("addr");
// 联行号
const bankRegionCode = postman.getEnvironmentVariable("bankRegionCode");
// 银行支行
const bankRegionName = postman.getEnvironmentVariable("bankRegionName");
// 银行编码
const bankCode = postman.getEnvironmentVariable("bankCode");
// 银行卡号
const bankAcct = getBank_account(bankCode);
// 支行号码
const currency = postman.getEnvironmentVariable("currency");
// 申请日期
const appDt = postman.getEnvironmentVariable("appDt");
// 申请时间
const appTm = postman.getEnvironmentVariable("appTm");


// 清除环境变量值
postman.clearEnvironmentVariable("custName");
postman.clearEnvironmentVariable("idNo");
postman.clearEnvironmentVariable("mobile");
postman.clearEnvironmentVariable("bankAcct");

// 重新设置环境变量值
postman.setEnvironmentVariable("custName", custName);
postman.setEnvironmentVariable("idNo", idNo);
postman.setEnvironmentVariable("mobile", mobile);
postman.setEnvironmentVariable("bankAcct", bankAcct);
postman.setEnvironmentVariable("addr", addr1+(++counter));
postman.setEnvironmentVariable("test-counter", counter);



var nameInfo = {
    "姓名": custName, "身份证": idNo, "手机号码": mobile, "银行卡": bankAcct
};

postman.setGlobalVariable("nameInfo", JSON.stringify(nameInfo));

console.log("姓名："+custName+"\n身份证："+idNo+"\n手机号码："+mobile+"\n 银行卡："+bankAcct);
```
