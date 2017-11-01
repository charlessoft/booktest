# Basin spider


<a name="overview"></a>
## Overview
basin 爬虫文档 api


### Version information
*Version* : 1.0.0


### Contact information
*Contact Email* : 7671557@qq.com


### License information
*License* : Apache 2.0  
*License URL* : http://www.apache.org/licenses/LICENSE-2.0.html  
*Terms of service* : http://swagger.io/terms/


### URI scheme
*Host* : 127.0.0.1  
*BasePath* : /v1  
*Schemes* : HTTP


### Tags

* spiderapps : 爬虫app管理
* sys : 系统参数配置
* tasks : 任务管理




<a name="paths"></a>
## Paths

<a name="spiderapps-post"></a>
### 新增爬虫app
```
POST /spiderapps
```


#### Description
新增爬虫app


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Body**|**body**  <br>*required*|spider-app 字段|[SpiderApp](#spiderapp)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|ok|No Content|
|**400**|Invalid input|No Content|


#### Consumes

* `application/json`


#### Produces

* `application/json`


#### Tags

* spiderapps


<a name="getspiderapps"></a>
### 获取爬虫app列表(支持分页查询)
```
GET /spiderapps
```


#### Description
获取爬虫app列表,支持模糊查询,返回查询个数.(支持分页查询)


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Query**|**limit**  <br>*optional*|取多少条|integer (int32)|
|**Query**|**offset**  <br>*optional*|偏移量|integer (int32)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK  <br>**Headers** :   <br>`X-Total-Count` (integer) : 返回查询记录总数.|< [SpiderApp](#spiderapp) > array|
|**400**|Invalid input|No Content|


#### Produces

* `application/json`


#### Tags

* spiderapps


<a name="getspider"></a>
### 获取已存在的spider app
```
GET /spiderapps/{spiderid}
```


#### Description
获取已存在的spider app


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**spiderid**  <br>*required*|爬虫id|string (string)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|[SpiderApp](#spiderapp)|
|**400**|Invalid input|No Content|


#### Produces

* `application/json`


#### Tags

* spiderapps


<a name="updatespider"></a>
### 更新已存在的spider app
```
PUT /spiderapps/{spiderid}
```


#### Description
更新已存在的spider app


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**spiderid**  <br>*required*|爬虫id|string (string)|
|**Body**|**body**  <br>*required*|更新指定spider-app对象|[SpiderApp](#spiderapp)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|No Content|
|**400**|Invalid input|No Content|


#### Produces

* `application/json`


#### Tags

* spiderapps


<a name="spiderapps-spiderid-delete"></a>
### 删除指定的spider app
```
DELETE /spiderapps/{spiderid}
```


#### Description
删除指定的spiderapp


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**spiderid**  <br>*required*|爬虫id|string (string)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|No Content|
|**400**|Invalid input|No Content|


#### Tags

* spiderapps


<a name="createspidertype"></a>
### 创建类型
```
POST /sys/types
```


#### Description
创建类型


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Body**|**body**  <br>*required*|创建类型|[SpiderType](#spidertype)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|No Content|


#### Produces

* `application/json`


#### Tags

* sys


<a name="getspidertypes"></a>
### 获取类型配置(spider app接口包含类型了)
```
GET /sys/types
```

Caution : 
operation.deprecated


#### Description
获取类型配置


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**default**|OK|No Content|


#### Produces

* `application/json`


#### Tags

* sys


<a name="deletespiderbytypeid"></a>
### 删除指定类型配置
```
DELETE /sys/types/{typeid}
```


#### Description
删除指定类型配置


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**typeid**  <br>*required*|类型id|integer (int32)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|No Content|
|**400**|Invalid input|No Content|
|**404**|typeid not found|No Content|


#### Produces

* `application/json`


#### Tags

* sys


<a name="tasks-post"></a>
### 创建一个新任务
```
POST /tasks
```


#### Description
createNewTask


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Body**|**body**  <br>*required*|spiderapp object that needs to be added to spiderapps|[TaskInfo](#taskinfo)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|No Content|
|**400**|Invalid input|No Content|


#### Consumes

* `application/json`


#### Produces

* `application/json`


#### Tags

* tasks


<a name="getalltasks"></a>
### 获取所有任务列表
```
GET /tasks
```


#### Description
返回所有任务列表


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|< [Task](#task) > array|


#### Produces

* `application/json`


#### Tags

* tasks


<a name="updateconfingtask"></a>
### 配置采集任务
```
PUT /tasks/config/{taskname}
```


#### Description
配置采集任务


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**taskname**  <br>*required*|任务名称|string (string)|
|**Body**|**body**  <br>*required*|创建类型|[ConfigTask](#configtask)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|No Content|
|**400**|Invalid input|No Content|
|**404**|Taskid not found|No Content|


#### Produces

* `application/json`


#### Tags

* tasks


<a name="gettasklog"></a>
### 获取任务采集日志(支持分页查询)
```
GET /tasks/log/{taskname}
```


#### Description
获取任务采集日志(支持分页查询)


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Header**|**X-Total-Count**  <br>*optional*|返回查询记录总数|integer (int32)|
|**Path**|**taskname**  <br>*required*|任务名称|string (string)|
|**Query**|**limit**  <br>*optional*|取多少条|integer (int32)|
|**Query**|**offset**  <br>*optional*|偏移量|integer (int32)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|< [TaskLog](#tasklog) > array|
|**400**|Invalid input|No Content|
|**404**|Taskid not found|No Content|


#### Produces

* `application/json`


#### Tags

* tasks


<a name="gettaskresult"></a>
### 获取任务采集日志(支持分页查询)
```
GET /tasks/result/{taskid}
```


#### Description
获取任务采集日志(支持分页查询)


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Header**|**X-Total-Count**  <br>*optional*|返回查询记录综述|integer (int32)|
|**Path**|**taskid**  <br>*required*|任务名称|string (string)|
|**Query**|**limit**  <br>*optional*|取多少条|integer (int32)|
|**Query**|**offset**  <br>*optional*|偏移量|integer (int32)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|< [TaskResult](#taskresult) > array|
|**400**|Invalid input|No Content|
|**404**|Taskid not found|No Content|


#### Produces

* `application/json`


#### Tags

* tasks


<a name="webhooktaskid"></a>
### webhook,用于集成第三方采集回调数据
```
POST /tasks/{taskname}
```


#### Description
集成神箭手等采集服务,采集的数据.发送到该接口中,保存到对应的结果集中.


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**taskname**  <br>*required*|任务名称|string (string)|
|**Body**|**body**  <br>*required*|采集结果数据|[SpiderData](#spiderdata)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|No Content|
|**400**|Invalid input|No Content|
|**404**|Taskid not found|No Content|


#### Produces

* `application/json`


#### Tags

* tasks


<a name="gettasktaskid"></a>
### 获取任务信息/状态/采集量
```
GET /tasks/{taskname}
```


#### Description
获取任务信息/状态/采集量


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**taskname**  <br>*required*|任务名称|string (string)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|[TaskStatus](#taskstatus)|
|**400**|Invalid input|No Content|
|**404**|Taskid not found|No Content|


#### Produces

* `application/json`


#### Tags

* tasks


<a name="updatetaskid"></a>
### 更新任务(启动/停止)任务
```
PUT /tasks/{taskname}
```


#### Description
更新任务(启动/停止)任务


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**taskname**  <br>*required*|任务名称|string (string)|
|**Body**|**body**  <br>*optional*|状态(stop\|start)|[TaskScheduler](#taskscheduler)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|No Content|
|**400**|Invalid input|No Content|
|**404**|Taskid not found|No Content|


#### Produces

* `application/json`


#### Tags

* tasks


<a name="deletebytaskid"></a>
### 删除指定任务
```
DELETE /tasks/{taskname}
```


#### Description
删除指定任务


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**taskname**  <br>*required*|任务名称|string (string)|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|No Content|
|**400**|Invalid input|No Content|
|**404**|Taskid not found|No Content|


#### Produces

* `application/json`


#### Tags

* tasks




<a name="definitions"></a>
## Definitions

<a name="configtask"></a>
### ConfigTask

|Name|Description|Schema|
|---|---|---|
|**extra**  <br>*optional*|自定义数据|object|
|**option**  <br>*optional*|可选|enum (可选,设置历史才生效 2017-01-01~2017-02-02--需要app支持(暂不支持))|
|**proxy**  <br>*optional*||string (string)|
|**type**  <br>*optional*||enum (once, realtime, history)|
|**urls**  <br>*optional*||< string > array|


<a name="spiderapp"></a>
### SpiderApp

|Name|Description|Schema|
|---|---|---|
|**createtime**  <br>*optional*|创建时间|string (date-time)|
|**description**  <br>*optional*|爬虫描述,支持md语法|string (string)|
|**name**  <br>*optional*|爬虫名称,英文表示|string (string)|
|**script**  <br>*optional*|爬虫脚本|string (string)|
|**simplename**  <br>*optional*|爬虫简称等|string (string)|
|**type**  <br>*optional*|爬虫app类型, url\|query|string (string)|
|**updatetime**  <br>*optional*|更新时间|string (date-time)|


<a name="spiderdata"></a>
### SpiderData

|Name|Schema|
|---|---|
|**fields**  <br>*optional*|< string > array|
|**name**  <br>*optional*|string|
|**timestamp**  <br>*optional*|string (date-time)|


<a name="spidertype"></a>
### SpiderType

|Name|Schema|
|---|---|
|**name**  <br>*optional*|string (string)|


<a name="task"></a>
### Task

|Name|Schema|
|---|---|
|**name**  <br>*optional*|string|
|**status**  <br>*optional*|enum (running, stop)|
|**updatetime**  <br>*optional*|string|


<a name="taskinfo"></a>
### TaskInfo

|Name|Description|Schema|
|---|---|---|
|**data**  <br>*optional*|采集任务|string|
|**spidername**  <br>*optional*|爬虫app 名称|string|
|**status**  <br>*optional*||enum (running, stop)|
|**taskname**  <br>*optional*|任务名称|string|
|**type**  <br>*optional*||enum (url, query)|


<a name="tasklog"></a>
### TaskLog

|Name|Schema|
|---|---|
|**msg**  <br>*optional*|string|
|**name**  <br>*optional*|string|
|**status**  <br>*optional*|string|
|**url**  <br>*optional*|string|


<a name="taskresult"></a>
### TaskResult

|Name|Schema|
|---|---|
|**content**  <br>*optional*|string|
|**extra**  <br>*optional*|string|
|**html**  <br>*optional*|string|
|**publish_date**  <br>*optional*|string|
|**title**  <br>*optional*|string|
|**update_time**  <br>*optional*|string|
|**url**  <br>*optional*|string|


<a name="taskscheduler"></a>
### TaskScheduler

|Name|Schema|
|---|---|
|**status**  <br>*optional*|string|


<a name="taskstatus"></a>
### TaskStatus

|Name|Description|Schema|
|---|---|---|
|**1d-pending**  <br>*optional*|1天采集量增量|string|
|**1d-success**  <br>*optional*|1天成功采集量|string|
|**1h-pending**  <br>*optional*|1小时采集增量|string|
|**1h-success**  <br>*optional*|1小时成功采集量|string|
|**5m-pending**  <br>*optional*|5分钟采集增量|string|
|**5m-success**  <br>*optional*|5分钟成功采集量|string|
|**name**  <br>*optional*||string|





