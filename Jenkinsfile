pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
       stage("create tomcat docker image"){
           steps {
               sh "pwd"
               sh "ls -a"
               sh "docker build . -t tomcatsamplewebapp:${env.BUILD_ID}"
           }
       } 
    }
}