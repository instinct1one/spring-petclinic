node('OPENJDK-11') {
    stage('vcs') {
      git branch: 'main', url: 'https://github.com/instinct1one/spring-petclinic.git'
    }
    stage("build") {
        sh 'mvn package'
    }
    stage("archive results") {
        junit '**/surefire-reports/*.xml'
    }
    stage("clean") {
        cleanWs cleanWhenAborted: false, cleanWhenFailure: false, cleanWhenNotBuilt: false, cleanWhenUnstable: false
    }
}
