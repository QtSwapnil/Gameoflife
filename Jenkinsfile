pipeline {
    agent { label 'OPENjdk' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/GitpracticerepoSwapnil/spring-petclinic.git',
                    branch: 'main' 
            }
        }
        stage('build') {
   		agent { label 'OPENjdk' }
            steps {
                sh '/usr/share/maven/bin/mvn package' 
            }
        }
        stage('archive') {
            steps {
                junit '**/surefire-reports/*.xml'
            }        
        }
        }
    }
