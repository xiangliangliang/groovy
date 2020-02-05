pipeline {
	agent {
			label 'master'
			}

	options { 
		disableConcurrentBuilds() 
		buildDiscarder(logRotator(numToKeepStr: '10'))
		timestamps()	
		}

   stages {
       
     stage("file"){
          steps{
              script{
                  echo "file"
                  println("workspace is ${env.WORKSPACE}")
                  println("jenkins home is ${env.JENKINS_HOME}")
                  test_file = "${env.JENKINS_HOME}/workspace/file.json"
                    if(fileExists(test_file) == true) {
                        echo("test file is exists")
                        file_contents = readFile test_file
                        println(file_contents)
                        println("========")
                        def propMap = readJSON file : test_file
                        	propMap.each {
                        	    println ( it.key + " = " + it.value )
                        	}
                        
                        
                        
                        }
					else {
                        error("here haven't find test file")
                    }
				}
			}
		}//
      
      stage('int') {
         steps {
            script{
                //echo 'Hello World'
                println("hello world")
                def age = "Dog"
                age = 40
                println age
                
                println("5 + 4 = " + (5 + 4))
                println("5 - 4 = " + (5 - 4))
                println("5 * 4 = " + (5 * 4))
                println("5 / 4 = " + (5 / 4))
                println("5 / 4 = " + (5.intdiv(4)))
                println("5 % 4 = " + (5 % 4))
                
                println("5.2 + 4.4 = " + (5.2.plus(4.4)))
                println("5.2 - 4.4 = " + (5.2.minus(4.4)))
                println("5.2 * 4.4 = " + (5.2.multiply(4.4)))
                println("5.2 / 4.4 = " + (5.2 / 4.4))
                
                println("3 + 2 * 5 = " + (3 + 2 * 5))
                println("(3 + 2) * 5 = " + ((3 + 2) * 5))
                
                println("age is "+age)
                println("age++ = " + (age++))
                println("++age = " + (++age))
                println("age-- = " + (age--))
                println("--age = " + (--age))
                
                def num = 2.0
                println(num.pow(3))
                // println(Math.round(2.45)) 不能使用Math函数
            }
         }
      } //
      
      stage("string"){
          steps{
              script{
                  
                  def name = "Derek"
                  println('i am ${name}')
                  println("i am ${name}")
                  
                  def multString = ''' i am
                  a String goes on
                  from many lines '''
                  
                  println('show the multString ${multString}')
                  println("show the multString ${multString}")
                  
                  println("3rd Index of Name is " + name[3])
                  println("Index of r is " + name.indexOf('r'))
                  println("1st 3 Chars " + name[0..2])
                  println("Every Other Char " + name[0,2,4])
                  
                  println("Substring at 1 is " + name.substring(1))
                  println("Substring at 1 to 4 is " + name.substring(1,4))
                  println("My name is " + name)
                  
                  println("Derek == Derek: " + ('Derek'.equals('Derek')))
                  println("Derek == derek: " + ('Derek'.equalsIgnoreCase('derek')))
                  
                  println("Length is " + name.length())
                  
                  def repeatStr = "what I said is " * 2
                  println(repeatStr - "what")
                  str_list_1 = repeatStr.split()
                  println(str_list_1.toList())
                  
                  str_list_2 = repeatStr.tokenize()
                  println(str_list_2[1..3])
                  println(repeatStr.toList())
                  
                  println(repeatStr.replaceAll('I','she'))
                  println("Uppercase is " + name.toUpperCase())
                  println("LowCase is " + name.toLowerCase())
                  
                  println("Ant <=> Banana " + ('Ant' <=> 'Banana'))
                  println("Banana <=> Ant " + ('Banana' <=> 'Ant'))
                  println("Ant <=> Ant " + ('Ant' <=> 'Ant'))
              }
          }
      }//
      
   
      stage("list"){
          steps{
              script{
                  echo "list"
                  def primes = [2,3,5,7,11,13]
                  println("2nd prime is " + primes[1])
                  println("3rd prime is " + primes.get(2))
                  
                  def employee = ['Derek', 40, 6.25, [1,2,3]]
                  println("2nd number " + employee[3][1])
                  println("Length is " + primes.size())
                  
                  primes.add(17)
                  primes<<19
                  primes.add(23)
                  primes + [29,31]
                  println(primes)
                  
                  primes - [31]
                  println(primes)
                  
                  println("is empty: " + primes.isEmpty())
                  println("1st 3 is " + primes[0..2])
                  
                  println("Matchs " + primes.intersect([2,3,7]))
                  println("Reverse " + primes.reverse())
                  println("Sore " + primes.sort())
                  println("Last " + primes.pop())
                  
                      
              }
          }
      }//
      
      stage("map"){
          steps{
              script{
                  echo "map"
                  
                  def paulMap = [
                      'name' : 'Paul',
                      'age' : 35,
                      'address' : '123 main st',
                      'list': [1,2,3]
                      ]
                      
                println("name is " + paulMap['name'])
                println("age " + paulMap.get('age'))
                println("list item " + paulMap['list'][1])
                
                paulMap.put('city','pittsburg')
                println("Has City: " + paulMap.containsKey('city'))
                println("Size is " + paulMap.size())
                println("Keys : " + paulMap.keySet())
                println("values :" + paulMap.values())
                
                paulMap.each{toye->
                    println toye.key+':'+toye.value
                            }

              }
          }
      }//
  
     stage("range"){
          steps{
              script{
                  echo "range"
                  def oneTo10 = 1..10
                  def aTOz = 'a'..'z'
                  def zTOa = 'z'..'a'
                  
                  println("one to ten " + oneTo10)
                  println("a to z " + aTOz)
                  println("z to a " + zTOa)
                  
                  println("Size " + oneTo10.size())
                  println("2nd item " + oneTo10.get(1))
                  println("Contains 11 is " + oneTo10.contains(11))
                  println("Get last " + oneTo10.getTo())
                  println("From Firset " + oneTo10.getFrom())
              }
          }
      }//
 
     stage("condition"){
          steps{
              script{
                  echo "condition"
                  def ageold = 16
                  
                  if (ageold == 5) {
                      
                      println("go to kindergarten")
                      
                  }else if((ageold > 5) && (ageold < 18)){
                      
                      println("go to grade ${ageold-5}")
                      
                  }else{
                      
                      println("go to college")
                      
                  }
                  
                  def canVote = true
                  println(canVote ?"CanVote":"cant vote")
                  
                  switch(ageold){
                      case 16: 
                          println("16 you can drive")
                          break
                      case 18:
                          println("18 you can vote")
                          break
                      default: println("have fun")
                  }
                  
                  switch(ageold){
                      case 0..6:println("baby");break
                      case 7..12:println("child");break
                      case 13..18:println("young adult");break
                      default:println("adult")
                  }
                  
              }
          }
      }// 
      
      stage("looping"){
          steps{
              script{
                  echo "looping"
                  
                  def i = 0
                  
                  while( i < 10 ){
                      if(i % 2 ){
                          i++;
                          continue
                      }
                      if(i == 8){
                          break
                      }
                      
                      println(i)
                      i++
                  }
                  
                for(i=0;i < 5; i++){
                    println(i)
                }
                
                for(j in 2..6){
                    println(j)
                }
                
                def randlist = [10,12,13,14]
                for(j in randlist){
                    println(j)
                }
                
                def custs = [
                    100 : "paul",
                    101 : "sally",
                    102 : "sue"
                    ]
                
                for(cus in custs){
                    println("${cus.value} : ${cus.key}")
                }
                
                
                
              }
          }
      }//
      
     stage("closure"){
          steps{
              script{
                  echo "closure"
                  // eg:1
                  def getfactorial = {num -> (num <= 1 ? 1: num * call(num -1))}
                  println("factorial 4 is " + getfactorial(4))
                  
                  //eg：2
                  def greeting = "Goodbye"
                  def sayGoodbye = {theName -> 
                      println("$greeting $theName")
                  }
                  sayGoodbye("derek")
                  
                  //eg:3
                  def numlist = [1,2,3,4]
                  numlist.each{println(it)}
                  
                  //eg:4
                    def custs = [
                        100 : "paul",
                        101 : "sally",
                        102 : "sue"
                    ]
                    
                    custs.each{println("$it.key : $it.value")}
                 
                 //eg:5
                 def randnum = 1..6
                 randnum.each{num-> if(num % 2 == 0) println(num)}
                  
                 //eg:6
                 def namelist = ["dong","sally","sue"]
                 def matchlist = namelist.find{item-> item == 'sue'}
                 println(matchlist)
                 
                 //eg:7
                 def num_lt = 1..6
                 def num_match = num_lt.findAll{item-> item > 4}
                 println(num_match)
                 println("any number >5 :" + num_lt.any{item-> item>5})
                 println("every number >1 :" + num_lt.every{item-> item>1})
                 println("double for collect :" + num_lt.collect{item-> item *2})
                 
                 
              }
          }
      }//
        

   }
}