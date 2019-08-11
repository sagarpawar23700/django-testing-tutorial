#!/usr/bin/groovy

node {

        stage 'Checkout'
            checkout scm
            sh 'rm -rf venv django-testing-tutorial' 
            sh 'git clone https://github.com/sagarpawar23700/django-testing-tutorial.git'
      
            

        stage 'Test'
	    sh 'cd django-testing-tutorial'
            sh 'python3 manage.py test'
 
        stage 'Deploy'
            sh 'docker-compose up'

 

}

