## groovy
learn groovy

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
