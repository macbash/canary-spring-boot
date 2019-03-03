node {
    stage('Checkout') {
    checkout scm
}
 stage('Artifact-Def') {
  if(env.BRANCH_NAME == 'master'){
   sh '''
   mvn versions:set -DnewVersion=1.0.1-'${env.BUILD_NUMBER}'-RELEASE
   '''
} else {
             sh '''
   mvn versions:set -DnewVersion=1.0.1-'${env.BUILD_NUMBER}'-SNAPTSHOT
   '''
}
}

    stage('Build') {
     sh 'mvn clean install'
}
 stage('Test') {
     sh 'mvn test'
}
 stage('CodeCoverage') {
     sh 'mvn sonar:sonar'
}

stage('Deploy') {
   sh '''
     mvn deploy
     
     '''
}

}
