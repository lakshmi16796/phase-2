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
        num=$(echo "$line" | grep -o -E '[0-9]+')
        echo "$num"
        
        #Enabling the mentioned feature for build in local.conf
        sed -i "$num s/#/ /" sample.txt
        cat sample.txt
        
        #Disabling the feature after build is complete in local.conf
        sed -i "$num s/ /#/1" sample.txt
        cat sample.txt
        
        '''
        }  
    }
  }
   }
  }
}
