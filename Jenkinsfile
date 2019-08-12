pipeline {
   agent { label 'maven' }
   stages {
      stage('Prepare') {
         steps {
            sh 'printenv'
         }
      }
      stage('Build') {
         when {
            expression { env.CHANGE_ID != null } // Pull request
         }
         steps {
            sh 'mvn -B -V clean verify -Prun-its -Pci'
         }
      }
      stage('Deploy') {
         when {
            expression { env.BUILD_ID != null } // Merge
         }
         steps {
            sh 'mvn -B -V clean deploy'
         }
      }
   }
}