pipeline {
  //agent { docker { image 'python:3.9-bullseye' } }
  agent any
    environment {
      // The following variable is required for a Semgrep App-connected scan:
      SEMGREP_APP_TOKEN = credentials('SEMGREP_APP_TOKEN')

      // Uncomment the following line to scan changed 
      // files in PRs or MRs (diff-aware scanning): 
      // SEMGREP_BASELINE_REF = "main"

      // Troubleshooting:

      // Uncomment the following lines if Semgrep App > Findings Page does not create links
      // to the code that generated a finding or if you are not receiving PR or MR comments.
      // SEMGREP_JOB_URL = "${BUILD_URL}"
      // SEMGREP_COMMIT = "${GIT_COMMIT}"
      // SEMGREP_BRANCH = "${GIT_BRANCH}"
      // SEMGREP_REPO_NAME = env.GIT_URL.replaceFirst(/^https:\/\/github.com\/(.*).git$/, '$1')
      // SEMGREP_REPO_URL = env.GIT_URL.replaceFirst(/^(.*).git$/,'$1')
      // SEMGREP_PR_ID = "${env.CHANGE_ID}"
    }
    stages {
      stage('Semgrep-Scan') {
        steps {
          sh 'echo $PATH'
          sh 'echo $SEMGREP_APP_TOKEN'
          sh 'echo ${GIT_COMMIT}'
          //sh 'export PATH=$PATH:$HOME/.local/bin'
          sh 'pip3 install semgrep'
          sh 'semgrep scan --config p/java'
      }
    }
  }
}
