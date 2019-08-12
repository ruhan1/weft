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
      stage('Merge') {
         when {
             branch 'master-ci-test'
         }
         steps {
            sh 'echo "This is to merge to master-ci-test............"'
            sh 'cat /home/jenkins/.m2/settings.xml'
         }
      }
   }
}