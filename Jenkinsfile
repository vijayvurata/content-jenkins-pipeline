pipeline {
   agent {
     label 'slave'
   }
   stages {
      stage('build') {
          steps {
            sh 'javac -d . src/*.java'
            sh 'echo Main-Class: Rectangulator > MANIFEST.MF'
            sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
          }
      }
      stage('run') {
          steps {
             sh 'java -jar rectangle.jar 7 9'
          }
      }
   }
   post {
      success {
          archiveArtifacts artifacts: '/var/lib/jenkins/workspace/arts/rectangle.jar', fingerprint: true
      }
   }
}

