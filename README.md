# 使用xbim获取实体属性

## getAllIfcProperty
直接使用来获取IFC文件中以下信息：
1. 所有ifcproduct(和它的子类)的EXPRESS非引用属性信息+Pset属性信息（通过getBasicInfo函数）
2. 所有RelContainedInSpatialStructure信息（通过GetRelContains函数）

## getBasicInfo
获取一个指定实体的信息，包括
1. express属性信息（express属性只获取直接有值的，不获取引用的）
2. definedbyProperties信息
3. AABB包围盒几何信息（通过GetAABB函数）

另外，express属性也获取了几何表达形式IfcProductDefinitionShape


## 使用
```
            string path = Directory.GetParent(Directory.GetCurrentDirectory()).Parent.FullName;
            string fileName = path + "//test.ifc"; //this can be either IFC2x3 or IFC4

            IfcStore model = IfcStore.Open(fileName);
            var context = new Xbim3DModelContext(model);
            context.CreateContext();

            PropertyExtract start = new PropertyExtract(model, context);
            string properties = JsonConvert.SerializeObject(start.getAllIfcProperty());
            //start.GetRelContains();
            Console.WriteLine(properties);
```