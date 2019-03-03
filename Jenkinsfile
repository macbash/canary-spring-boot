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


}
