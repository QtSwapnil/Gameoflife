pipeline {
    agent any
    triggers {
        
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                  mail subject: "Build Started for Jenkins JOB $env.JOB_NAME", 
                  body: 'Build Started', 
                  to: 'qtdevops@gmail.com' 
                git branch: 'main', url: 'https://github.com/GitpracticerepoSwapnil/spring-petclinic.git'
            }

        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }
    }
    	    post {
        always {
            echo 'Job completed'
            mail subject: 'Build Completed', 
                  body: 'Build Completed', 
                  to: 'qtdevops@gmail.com'
        }
        failure {
            mail subject: 'Build Failed', 
                  body: 'Build Failed', 
                  to: 'qtdevops@gmail.com' 
        }
        success {
            mail subject: "Build Success", 
                  body: "Build Success for $env.BUILD_DISPLAY_NAME", 
                  to: 'qtdevops@gmail.com'
                  
            junit '**/surefire-reports/*.xml'
        }

    }
}
