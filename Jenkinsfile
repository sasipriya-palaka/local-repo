pipeline {
    agent any
    stages {
        stage('checkout'){
            steps{
                cleanWs()
                echo 'checking out remote rep'
                git changelog: false, credentialsId: 'git', poll:false, url: https://github.com/sasipriya-palaka/local-repo.git
            }
        }
        stage('build'){
            steps {
                echo 'build and package the artifact'
                sh """
                ls -ltr 
                which mvn 
                mvn clean package
                """
            }
        }
        stage('deploy') {
            steps {
                echo 'Build and package the artifact'
                sh """
                echo $WORKSPACE
                cp -rp $WORKSPACE/target/hello-world-maven.war /opt/tomcat9/webapps
                """

            }
        }
    }
}