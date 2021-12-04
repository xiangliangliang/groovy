<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Hello, Bootstrap Table!</title>

    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css" integrity="sha384-GJzZqFGwb1QTTN6wy59ffF1BuGJpLSa9DkKMp0DgiMDm4iYMj70gZWKYbI706tWS" crossorigin="anonymous">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.6.3/css/all.css" integrity="sha384-UHRtZLI+pbxtHCWp1t77Bi1L4ZtiqrqD80Kn4Z8NTSRyMA2Fd33n5dQ8lWUE00s/" crossorigin="anonymous">
    <link rel="stylesheet" href="https://unpkg.com/bootstrap-table@1.15.3/dist/bootstrap-table.min.css">
  </head>
  <body>
    <table data-toggle="table"
			data-pagination="true"
			data-side-pagination="client"
			data-page-size="3">
      <thead>
        <tr>
          <th>Item ID</th>
          <th>Item Name</th>
          <th>Item Price</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
          <td>Item 1</td>
          <td>$1</td>
        </tr>
        <tr>
          <td>2</td>
          <td>Item 2</td>
          <td>$2</td>
        </tr>
        <tr>
          <td>3</td>
          <td>Item 3</td>
          <td>$3</td>
        </tr>
        <tr>
          <td>4</td>
          <td>Item 4</td>
          <td>$4</td>
        </tr>
		<tr>
          <td>5</td>
          <td>Item 5</td>
          <td>$5</td>
        </tr>
      </tbody>
    </table>

    <script src="https://code.jquery.com/jquery-3.3.1.min.js" integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8=" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js" integrity="sha384-B0UglyR+jN6CkvvICOB2joaf5I4l3gm9GU6Hc1og6Ls7i6U/mkkaduKaBhlAXv9k" crossorigin="anonymous"></script>
    <script src="https://unpkg.com/bootstrap-table@1.15.3/dist/bootstrap-table.min.js"></script>
	<script>
		$('#table').bootstrapTable({
	  columns: [{
		field: 'id',
		title: 'Item ID'
	  }, {
		field: 'name',
		title: 'Item Name'
	  }, {
		field: 'price',
		title: 'Item Price'
	  }],
	  data: [{
		id: 1,
		name: 'Item 1',
		price: '$1'
	  }, {
		id: 2,
		name: 'Item 2',
		price: '$2'
	  }]
	})
	</script>
  </body>
</html>






## groovy
learn groovy
https://www.cnblogs.com/eastson/archive/2012/05/27/2519781.html
https://blog.csdn.net/qq_35495763/article/details/85722207

## 执行shell语句并赋值
hostname = "hostname".excute().text

## 类似列表推导式
num = [1,2,3,5]

num_2 = num.collect{it*2}

## 统计
def text ="""
Look for the bare necessities
The simple bare necessities
Forget about your worries and your strife
I mean the bare necessities
Old Mother Nuture's recipes
That bring the bare necessities of life
"""

def words = text.tokenize()

def wordFreq = [:]

words.each{word->
    wordFreq[word] = wordFreq.get(word,0)+1
}

println wordFreq

