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
		
        dir("/home/lakshmi/test/local") {
        sh '''#!/bin/bash
	
	echo "inside shell"
	#echo "${env.feature}"
	input=$(printenv feature)
	echo "your input"
	echo "$input"
       	
        #Locating the line with mentioned feature
        line=$(sed -n "/$input/p" local.conf | head -1)
        echo "$line"
	
	'''
	
      	}  
    }
  }
   }
  }
}
