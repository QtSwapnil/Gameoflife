pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                  mail subject: 'Build Started', 
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
        stage('archive results') {
            steps {
                junit '**/surefire-reports/*.xml'
		    archiveArtifacts artifacts: '**/spring-petclinic*.jar', followSymlinks: false
            }
        }
    }
}