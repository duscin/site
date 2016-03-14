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
# 默认的maptalks.json

```json
{
    "server" : {
        "port" : 8090,
        "loglevel" : "INFO",
        "resource" : "./resources",
    },
    "database" : {
        "instances": [
            {
                "name": "default",
                "type": "sqlite",
                "database": "./db/default.db"
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
    "rest" : {
        "port": 11215
    },
    "tile" : {
        "loglevel" : "ERROR",
        "port": 11214,
        "instances": [
            {
                "name": "sample",
                "vendor": "custom",
                "format": "png",
                "type": "exploded",
                "version": "default",
                //支持相对路径
                "folder": "./tiles/sample",
                "size": 256
            }
        ]
    }
}
```
