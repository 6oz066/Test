# 部署文件运行说明
本作品采用WeBase一键部署，详见：WeBase技术文档链接https://webasedoc.readthedocs.io/zh-cn/latest/docs/WeBASE/install.html。
## 修改配置（重要）
### 修改配置文件（vi common.properties）；
一键部署支持使用已有链或者搭建新链。通过参数”if.exist.fisco”配置是否使用已有链，以下配置二选一即可：
- 当配置”yes”时，需配置已有链的路径fisco.dir。路径下要存在sdk目录，sdk目录中包含ca.crt, sdk.crt, sdk.key及gm目录，gm目录中包含国密SSL所需证书，包含gmca.crt、gmsdk.crt、gmsdk.key、gmensdk.crt和gmensdk.key
- 当配置”no”时，需配置节点fisco版本和节点安装个数，搭建的新链默认两个群组，建议搭建至少四个群组。
如果不使用一键部署搭建新链，可以参考FISCO BCOS官方文档搭建 FISCO BCOS部署流程。
** 注意：本作品建议使用国密版部署，故需要修改设置配置项encrypt.type=1，并修改设置配置项encrypt.sslType=1来使用使用国密SSL。**
## 访问
一键部署完成后，打开浏览器（Chrome Safari或Firefox），即可访问WeBase平台。（默认端口为5000）  
``http://{deployIP}:{webPort}``  
``示例：http://localhost:5000``    
## 部署流程
将Contract文件夹当中的所有合约导入“合约IDE”中并保存。
在“私钥管理”中创建至少两个用户。建议创建至少四个用户，分别为县级政府（County_Gov），乡级政府（Town_Gov），银行（WeBank），中标企业（Enterprise）。  
将County_Gov、Town_Gov、Bank、Enterprise的四个合约分别部署到County_Gov、Town_Gov、WeBank、Enterprise四个用户当中，输入指定参数即可。企业和银行用户的id，建议使用统一社会信用代码。  
* 县级政府可以通过使用addTown函数，将乡级政府的单位名称和用户地址导入到县级政府特有的乡级政府管理列表town_list中，方便后续管理。  
* 县乡政府的合约统一通过Government合约派生而来，故基本功能一致。  
## 交易环节
### - 1.政府设置预算。（SetBal）  
政府部门要设立当年的采购预算，方可进行立项和招标。
### - 2.政府部门立项。（CreateProj）  
政府部门立项，设立项目标签和项目预算等信息。项目编号建议由上级部门统一批复，防止出现同一个中标企业同时接到两个不同的工单但为同一个ProjectID的现象。







