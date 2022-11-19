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
      	}  
    }
  }
   }
  }

