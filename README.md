#### 第1步：先下载编译protobuf的js编译器

下载链接为`https://github.com/protocolbuffers/protobuf/releases`  在该 地址下选择最新的下载包 [protoc-21.5-win64.zip](https://github.com/protocolbuffers/protobuf/releases/download/v21.5/protoc-21.5-win64.zip) 并提取内部的bin文件包

#### 第2步：准备proto文件

将准备好的proto文件放在protoc.exe的同级目录下（一般就是bin文件底下），进入cmd命令行，使用 

```
protoc  --js_out=import_style=commonjs,binary: ./xxx.proto
```

即可生成编译后的js文件

#### 第3步：使用该编译文件

1. 需要再次将该js打包，需要require.js,一个打包的browserify.js/webpack

   ```javascript
   npm install require -g
   npm install browserify -g 
   npm install google-protobuf
   ```

2. 然后新建一个打包的js文件，export.js

   ```javascript
   var address = require("js文件路径");
   module.exports = {
       DataProto:address
   }
   ```

3. 然后执行打包命令"`browserify export.js -o  proto_main.js`",打包完成的js就可以使用了

4. 引入js文件使用

   ```javascript
   import "./proto_main.js"
   ```

   
