pipeline {
    agent any
    stages{
        stage('Checkout'){
            steps{
                checkout scm
            }
        }
        stage('Build'){
            steps{
                bat"""
                if exist rmdir /s /q out
                mkdir out
                python src//hello//Example.py > out//output.txt
                echo Build_OK > artifacts.txt
                """
            }
        }
    }
    post{
        always
        {
            archiveArtifacts artifacts : 'artifacts.txt, out/**', allowEmptyArchive: false
        }
    }