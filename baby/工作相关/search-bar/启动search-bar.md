###准备环境

1.在本地机器创建/opt/tomcat7/conf/app/new_bar.properties，

文件内容见search-bar/bb_conf/pre/new_bar.properties。

原因是服务启动依赖PropertyPlaceholderConfigurerbean属性（search-bar-provider/src/main/resources/spring/spring_new_bar.xml）

2.安装并启动redis，将本地redis地址覆盖到刚创建的new_bar.properties中。

3.本地安装tomcat

4.申请 跳板机和10.2.19.43 机器权限

5.本地安装proxifier 代理软件，导入proxifer.ppx 配置文件

6.远程登录  ssh -D 8000 zeyu.lang@bbgw.husor.com -p 8725

7.测试代理创建是否成功，可以访问<http://10.2.11.15:9200/_plugin/head>

###启动服务

1.idea中添加 tomcat server

2.在deployment tab 中添加 search-bar-provider war包

###调试服务

curl 命令 如：

~~~shell
curl -H "Content-Type: application/json" -d '{"closeProfile":true,"filterConditions":[{"field":"item_sold_out","fieldValue":[0]}],"from":"Android","highLight":true,"isDebug":true,"newItemsAggNum":0,"notFilterConditions":[{"field":"brand.brand_type","fieldValue":[80]},{"field":"tuan_type","fieldValue":[3,12,113]},{"field":"oversea_type","fieldValue":[12,113]}],"pageNo":1,"pageSize":20,"propFilter":false,"query":"卫衣巴拉巴拉","sceneFilterCondition":{"beidianFilter":false,"mallOverseaFilter":false,"martMallFilter":false,"overseaFilter":false,"pintuanFilter":false,"showFilter":false,"tuanFilter":false},"searchCheck":true,"searchComplement":true,"searchGoodsQuery":true,"shouldFilterConditions":[{"field":"cid.c1","fieldValue":["49"]},{"field":"cid.c2","fieldValue":["49"]},{"field":"cid.c3","fieldValue":["49"]}],"subType":0,"type":10,"userId":""}' -XPOST 10.2.20.57:8080/search-bar/search/searchbar
~~~

或post 



