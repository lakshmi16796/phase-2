pipeline {
  agent any
  stages 
{  
    stage ("Edit")
    {
	    
      steps {	 
	      
	 script
         {
        		    
	    env.feature = input message: "Please select a Feature for build" ,   
	                        parameters: [
		   		extendedChoice( defaultValue: 'Docker', description: '', descriptionPropertyValue: 'Docke,Xen,QT', multiSelectDelimiter: ',', 
	     			name: 'feature', quoteValue: false, saveJSONParameterToFile: false, type: 'PT_CHECKBOX', value: 'Docker,Xen,QT', visibleItemCount: 5)
               		        ]
	    echo "Selected feature is ${feature}"
		 
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
		
		#line=$(sed -n "/$i/p" local.conf | head -1)
        	#echo "$line"
		
		n=$(grep -rin $i local.conf | head -1 | awk '{print $1 }' | cut -d: -f 1)
		test=$(grep -rin $i local.conf | head -1)
		echo "test"
		echo "$test"
		echo "Line number is"
		echo "$n"
		
		lines=$(grep -rin $i local.conf | head -1 | awk '{print $1}' | cut -d# -f 2)
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
	
	cd /home/lakshmi/dell_pods/poky
	pwd
	source oe-init-build-env
	pwd
	#rm -rf bitbake.lock
	
	
	#bitbake -c clean core-image-pods
	bitbake core-image-pods

        '''
	}
      	}  
    }
  }
   }
  }

