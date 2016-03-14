# maptalks使用方法
```bash
npm install -g maptalks
cd /home/foo/maptalks
maptalks install
#install后的maptalks目录
/home/foo/maptalks
    |- resource
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