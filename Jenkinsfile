pipeline {
   agent { label 'maven' }
   stages {
      stage('Build') {
         when {
             expression { env.CHANGE_ID != null }  // Pull request
         }
         steps {
            sh 'printenv'
            sh 'mvn -DskipTests -B clean verify'
         }
      }
   }
}