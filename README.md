# 使用xbim获取实体属性

## getBasicInfo
获取一个指定实体的信息，包括express属性信息和definedbyProperties信息
其中，express属性只获取直接有值的，不获取引用的
另外，express属性也获取了几何表达形式IfcProductDefinitionShape

## 使用
```
QuickStart start = new QuickStart(fileName);
var aDoor = start.getDoorById(id);
start.getBasicInfo(aDoor);
```