pipeline{
    agent any
    environment{
        PATH="/opt/maven/bin:$PATH"
    }

    stages{
        stage("build"){
            stpes{
                sh "mvn clean deploy"
            }
        }
        stage("SonarQube Analysis"){
            environment{
                scannerHome= tool "saidemy-sonar-scanner"
            }
            steps{
                withSonarQubeEnv("saidemy-sonarqube-server"){
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}

