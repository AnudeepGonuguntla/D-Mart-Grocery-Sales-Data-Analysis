pipeline {
    agent any

    environment {
        VENV_DIR = 'venv'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/AnudeepGonuguntla/D-Mart-Grocery-Sales-Data-Analysis.git'
            }
        }

        stage('Set Up Python Virtual Environment') {
            steps {
                sh 'python3 -m venv $VENV_DIR'
                sh '. $VENV_DIR/bin/activate'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '. $VENV_DIR/bin/activate && pip install --upgrade pip'
                sh '. $VENV_DIR/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run Analysis Script') {
            steps {
                sh '. $VENV_DIR/bin/activate && jupyter nbconvert --execute --inplace EDA_Project.ipynb'

                // Replace "analysis.py" with your actual script name
            }
        }
    }

    post {
        success {
            echo '✅ Data Analysis Completed Successfully!'
        }
        failure {
            echo '❌ Pipeline Failed. Please check console output.'
        }
    }
}
