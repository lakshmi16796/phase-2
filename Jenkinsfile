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
	input=${env.feature}
	echo "$input"
	
	dir("/home/lakshmi/test/local") {
        sh '''#!/bin/bash
	
	array=()
	IFS=';' read -ra array <<< "${env.feature}"
	for i in "${ADDR[@]}"; do
  		echo "$i"
	done
	
	'''
	}
      	}  
    }
  }
   }
  }

