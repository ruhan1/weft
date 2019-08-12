pipeline {
   agent { label 'maven' }
   stages {
      stage('Build') {
         steps {
            sh 'printenv'
            script {
               if ( env.CHANGE_ID != null ) { // Pull request
                  sh 'mvn -B -V clean verify -Prun-its -Pci'
               } else {
                  sh 'echo "Merge..."'
                  sh 'mvn -B -V clean deploy'
               }
            }
         }
      }
   }
}