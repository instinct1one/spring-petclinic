node('OP11&MVN3.6') {
    // some block
}node('OPENJDK-11') {
    stage('vcs') {
      git branch: 'main', url: 'https://github.com/instinct1one/spring-petclinic.git'
    }
    stage("build") {
        sh 'mvn package'
    }
    stage("archive results") {
        junit '**/surefire-results/*.xml'
    }
    stage("clean") {
        cleanWs cleanWhenAborted: false, cleanWhenFailure: false, cleanWhenNotBuilt: false, cleanWhenUnstable: false
    }
}