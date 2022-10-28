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
          env.FEATURE = input message: 'Please enter the feature you want to build with',
                             parameters: [string(defaultValue: '',
                                          description: '',
                                          name: 'Feature')]
        }
      }
    }
    
    stage ("Edit")
    {
      steps {
        dir("/home/lakshmi/Desktop") {
        pwd 
        ls
        echo env.FEATURE
        sed -n '/docker/p' sample.txt | head -1
        }  
    }
   }
  }
}
