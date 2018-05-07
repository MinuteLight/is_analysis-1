# 实验5：图书管理系统数据库设计与界面设计
## 1.数据库表设计
![](images/数据库总表.png)
### 1.1. 图书表
![](images/t_book.png)
![](images/t_book信息.png)

### 1.2. 读者表
![](images/t_reader.png)

### 1.3. 管理员表
![](images/t_admin.png)

### 1.4. 借阅归还表
![](images/t_lend.png)

### 1.5. 读者类别表
![](images/t_readerType.png)

### 1.6. 图书类别表
![](images/t_bookType.png)
## 2. 界面设计

### 2.1. 首页设计
![](images/首页.png)

- API接口如下：

1. 图书查询API
![](images/所有图书.png)
- 功能：用于获取所有图书信息
- 请求地址： http://localhost:8080/bookManagerV4.0/page/book/findBook.html?all
- 请求方法：POST
- 请求参数：pageNow: 1,pageSize: 10

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|pageNow|是|当前页|
|pageSize|是|每页的数量|

- 返回实例：
```
{
    code:0
    count:44
    "data": 
    [
      0:{
          author:"罗廷方1"
          bookName:"Java"
          bookNo:"0881"
          introduction:"《你是人间四月天》收录了林徽因几乎所有的诗歌、散文、小说。"
          lastTime:{date: 6, day: 3, hours: 10, minutes: 17, month: 11, nanos: 0, seconds: 53, time: 1512526673000,…}
          num:84
          photo:[-1, -40, -1, -32, 0, 16, 74, 70, 73, 70, 0, 1, 1, 1, 0, 72, 0, 72, 0, 0, -1, -37, 0, 67, 0, 9, 6, 7,…]
          price:595
          publish:"成都大学出版社"
          publishDate:{date: 4, day: 1, hours: 20, minutes: 52, month: 11, nanos: 0, seconds: 15, time: 1512391935000,…}
          snum:80
          },
       1:{...},
       2:{...},
    ]
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|count|查询数的总数|
|data|书籍的详细信息|

2.编辑图书API
![](images/编辑.png)
- 功能：修改图书的信息
- 请求地址： http://localhost:8080/bookManagerV4.0/page/book/updateBook.html?book.bookNo=123
- 请求方法：POST
- 请求参数：
```
      bookNo: 123
      book.bookNo: 123
      book.bookName: JavaEE
      book.bookType.id: 23
      book.price: 14
      book.snum: 81
      book.num: 16
      book.author: 罗廷方2
      book.publishDate: 2017-12-17 16:03:51
      book.publish: 成都大学出版社
      book.introduction: 《你是人间四月天》收录了林徽因几乎所有的诗歌、散文、小说。

```
- 返回实例：
```
{
   "1"
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|1|成功|


### 2.2. 个人信息页面设计
![pic1](images/个人信息界面.png)
- 用例图参见：个人信息用例
- 类图参见：读者类
- 顺序图参见：读者顺序图
- API接口如下：

1. 个人信息API

- 功能：用于获取读者的个人信息
- 请求地址： http://localhost:8080/BookManagementSystem/showReaderInfo
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|borrow_id|是|读者编号|

- 返回实例：
```
{
    "status_code": "1/0",
    "data": 
    [
        {
            "account","meien",
            "password","123",
            "nickname","梅恩",
            "student_id","201510414413",
            "head_img","http://www.meien.xyz/meien.jpg"
        },
    ]
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|status_code|状态码（1成功，0失败）|
|data|读者的详细信息|

## 2.3. 借阅信息页面设计
![pic1](images/借阅信息页面.png)
- 用例图参见：借阅用例
- 类图参见：借阅类
- 顺序图参见：借阅图书顺序图
- API接口如下：

1. 借阅信息API

- 功能：用于获取读者的借阅信息
- 请求地址： http://localhost:8080/BookManagementSystem/getBorrowInfo
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|borrow_id|是|读者编号|

- 返回实例：
```
{
    "status_code": "1/0",
    "data": 
    [
        {
            "book_name","大学物理",
            "book_id","ME_2323",
            "book_type","3",
            "author","梅恩",
            "press","成大出版社",
            "price","66.66",
            "borrow_time","2018-10-10 10:10:10",
            "should_r_time","2018-11-10 10:10:10",
        },
    ]
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|status_code|状态码（1成功，0失败）|
|data|借阅信息的详细信息|


### 2.4. 添加图书页面设计
![pic1](images/添加图书.png)
- 用例图参见：图书用例
- 类图参见：图书类
- 顺序图参见：图书顺序图
- API接口如下：

1. 添加图书API

- 功能：用于管理员添加图书信息
- 请求地址： http://localhost:8080/BookManagementSystem/addBook
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|book_id|是|图书编号|
|book_name|是|图书名称|
|book_type|否|类别（默认文学类）|
|author|是|作者|
|press|是|出版社|
|price|是|单价|
|publish_time|是|出版日期|

- 返回实例：
```
{
    "status_code": "1/0"
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|status_code|状态码（1成功，0失败）|

