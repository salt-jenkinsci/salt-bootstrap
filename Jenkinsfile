def notifySuccessful(String stageName) {
  slackSend (color: '#00FF00', message: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})" + "\n  Stage -- " + stageName)
}

def notifyFailed(String stageName) {
  slackSend (color: '#FF0000', message: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})" + "\n  Stage -- " + stageName)
}


pipeline {
   environment {
      STAGE1 = "shellcheck"
    }
agent { docker 'koalaman/shellcheck:v0.4.6' }    
       currentBuild.result = "SUCCESS"

stage('shellcheck') {
        //Run the shell check utility and report on the output.
         print "Running shellcheck on bootstrap script for $ghpr"
         bash '''#!/bin/bash
                 shellcheck -s sh -f checkstyle bootstrap-salt.sh | tee checkstyle.xml 
         '''
       }
}
