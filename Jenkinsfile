pipeline{
    agent any
    
    tools {
         maven 'maven'
//          jdk 'java'
    }

    stages{
        stage('checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github access', url: 'https://github.com/sreenivas449/java-hello-world-with-maven.git']]])
            }
        }
        stage('build'){
            steps{
               sh 'mvn install'
            }
        }
        stage('analysis'){
            withSonarQubeEnv('SonarQube'){
                sh 'mvn -Psonar -Dsonar.sourceEncoding=UTF-8 org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
            }
        }
    }
}