[Look:1, for:1, the:3, bare:4, necessities:4, The:1, simple:1, Forget:1, about:1, your:2, worries:1, and:1, strife:1, I:1, mean:1, Old:1, Mother:1, Nuture's:1, recipes:1, That:1, bring:1, of:1, life:1]


## groupBy

def errorCodeList = [
                [code: "1", language: "2", content: "3"],
                [code: "1", language: "2", content: "4"],
                [code: "1", language: "3", content: "5"],
                [code: "1", language: "3", content: "6"],
                [code: "2", language: "1", content: "3"],
                [code: "2", language: "2", content: "3"],
                [code: "1", language: "2", content: "4"]
        ]
        
gb1 = errorCodeList.groupBy{it.code}

println gb1["1"] 

//[[code:1, language:2, content:3], [code:1, language:2, content:4], [code:1, language:3, content:5], [code:1, language:3, content:6], [code:1, language:2, content:4]]

## 筛选字符串相同的前缀

a = ['aa','aa-a1-b1-s0','aa-a1-b1-s1','aa-a2-b1-s0','aa-a2-b1-s1','aa-a3']

b = a.collect{it.replaceAll("-s.*","")}.unique()

c = b.collect{ a.find{item -> item.contains(it)}}

说明1 》 b = a.collect{it.replaceAll("-s.*","")}.unique() ==> [aa, aa-a1-b1, aa-a2-b1, aa-a3]

说明2 》 c = b.collect{ a.find{item -> item.contains(it)}} ==> [aa, aa-a1-b1-s0, aa-a2-b1-s0, aa-a3]

简化：b = a.collect{it.replaceAll("-s.*","")}.unique().collect{ a.find{item -> item.contains(it)}} ==> [aa, aa-a1-b1-s0, aa-a2-b1-s0, aa-a3]


## 执行脚本.execute().text.readLines()

rsp = 'cmd /c dir'.execute(null, new File("E:\\Jenkins")).text.readLines()

rsp = rsp.findAll{item-> item.size()>0}.each{it.trim()}.each{println(it)}

https://www.cnblogs.com/dreampursuer/p/5569266.html


## 遍历文件目录

https://blog.csdn.net/rainyRs/article/details/53184805

def list= []

new File('D:\\Groovy\\Scripts').eachFile{ list<< it.name }
    //eachFile() returns a list of File objects
    
assert list ==   ['Script.bat', 'File1.txt', 'File2.txt', 'Directory1', 'Directory2']

list= []

new File('D:\\Groovy\\Scripts').eachFileRecurse{ list<< it.name }

assert list == ['Script.bat', 'File1.txt', 'File2.txt','Directory1', 'Directory2', 'SubDir1']
 
list= []

new File('D:\\Groovy\\Scripts').eachDir{ list<< it.name }

assert list == ['Directory1', 'Directory2']

## 解析xml

/**
     test.xml 文件的内容如下：

     <langs type="current">
         <language1>Java</language1>
         <language2>Groovy</language2>
         <language3>JavaScript</language3>
     </langs>
 */
 
 //一行代码就解析了xml
 
 def langs = new XmlParser().parse("test.xml")//打印出node的属性println langs.attribute('type')
 
 //对xml文件的遍历langs.each {println it.text()}
 
 //输出
current 

Java

Groovy

JavaScript

## 各种文件操作
https://blog.csdn.net/wensonlee/article/details/84620640

assert new File('D:/Groovy/Scripts').list().toList() ==
  ['Script.bat', 'File1.txt', 'File2.txt', 'Directory1', 'Directory2']
  
  
  assert new File('D:/Groovy/Scripts').listFiles().toList()*.name ==
  ['Script.bat', 'File1.txt', 'File2.txt', 'Directory1', 'Directory2']
    
    //listFiles() returns array of File objects
    
 assert new File('D:/Groovy/Scripts').listFiles(     {dir, file-> file ==~ /.*?\.txt/ } as FilenameFilter   ).toList()*.name == [ 'File1.txt', 'File2.txt' ]
 
 
 ## json 例子,筛选 enable=true的case
 str = {
"test_1":[
	{"Enable":true},{"para":2}
	],
"test_2":[
	{"Enable":false},{"para":0}
	],
"test_3":[
	{"Enable":true},{"para":2}
	],
"test_4":[
	{"Enable":true},{"para":3}
	]
}

test_list = json_content.findAll{it.value[0].Enable==true}.keySet() // [test_1, test_3, test_4]


    
## 筛选结果

   stage('Preparation') { 
        script{
            
            fp = 'summary.txt' 
            File file = new File(fp) 
            def propMap = readJSON text : '{}' 
                propMap.File_analyzed = file.readLines().find{it.contains("File analyzed")}.toString().split(":")[1].trim() - ']' 
                propMap.defect_info = file.readLines().findAll{it.startsWith("\t") or it.contains("Defect")}.collect{it.replaceAll("\t","")}.toString().split(":")[1].trim() - ']' 
            println propMap.toString()
            
        }

   }
   
   
## 筛选命令行

curl -u xxx:xxx http://192.168.56?????? -o abc.txt

fp = 'E:/Jenkins_20200204/abc.txt' 

File file = new File(fp) 

def ct=file.readLines().find{it.contains('jnlpUrl')}.toString()

st = ct.indexOf('-jnlpUrl')

end = ct.indexOf('</pre>')-1

cmd = 'java -jar agent.jar ' + ct[st..end]

println cmd
