pipeline {
    agent any

    tools {
        python 'Python3'  // Make sure Python is set up in Jenkins Global Tools
    }

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

        stage('Run Analysis') {
            steps {
                // Run your main Python script or Jupyter Notebook conversion
                sh '. $VENV_DIR/bin/activate && python EDA_Project.ipynb'
                // OR if using Jupyter Notebook:
                // sh '. $VENV_DIR/bin/activate && jupyter nbconvert --execute your_notebook.ipynb'
            }
        }
    }

    post {
        success {
            echo '✅ Analysis completed successfully.'
        }
        failure {
            echo '❌ Analysis failed. Check console output.'
        }
    }
}
