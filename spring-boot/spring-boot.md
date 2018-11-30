1.  spring-boot 415错误

 	-  媒体类型错误，需要设置content-type = application/json, 且数据格式为json字符串

2. spring-boot mongo排序

   [springboot(十一)：Spring boot中mongodb的使用](https://www.cnblogs.com/ityouknow/p/6828919.html)

   先查询，在对查询结果list进行排序。

   Comparator sort = Comparator.comparing(Objetc(eg: String)::getId(方法，eg: toString))

   or

   Comparator sort = Comparator.comparing(Object s -> s.toString())

   其中s需要实现compara方法

