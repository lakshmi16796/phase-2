pipeline {
  agent any
  stages {
	  

    stage ("Edit")
    {
      steps {
        
        script {
	 		       
	env.feature = input message: 'Please enter the feature you want to build with',
                             parameters: [string(defaultValue: '',
                                          description: '',
                                          name: 'Feature')]
        echo "Entered feature is "
	echo "${env.feature}"
		
		
        dir("/home/lakshmi/Desktop") {
        sh '''#!/bin/bash
	
	echo "inside shell"
	echo "${env.feature}"
       	
        #Locating the line with mentioned feature
        line=$(sed -n "/($feature)/p" sample.txt | head -1)
        echo "$line"
	
        
        #extracting the line numbers 
        array=()
        
	n=$(echo "$line" | sed -e 's/#/,/2g' -e 's/#//1' -e 's/[a-z]//g' -e 's/[A-Z]//g') ; 
	echo "line number is"
	echo $n
	IFS="," read -a array <<< $n
	
	        	             
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
