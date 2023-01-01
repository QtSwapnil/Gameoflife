pipeline {
    agent  { label 'OPENjdk' }
    triggers {

        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
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