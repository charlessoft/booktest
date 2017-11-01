# ETL

项目路径：/data/BasinSpace/src/etl

## Api
-------


### Create Task

- URL:/task/create
- Type:JSON
- HTTP Method:POST
- Parameters:

- Parameters Example:

        {
            'source': {
                'url' : 'http://localhost:6000',
                'task': 'test',
                'type' : 'DB_API',
            }, 
            'processor' : {
                'url' : 'http://localhost:12000',
                'type' : 'BID',
                'parameter' : {}
            },
            'dest' : {
                'url' : 'http://localhost:6000',
                'task': 'bid',
                'type' : 'DB_API'
            }
        }

- Result Example:

    None

-----------------

## 结果查看页面

- URL:`/?task=<task_name>`

`<task_name>` 为 订阅服务指定的task_name


