pipeline {
    agent any
    tools {
        maven "Maven_3.9.6"
    }

    stages {
        stage('BUILD') {
            steps {
                // Get some code from a GitHub repository
                checkout scm

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            
        }
        stage('DEPLOY') {
            steps {
                checkout scm
                sh "mvn -Dmaven.test.failure.ignore=true -s settings.xml clean deploy"
            }
        }
        // stage('SonarQube Analysis') {
        //     steps {
        //       withSonarQubeEnv('sonar') {
        //           sh "mvn clean verify sonar:sonar -Dsonar.projectKey=myapp"
        //       }
        //     }
        // }
    }
}