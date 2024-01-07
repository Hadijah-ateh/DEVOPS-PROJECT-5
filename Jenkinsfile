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
    }
}