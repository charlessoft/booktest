# Universal Backend

项目路径：/data/BasinSpace/src/universal_backend

----------------

## Api

### Insert

- URL:/insert
- Type:JSON
- HTTP Method:POST
- Parameters:

    |name | required | type and range | info |
    | --- | ---- | --- | --- |
    | unlimited | false | unlimited |  |


- Parameters Example:

    None

- Result Example:

    None


### Select

- URL:/select
- HTTP Method:GET
- Parameters:

    |name | required | type and range | info |
    | --- | ---- | --- | --- |
    | filters   | false | dict | 规则 |
    | offset | false | int | 起始位置 |
    | limit | false | int | 返回个数 |
    | starttime | false | timestamp | 开始时间 |
    | endtime | false | timestamp | 结束时间 |

- Parameters Example:

        {
            'limit': 10,
            'offset': 0,
            'starttime': 1508986970.967,
        }


- Result Example:

        [
            item, item ....
        ]
    
------------------------

## Client

        from universal_backend.client import UBApi
    
        api = UBApi('http://localhost:5000')
        api.insert({'name':'test'})
        data = api.select()
    
        print(data)