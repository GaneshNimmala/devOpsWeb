pipeline{
    agent any
    tools{
        maven 'MAVEN_HOME'
    }
    stages{
        stage ('Build'){
            steps{
                bat 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                deploy adapters: [tomcat9(credentialsId: '2673d1fd-d171-4121-8218-d277231b1394', path: '', url: 'http://localhost:8086/')], contextPath: null, war: '**/*.war'
                echo "Deployment"
            }
        }
    }
}
