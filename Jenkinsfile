pipeline {
  agent none
  stages {
    stage('Preparation') {
      parallel {
        stage('Preparation') {
          agent {
            node {
              label 'ubuntuNode'
            }

          }
          steps {
            git 'https://github.com/andyzyzy/BlueOceanDemo.git'
          }
        }

        stage('second') {
          agent any
          steps {
            sh 'echo preparation2'
          }
        }

      }
    }

    stage('build') {
      agent any
      steps {
        sh 'pwd'
        echo 'abc'
      }
    }

    stage('Test') {
      parallel {
        stage('node 1') {
          agent any
          steps {
            sh 'pwd'
            sh 'sleep 20s'
            sh 'echo hstream1'
          }
        }

        stage('node 2') {
          agent {
            label 'ubuntuNode'
          }
          steps {
            sh 'pwd'
            sh 'sleep 20s'
            sh 'echo andy good1'
            sh 'python ./test/test.py'
          }
        }

        stage('node 3') {
          steps {
            sleep 11
          }
        }

      }
    }

  }
}