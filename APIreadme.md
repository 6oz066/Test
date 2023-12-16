# Wetender合约接口说明文档

## 县级政府合约（County_Gov）
### 变量
- struct Towns{address town,bool valid} 乡级政府列表，valid用于检验乡镇
### 初始化
- constructor(string name) public Government(name){}
### 函数
- 1.
'''
- function addTown(string name, address town) public onlyOwner() 用于添加乡级政府
'''
- 2.function removeTown(string name) public onlyOwner()  删除乡级政府
- 3.function checkTown(string name) public view returns(string, address) 查询乡级政府是否存在
