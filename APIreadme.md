# Wetender合约接口说明文档
## 合约说明
### 辅助功能合约
- Project 项目进度合约
- Table 表合约
- Government 政府合约
### 部门及管理合约
- Bank 银行合约
- Enterprise 企业合约
- Town_Gov 乡政府合约
- County_Gov 县政府合约




## 项目进度合约（Project)
### 变量
```
Struct Tracedata                         追踪表结构体
{
uint public ProjectId;                   项目编号
string public ProjectName;               项目名称
uint public _status;                     项目状态 状态代号：0.已立项; 1.已招标; 2.正在施工; 3.已竣工; 4.已验收; 5.已投入使用; 6.售后修缮;
}
uint public bal;                         项目预算
uint used_money;                         当前使用总预算  
TraceData[] public traceData;            追踪表   
address public owner;                    项目归属方
address public builder;                  项目承包方            
```
### 初始化
```
constructor(uint id, string name, uint balance) public
```
### 功能函数
1.项目开标（只有所有者可以操作）
```
function Deal(address target, string remark) external onlyOwner()
```
2.正在施工（只有中标者可以操作）
```
function Build(uint money, string remark) external onlyBuilder()
```
3.已竣工（只有中标者可以操作）
```
function Finish(string remark) external onlyBuilder()
```
4.已验收（只有所有者可以操作） 备注：money用于第三方检测验收的预算
```
function Pass(uint money, string remark) external onlyOwner()
```
5.投入使用（只有所有者可以操作）
```
function Work(string remark) external onlyOwner()
```
6.售后修缮（只有所有者可以操作）
```
function AfterMarket(uint money, string remark) external onlyOwner()
```
7.查询项目状态
```
function getStatus() public view returns(uint)
```
8.查询项目使用资金
```
function getPrice() public view returns(uint)
```
9.查询溯源记录
```
function getTraceInfo() public view returns(TraceData[] memory _data)
 ```


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

