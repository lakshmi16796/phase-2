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
	

	
	dir("/home/lakshmi/dell_pods/poky/build/conf")  {
        sh '''#!/bin/bash
	input=$(printenv feature)
	echo "your input"
	echo "$input"
	
	array=()
	IFS='+, ' read -ra array <<< $input
	for i in "${array[@]}"; do
  		echo "$i"
		
		line=$(sed -n "/$i/p" local.conf | head -1)
        	echo "$line"
		
		test=$(grep -rn $i)
		echo "testing"
		echo "$test"
		
		n=$(grep -rn $i | head -1 | awk '{print $1 }' | cut -d: -f 2)
		echo "Line number is"
		echo "$n"
		
		lines=$(grep -rn $i | head -1 | awk '{print $1}' | cut -d# -f 2)
		echo "Number of lines to edit is"
		echo "$lines"
		
		#Enabling the mentioned feature for build in local.conf 
		sum=$n
		for (( x=1 ; x<=$lines ; x++ )); 
		do
			echo "iterator is"	
	  		echo "$x"
			sum=$(($sum + 1))
			echo "$sum"
    			sed -i "$sum s/#//" local.conf
		
		done
	done
	
	'''
	}
      	}  
    }
  }
   }
  }

