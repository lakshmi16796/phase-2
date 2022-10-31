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
          line = input message: 'Please enter the feature you want to build with',
                             parameters: [string(defaultValue: '',
                                          description: '',
                                          name: 'Feature')]
        }
      }
    }
    
    stage ("Edit")
    {
      steps {
        
        script {
        dir("/home/lakshmi/Desktop") {
        sh '''#!/bin/bash
        
        pwd 
        ls
        line = $(sed -n '/docker/p' sample.txt | head -1)
        echo "$line"
       
        '''
        }  
    }
  }
   }
  }
}
