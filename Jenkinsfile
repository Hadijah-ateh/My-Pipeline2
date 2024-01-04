pipeline{

    agent any

    stages{

        stage('Continous Download') {

            steps{
                git branch: 'main', url: 'https://github.com/Hadijah-ateh/My-Pipeline2.git'
            }
        }
        stage("Intergration Testing"){

            steps{
                sh 'mvn verify -DskipUnitests'
            }
        }
        stage("Unit Testing"){

            steps{
                sh 'mvn test'
            }
        }
        stage("Continous Build"){

            steps{
                sh 'mvn clean install git'
            }
        }
        stage("Static Test Analysis"){

            steps{

                script{
                    withSonarQubeEnv(credentialsId: 'sonarqube-token')
                }
            }
        }
    }
}