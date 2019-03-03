node {
    stage('Checkout') {
    checkout scm
}
 stage('Artifact-Def') {
  if(env.BRANCH_NAME == 'master'){
   sh '''
   mvn versions:set -DnewVersion=1.0.1-'${env.BUILD_NUMBER}'-RELEASE
   '''
}
}

    stage('Build') {
  if(env.BRANCH_NAME == 'master'){
   sh '''
     mvn clean install
  '''
} else {
  sh '''
   mvn clean install -Dbuildnumber=b'${env.BUILD_NUMBER}'
  '''
}
}
 stage('Test') {
 if(env.BRANCH_NAME == 'master'){
   sh '''
     mvn test
  '''
} else {
  sh '''
   mvn test -Dbuildnumber=b'${env.BUILD_NUMBER}'
  '''
}
}

 stage('CodeCoverage') {
 if(env.BRANCH_NAME == 'master'){
   sh '''
     mvn sonar:sonar
    '''
} else {
   sh '''
   mvn sonar:sonar -Dbuildnumber=b'${env.BUILD_NUMBER}'
   '''
}
}


stage('Publish-Artifact') {
 if(env.BRANCH_NAME == 'master'){
   sh '''
     mvn deploy
    '''
} else {
   sh '''
   mvn deploy -Dbuildnumber=b'${env.BUILD_NUMBER}'
   '''
}

}
stage('Deploy') {
 if(env.BRANCH_NAME == 'master'){
   sh '''
     echo 'In-Progress'
    '''
} else {
  paramvalue="1.0.1-${env.BUILD_NUMBER}-SNAPTSHOT"
  println paramvalue
 build job: 'Dev-Release', parameters: [[$class: 'StringParameterValue', name: 'ARTIFACT_NAME', value: "1.0.1-15-SNAPTSHOT"]]
}

}

}
