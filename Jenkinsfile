pipeline {
  agent any
  stages {
    stage ("Prompt for input") {
      steps {
        script {
          echo "Features Options"
          echo "Docker"
          echo "Xen"
          echo "All"
          
        }
      }
    }
    
    stage ("Edit")
    {
      steps {
        
        script {
        def feature = input message: 'Please enter the feature you want to build with',
                             parameters: [string(defaultValue: '',
                                          description: '',
                                          name: 'Feature')]
        echo "Entered feature is "
        echo "$feature"
        dir("/home/lakshmi/Desktop") {
        sh '''#!/bin/bash
        
        #Locating the line with mentioned feature
        line=$(sed -n "/$feature/p" sample.txt | head -1)
        echo "$line"
	
        
        #extracting the line numbers 
        array=()
        #n=$(echo "$line" | grep -Eo '[0-9]{1,4}')
	n=$(echo "$line" | sed -e 's/#/,/2g' -e 's/#//1' -e 's/[a-z]//g' -e 's/[A-Z]//g') ; 
	echo "line number is"
	echo $n
	IFS="," read -a array <<< $n
	#echo "Number of elements in the array: ${#array[@]}"
	
	
        	             
        #Enabling the mentioned feature for build in local.conf         
        for x in "${array[@]}"
        do
	  echo "$x"
          sed -i "$x s/#/ /" sample.txt
        done        
        cat sample.txt                
        
		
	#Disabling the feature after build is complete in local.conf
        for x in "${array[@]}"
        do
	  echo "$x"
          sed -i "$x s/ /#/1" sample.txt
        done        
        cat sample.txt 
	
	'''
        }  
    }
  }
   }
  }
}
