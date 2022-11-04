pipeline {
  agent any
  stages {
	  
	  
    environment{
          branch1 = 'Docker'
          branch2 = 'Xen'
          branch3 = 'X11'
        }

    
    stage ("Edit")
    {
      steps {
        
        script {
		
 	
	       
	env.FEATURE = input message: 'Please enter the feature you want to build with',
                             parameters: [choice(name: 'Feature entered', choices: "${branch1}\n${branch2}\n${branch3}", description: 'Enter the feature name')]
        echo "Entered feature is "
		echo "${FEATURE}"
		
		
        dir("/home/lakshmi/Desktop") {
        sh '''#!/bin/bash
	
	echo "inside shell"
	echo "${FEATURE}"
       	
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
