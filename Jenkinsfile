pipeline {
    agent {label 'n'}
    stages {
        stage ('SOUREODE') {
            steps {
               git url: 'https://github.com/instinct1one/spring-petclinic.git',
                branch: 'main'
            }
        }
        stage ('ARTIFATORY_CONFIG') {
            steps {
				rtMavenDeployer (
                    id: "MAVEN_DEPLOYER",
                    serverId:     "JFROG",
                    releaseRepo:  "default-libs-release-local",
                    snapshotRepo: "default-libs-snapshot-local",
                    deployArtifacts : true
                )
            }
        }
        stage ('MAVEN') {
            steps {
                rtMavenRun (
                    pom:   "pom.xml",
                    tool: "MVN",
                    goals: "clean install",
                    deployerId: "MAVEN_DEPLOYER",
                )
            }
        }
        stage ('BUILD_INFO') {
            steps {
                rtPublishBuildInfo (
                    serverId: "JFROG"
                )
            }
        }
    }
	
}