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
        line=$(sed -n "/Docker/p" sample.txt | head -1)
        echo "$line"
        
        #extracting the line numbers 
        array=()
        array+=$(echo "$line" | grep -Eo '[0-9]{1,4}')
        echo "line number is"
        printf '%s\n' "${array[@]}"
        
        
        #Enabling the mentioned feature for build in local.conf
               
        for x in "${array[@]}"
        do
	  echo "$x"
          sed -i "$x s/#/ /" sample.txt
        done
        
        cat sample.txt
                
        '''
        }  
    }
  }
   }
  }
}
