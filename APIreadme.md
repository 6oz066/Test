# Wetender合约接口说明文档

## 县级政府合约（County_Gov）
### 变量
```
struct Towns{address town,bool valid} 乡级政府列表，valid用于检验乡镇
```
### 初始化
```
constructor(string name) public Government(name){}
```
### 功能函数
1.添加乡级政府
```
function addTown(string name, address town) public onlyOwner() 
```
2.删除乡级政府
```
function removeTown(string name) public onlyOwner()  
```
3.查询乡级政府是否存在
```
function checkTown(string name) public view returns(string, address)
```

## 乡级政府合约(Town_Gov)
### 变量
```

