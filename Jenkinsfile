pipeline {
    agent any
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/GitpracticerepoSwapnil/spring-petclinic.git',
                    branch: 'main' 
            }
        }
        stage('build') {
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
