pipeline {
  agent any
  stages {
	  

    stage ("Edit")
    {
      steps {
        
        script {
	 		       
	def testParam = checkBox("opt", // name
                "opt1,opt2,opt3", // values
                "opt1", //default value
                0, //visible item cnt
                "Multi-select", // description
                )

	properties([parameters([testParam])])

	node {
  	  echo "${params.opt}"
	}
	
      	}  
    }
  }
   }
  }
}
