pipeline{

    agent any

    stages{

        stage("Continous Download") {

            steps{
                git branch: 'main', url: 'https://github.com/Hadijah-ateh/DEVOPS-PROJECT-5.git'
            }
        }
        stage('Unit Testing'){

            steps{
                sh 'mvn test'
            }
        }
        stage('Intergration Testing'){

            steps{
                sh 'mvn verify -DskipUnitTests'
            }
        }
        stage('Statict Test Analysis'){

            steps{

                script{
                    withSonarQubeEnv(credentialsId: 'sonarqube-token'){
                        sh 'mvn clean package sonar:sonar'
                    }

                }
            }
        }
        stage('Quality Gate Analysis'){

            steps{

                script{
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonarqube-token'
                }
            }
        }
    }
}