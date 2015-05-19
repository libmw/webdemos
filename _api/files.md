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
</code></pre>