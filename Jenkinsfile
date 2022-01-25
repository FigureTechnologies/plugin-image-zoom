@Library('jenkins-pipeline') _
import com.figure.Common

def common
pipeline {
    agent any

    stages {
        stage('Stage Checkout') {
            steps {
                script {
                    common = new Common(this)
                }
                gitCheckout()
            }
        }
        stage('Npm Install') {
            steps {
                npmInstall()
            }
        }
        stage('Npm Publish') {
            steps {
                script {
                    if (env.BRANCH_NAME == "master") {
                        npmPublish()
                    }
                }
            }
        }        
    }
    post {
        always {
            script {
                rmrf('lib', 'node_modules')
            }
        }
    }
}