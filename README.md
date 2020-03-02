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


    

