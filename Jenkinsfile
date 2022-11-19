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
		
	IFS='+' read -ra ADDR <<< "$input"
	for i in "${ADDR[@]}"; do
  		echo "$i"
	done
      	}  
    }
  }
   }
  }

