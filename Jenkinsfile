pipeline {
  agent any
  environment{
      name="akshay"
      age="24"
  }
  parameters {
      string (name:'akshay',defaultValue:'akshay',description:'this is name of user ')
      booleanParam(name:'isMale',defaultValue:true,description:'')
      choice(name:'city',choices:['alwar','jaipur','pune'],description:'mention your city name here')
  }
  stages {
    stage('Log Ant version info') {
      steps {
        sh 'ant -version'
      }
    }
    stage('GitHub Jenkins Ant Build') {
      steps {
        git 'https://github.com/learn-devops-fast/rps-ant.git'
        sh 'ant clean compile test package war'
        echo 'hello'
        sh 'java -version'
      }
    }
    stage('Testing') {
        steps {
            echo "testing done"
            sh 'date && free -mh'
            sh 'date || free -mh'
            sh 'echo $name'
            sh 'echo $akshay'
        }
     }
    stage('Continue ?') {
        input {
            message 'should we deploy this'
            ok 'go ahead'
        }
      steps {
        echo 'can we deploy on prod'
      }
    }
    stage('Deploy on production') {
      steps {
        sh 'pwd'
        echo 'run deployment'
        script{
            if(fileExists('main/index.html')) {
                echo "index file is found"
            }
        }
      }
     }
    }
    post{
        always {
            echo 'it will run anyways'
        }
        failure {
            echo 'your job is failure'
        }
    }
  }
