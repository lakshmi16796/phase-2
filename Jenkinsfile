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
        feature = input message: 'Please enter the feature you want to build with',
                             parameters: [string(defaultValue: '',
                                          description: '',
                                          name: 'Feature')]
        echo "$feature"
        dir("/home/lakshmi/Desktop") {
        sh '''#!/bin/bash
        
        line=$(sed -n "/$feature/p" sample.txt | head -1)
        echo "$line"
        num=$(echo "$line" | grep -o -E '[0-9]+')
        echo "$num"
        sed -i "$num s/#/ /" sample.txt
        '''
        }  
    }
  }
   }
  }
}
