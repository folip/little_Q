### 高德API的使用

---

相关连接：

https://lbs.amap.com/api/webservice/gettingstarted  高德web api文档，基本上够用了

http://docs.python-requests.org/zh_CN/latest/user/quickstart.html  对python进行http request的基本操作

#### 相关方向

`坐标转换`

定位，将GPS模块得到的GPS信息转化成高德可以支持的坐标（可能是经纬度坐标？）便于后序的处理。

`地理/逆地理编码`

- 地理编码：将详细的结构化地址转换为高德经纬度坐标。且支持对地标性名胜景区、建筑物名称解析为高德经纬度坐标。
  结构化地址举例：北京市朝阳区阜通东大街6号转换后经纬度：116.480881,39.989410 
  地标性建筑举例：天安门转换后经纬度：116.397499,39.908722
- 逆地理编码：将经纬度转换为详细结构化的地址，且返回附近周边的POI、AOI信息。
  例如：116.480881,39.989410 转换地址描述后：北京市朝阳区阜通东大街6号

`路径规划`

`搜索`

一个结果的示例：

![Snipaste_2018-12-01_00-19-19](C:\Users\yuanl\Pictures\截图\Snipaste_2018-12-01_00-19-19.png)



#### 基本流程

暂考虑python编程环境中，利用web api进行（js，android, ios好像都不太合适）

* API申请：申请个账号就好，结果如图：
  * ![Snipaste_2018-12-01_00-23-37](C:\Users\yuanl\Pictures\截图\Snipaste_2018-12-01_00-23-37.png)
  * key: 0ccaf0e63c57e169e8cf27a2ba926f77
  * 配额对于调试开发完全充足，基本上每种有两千条左右吧

* 拼接得到URL

  * 示例：路径规划

    * 包括起始地点与和终结地点的经纬度，输出格式，key

    * 如下：

      ```html
      https://restapi.amap.com/v3/direction/driving?origin=116.45925,39.910031&destination=116.587922,40.081577&output=xml&key=<用户的key>
      ```

* 发送请求，得到结果，解析数据

  * 最简单的可以用python request库中的get函数



Python最基础示例：

![Snipaste_2018-12-01_00-30-07](C:\Users\yuanl\Pictures\截图\Snipaste_2018-12-01_00-30-07.png)

