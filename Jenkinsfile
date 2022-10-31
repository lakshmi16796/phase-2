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
          feature = input message: 'Please enter the feature you want to build with',
                             parameters: [string(defaultValue: '',
                                          description: '',
                                          name: 'Feature')]
          echo "$feature"
        }
      }
    }
    
    stage ("Edit")
    {
      steps {
        
        script {
        dir("/home/lakshmi/Desktop") {
        sh '''#!/bin/bash
        echo "Entered input is"
        echo "$feature"
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
