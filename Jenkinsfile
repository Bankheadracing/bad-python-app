pipeline {
    agent any

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
                sh 'python3 Fetch_main.py test2.yaml'
                echo 'Deployed the application to Terminal...'
            }
        }
    }
}
