pipeline {
  agent any

  environment {
    // The following variable is required for a Semgrep AppSec Platform-connected scan:
    SEMGREP_APP_TOKEN = credentials('SEMGREP_APP_TOKEN')

    // Uncomment the following line to scan changed
    // files in PRs or MRs (diff-aware scanning):
    // SEMGREP_BASELINE_REF = "main"

    // Troubleshooting:

    // Uncomment the following lines if Semgrep AppSec Platform > Findings Page does not create links
    // to the code that generated a finding or if you are not receiving PR or MR comments.
    // SEMGREP_JOB_URL = "${BUILD_URL}"
    // SEMGREP_COMMIT = "${GIT_COMMIT}"
    // SEMGREP_BRANCH = "${GIT_BRANCH}"
    // SEMGREP_REPO_NAME = env.GIT_URL.replaceFirst(/^https:\/\/github.com\/(.*).git$/, '$1')
    // SEMGREP_REPO_URL = env.GIT_URL.replaceFirst(/^(.*).git$/,'$1')
    // SEMGREP_PR_ID = "${env.CHANGE_ID}"
  }

  stages {
    stage('Build') {
      steps {
        echo 'Starting the build process...'

        sh '#!/bin/bash'
        sh 'python3 -m venv venv' // Create a virtual environment
        sh 'pip freeze > requirements.txt'
        sh '. ./venv/bin/activate && pip install -r requirements.txt' // Activate and install

        echo 'Build process complete...'
      }
    }
    stage('Test') {
      steps {
        echo 'Running tests on application...'
        sh '#!/bin/bash'
        sh 'python3 -m venv venv'
        sh '. ./venv/bin/activate'

        echo 'Tests completed on application...'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying the application...'

        echo 'Deployed the application to Terminal...'
      }
    }
    stage('Semgrep-Scan') {
      steps {
        echo 'Semgrep scan process intiated'
        sh 'pip3 install semgrep'
        sh 'semgrep ci'
        echo 'Semgrep scan process complete...'
      }
    }
  }
}
