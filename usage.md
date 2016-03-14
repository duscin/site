# maptalks使用方法
```bash
npm install -g maptalks
cd /home/foo/maptalks
maptalks init
# init后的目录结构
/home/foo/maptalks
    |- www
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
        |- sample
    |- maptalks.json
#运行
maptalks --config maptalks.json
```
# 默认的maptalks.json

```json
{
    "server" : {
        "port" : 8090,
        "loglevel": "INFO",
        //日志有可能需要配置到别的目录, 方便日志分析软件统一管理
        "logpath" : "./logs", 
        "docroot" : "./www"
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
                "folder": "./tiles/sample",
                "size": 256
            }
        ]
    }
}
```
