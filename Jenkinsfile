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
	input=$(printenv feature)
	echo "your input"
	echo "$input"
	
	array=()
	IFS='+' read -ra array <<< $input
	for i in "${array[@]}"; do
  		echo "$i"
		
		line=$(sed -n "/$i/p" local.conf | head -1)
        	echo "$line"
		
		n=$(grep -rin $i | head -1 | awk '{print $1 }' | cut -d: -f 2)
		echo "Line number is"
		echo "$n"
	done
	
	'''
	}
      	}  
    }
  }
   }
  }

