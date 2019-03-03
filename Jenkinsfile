node {
    stage('Checkout') {
    checkout scm
}
 stage('Artifact-Def') {
   sh '''
   mvn versions:set -DnewVersion=1.0.1-'${env.BUILD_NUMBER}'-RELEASE
   '''
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
