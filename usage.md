# maptalks使用方法
```bash
npm install -g maptalks
cd /home/foo/maptalks
maptalks install
#install后的maptalks目录
/home/foo/maptalks
    |- resources
        |-maptalks.js
        |-maptalks.css
        |-images+
        |-maptalks.foo.js
    |- db
        |-default.db
    |- logs
    |- dynamic
    |- snap
       |-shots
    |- tiles
        |- arcgis-nanjing
    |- maptalks.json
#运行
maptalks --config maptalks.json
```
# maptalks.json示例

```json
{
    "server" : {
        //Port of engine server
        "port" : 8090,
        //全局统一的日志级别
        "loglevel" : "INFO",
        "resource" : "./resources",
    },
    "database" : {
        "instances": [
            {
                "name": "default",
                "type": "sqlite",
                //表示引擎主目录
                "database": "./db/default.db"
            },
            {
                "name": "mysql",
                "type": "mysql",
                "host": "localhost",
                "port": 3306,
                "database": "testdb",
                "parameters": "?useUnicode=true&characterEncoding=utf-8",
                "username": "root",
                "password": "root",
                "pool" : {
                    "initialSize": 5,
                    "maxActive": 50
                }
            }
        ],
        "pool": {
            "initialSize": 2,
            "maxActive": 20,
            "maxWait": 60000,
            "timeBetweenEvictionRunsMillis": 60000,
            "minEvictableIdleTimeMillis": 300000,
            "validationQuery": "SELECT 'x'",
            "testWhileIdle": true,
            "testOnBorrow": false,
            "testOnReturn": false,
            "poolPreparedStatements": true,
            "maxPoolPreparedStatementPerConnectionSize": 20
        }
    },
    "dynamic" : {
         //override global loglevel
        "loglevel" : "INFO",
        "port": 11216,
        "minQueriedDataCountToCache": 3000
    },
    "rest" : {
        "port": 11215
    },
    "tile" : {
        "loglevel" : "ERROR",
        "port": 11214,
        "instances": [
            {
                "name": "custom-1",
                "vendor": "custom",
                "format": "png",
                "type": "exploded",
                "version": "default",
                //支持相对路径
                "folder": "./mapdata/mapabc-2012-07",
                "size": 256
            }
        ]
    }
}
```
