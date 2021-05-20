pipeline{
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }
  }
  stages {
    stage('Build'){
      steps{
        sh 'mvn -B -DskipTests clean package'
      }
     }
    stage('Test'){
      steps{
        sh 'mvn test'
      }
      
  }
     stage("build & SonarQube analysis") {
            steps {
              withSonarQubeEnv('SonarQube') {
                sh 'mvn sonar:sonar'
            }
        }
    }
  }
}