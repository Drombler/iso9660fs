pipeline { 
    agent any  
    tools { 
        maven 'Apache Maven 3.6' 
        jdk 'Java SE 11' 
    }
    stages { 
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true clean install -DperformRelease=true' 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
    }
}