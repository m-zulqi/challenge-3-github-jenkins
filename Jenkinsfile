pipeline {
  agent any

  options {
    buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
    timeout(time: 12, unit: 'HOURS')
    timestamps()
  }
  stages {
    stage("Requirements") {
      steps {
        sh('chmod +x ./algorithm.sh')
      }
    }
    stage("Build") {
      steps {
        sh("./algorithm.sh")

        archiveArtifacts allowEmptyArchive: true,
          artifacts: '*.txt',
          fingerprint: true,
          onlyIfSuccessful: true
      }
    }
  }


}
