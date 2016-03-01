---
  layout: api
  title: 文件操作
---

## IE下文件操作

### 读取文件夹下所有文件并重命名

<pre><code data-language="javascript">function readFiles(path){
    document.write("开始读取文件:<br/>");
    //初始化fso对象;
    fso = new ActiveXObject("Scripting.FileSystemObject");
    //根据路径获取文件夹;
    fldr = fso.GetFolder(path);
    //获取目录下的所有文件;
    fc = new Enumerator(fldr.files);
    //遍历所有文件
    for(; !fc.atEnd();   fc.moveNext()){
        //取文件对象
        s=fc.item();
        var name = s.name.replace(/\s/g, '');
        //文件重命名 王菲 - 爱不可及(电影《触不可及》主题曲)
        var nameArr = name.split('.');
        var extName = nameArr[nameArr.length-1];
        var pureName = name.split('.'+extName)[0];
        nameArr = pureName.split('-');
        //alert(pureName)
        var newName = nameArr[1] + '-' + nameArr[0] + '.' + extName;
        s.move(path + newName);
        //输出文件的类型和名称;
        document.write("pre:"+name + " new:"+newName +"<br/>");
    }
}

_getListByFolder: function(folderPath){ //递归所有子文件夹
    var fso = new ActiveXObject("Scripting.FileSystemObject");
    var folderObj = fso.GetFolder(folderPath);
    var filesEnumerator = new Enumerator(folderObj.files);
    var fileTypeReg = /.js$/;
    var subFolderEnumerator = new Enumerator(folderObj.subFolders);

    for(; !filesEnumerator.atEnd();   filesEnumerator.moveNext()){
        var file = filesEnumerator.item();
        if(file.name.match(fileTypeReg)){
            this._dumpFile(file);
        }
    }

    for(; !subFolderEnumerator.atEnd();   subFolderEnumerator.moveNext()){
        this._getListByFolder(subFolderEnumerator.item().Path);
    }

},
_dumpFile: function(file){
    var fso = new ActiveXObject("Scripting.FileSystemObject");
   // console.log(file.name);
    var fileObj = fso.OpenTextFile(file, 1, true); //写方式打开


    if(!fileObj.AtEndOfStream){
        var content = fileObj.ReadAll();
        this._findTr(content, file.name);
    }
    fileObj.Close();
    //this._langList.abc = content;
},
_findTr: function(contnet, file){
    var trReg = /IOT.tr\s*\(['"]([^'"]+)/g;
    var text;
    while(text = trReg.exec(contnet)){
        this._langList[text[1]] = {content:'', file: file};
    }
}
</code></pre>