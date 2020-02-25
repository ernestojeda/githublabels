def Git_Scm_Url = "https://github.com/venkata-lakshmi-penna/githublabels"
def SRC_GH_REPO = "Test-labels"
def TGT_GH_REPO = ["Project-2", "project-3", "project-4", "project-5"]
pipeline {
	agent any
	 stages {
	   stage('Git Checkout'){
		steps {
		checkout([$class: 'GitSCM', branches: [[name: '*/labels']], doGenerateSubmoduleConfigurations: false, userRemoteConfigs: [[url:"${Git_Scm_Url}"]]])
	}
	}
	stage('execute shell') {
		steps {
		script {
	        withCredentials([usernamePassword(credentialsId: 'githubcred', passwordVariable: 'GH_TOKEN', usernameVariable: 'GH_USER')]) {
			for (repo in TGT_GH_REPO) 
				sh "./github-copy-labels.sh $SRC_GH_REPO ${repo}"
		       }
		   }
	       }  	
	   }
      }  
}


 
