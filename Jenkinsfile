pipeline{
    agent any
    
    stages{
        stage('SCM'){
            steps{
                git credentialsId: 'cea56851-fd0a-44da-b67a-fee707bf6f4d',
                url: 'https://github.com/dhanu0001/tomcat-docker.git'
            }
        }
        stage('Build Application'){
            steps{
                sh 'mvn -f java-tomcat-sample-docker/pom.xml clean package'
            }
            post{
                success{
                    echo "now archiving the artificats....."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Create Tomcat image'){
            steps{
                sh "pwd"
                sh "ls -la"
                sh "docker build . -t tomcatsamplewebapp:${env.BUILD_ID}"
            }
        }
    }
}
