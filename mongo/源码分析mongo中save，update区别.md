## 源码分析mongo中save，update区别





### 1. update() 方法

update() 方法用于更新已存在的文档。语法格式如下：

```js
db.collection.update(
   <query>,
   <update>,
   {
     upsert: <boolean>,
     multi: <boolean>,
     writeConcern: <document>
   }
)
```

**参数说明：**

- **query** : update的查询条件，类似sql update查询内where后面的。
- **update** : update的对象和一些更新的操作符（如$,$inc...）等，也可以理解为sql update查询内set后面的
- **upsert** : 可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，默认是false，不插入。
- **multi** : 可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。
- writeConcern :可选，抛出异常的级别。

### 2. save() 方法

save() 方法通过传入的文档来替换已有文档。语法格式如下：

```
db.collection.save(
   <document>,
   {
     writeConcern: <document>
   }
)
```

**参数说明：**

- **document** : 文档数据。
- **writeConcern** :可选，抛出异常的级别。

db.save方法根据传入document的id进行更新

- ```javascript
  db.name.save
  
  function (obj) {
  
  if (obj == null || typeof obj == "undefined") {
  
  throw "can't save a null";
  
  }
  
  if (typeof obj == "number" || typeof obj == "string") {
  
  throw "can't save a number or string";
  
  }
  
  if (typeof obj._id == "undefined") {
  
  obj._id = new ObjectId;
  
  return this.insert(obj);
  
  } else {
  
  return this.update({_id:obj._id}, obj, true);
  
  }
      
  }
  
  
  
  
  ```

### 3. 参考文档

作者：super_paul
链接：https://www.jianshu.com/p/4a766bbd7a17
來源：简书
简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。