node {
    stage('Checkout') {
    checkout scm
}
    stage('Build') {
     sh 'mvn clean install test'
}

 stage('CodeCoverage') {
     sh 'mvn sonar:sonar'
}

stage('Deploy') {
   sh 'mvn deploy -Dbuildnumber="-${env.BUILD_NUMBER}-SNAPSHOT"'
}

}
