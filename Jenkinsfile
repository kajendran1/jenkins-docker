pipeline{
  agent 
  [
    docker { image 'kaj14/my-app-1.0' }
    ]
  stages{
    stage('checkout'){
          steps{
            git branch: 'main', url: 'https://github.com/kajendran1/jenkins-docker.git'
          }
       }
 
    stage('Build'){
          steps{
            sh 'mvn clean install'
          }
       }
   stage('Docker Image') {
            steps {
                script {
                  sh 'docker build -t kaj14/my-app-1.0'
                }
            }
     }
    stage('deploy docker image'){
      steps {
        script {
          withCredentials([usernameColonPassword(credentialsId: 'kajendran1', variable: 'dockerpawd')]) {
    sh 'docker login -u kajendran1 -p ${dockerpawd}'
}
          sh 'docker push kajendran1/my-app-1.0 .'
        }
      }
    }
}
}
