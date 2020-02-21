node {
    def Git_Scm_Url = "https://github.com/venkata-lakshmi-penna/githublabels" 
    def SRC_GH_USER = "venkata-lakshmi-penna" 
    def SRC_GH_REPO = "Test-labels"
    def TGT_GH_USER = "venkata-lakshmi-penna"
    def TGT_GH_REPO = ["Project-2", "project-3", "project-4", "project-5"]

     stage('Git Checkout'){
                    checkout([$class: 'GitSCM', branches: [[name: '*/labels']], doGenerateSubmoduleConfigurations: false, userRemoteConfigs: [[url:"${Git_Scm_Url}"]]])
                } 
     stage('execute shell') {
      for (repo in TGT_GH_REPO) {
         withCredentials([string(credentialsId: 'gitcred', variable: 'GH_TOKEN')]) {
	sh """
           bash github-copy-labels.sh $GH_TOKEN $SRC_GH_USER $SRC_GH_REPO $TGT_GH_USER ${repo}"""
	      }
           }
        }
 }
