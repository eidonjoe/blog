# 基于mongodb坐标位置,计算距离并排序

[如何基于mongodb来实现用户当前位置距离显示顺序功能](https://segmentfault.com/q/1010000000526177)

[Geospatial Indexes and Queries](https://docs.mongodb.com/manual/applications/geospatial-indexes/#geospatial-indexes-and-sharding)



#### 插入数据 lng对应经度  lat对应纬度 均为float型
```
db.collection.insert({location:[lng,lat],title:'test title'})
```

#### 创建2D空间索引
#### 2dsphere支持球面检索  2d二维空间搜索

```
db.collection.ensureIndex({location:'2dsphere'})
```
#### 按照半径搜索 搜索半径内的所有的点 按照由近到远排序
```
db.collection.find(
    {
        location:
        {
            $geoWithin:
            {
                $centerSphere: [ [lng, lat], 检索半径]
            }
        }
    }
)
```
mongodb支持其他条件检索
[$box](https://docs.mongodb.com/manual/reference/operator/query/box/#op._S_box),
[$polygon](https://docs.mongodb.com/manual/reference/operator/query/polygon/#op._S_polygon),
[$center](https://docs.mongodb.com/manual/reference/operator/query/center/#op._S_center) (defines a circle),
[$centerSphere](https://docs.mongodb.com/manual/reference/operator/query/centerSphere/#op._S_centerSphere) (defines a circle on a sphere).
#### 如果要计算距离

```
db.collection.aggregate([
   {
     $geoNear: {
        near: { type: "Point", coordinates: [ 116.50077 , 39.976554 ] },
        distanceField: "dist.calculated",
        includeLocs: "dist.location",
        distanceMultiplier: 1000/6371,
        spherical: true
     }
   }
]}
```
spherical参数决定mongodb计算距离的方式,如果为true,那么mongodb将以球面几何方式计算给定的点与需要计算的点的距离,并以弧度表示出来.默认为false,mongodb将以二位平面几何方式计算距离.
*如果使用球面检索(2dsphere),则spherical参数必须指定为true.

distanceField 包含计算距离的输出字段,在文档中嵌入一个字段,使用点来访问

includeLocs 指定用于计算距离的位置的输出字段。当一个位置字段包含多个位置时，这个选项的作用就凸显出来了,定义和访问方式同distanceField

distanceMultiplier 计算出的距离的转换方式,如果要将弧度转换成米,将此字段设置为1000/6371(地球半径)

其他可选参数参照官方文档[$geoNear (aggregation)](https://docs.mongodb.com/manual/reference/operator/aggregation/geoNear/#pipe._S_geoNear)
