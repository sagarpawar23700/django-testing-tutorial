#!/usr/bin/groovy

node {

        stage 'Checkout'
            checkout scm
            sh 'rm -rf venv django-testing-tutorial' 
            sh 'git clone https://github.com/sagarpawar23700/django-testing-tutorial.git'
      
            


        stage 'Test'
            sh 'python3 -m virtualenv venv'
            sh 'source venv/bin/activate'
	    sh 'pip3 install coverage pipenv'
	    sh 'cd django-testing-tutorial'
	    sh 'pipenv install --system'
	    sh 'python manage.py runtests'
            sh 'coverage run --source='.'  manage.py test'
            sh 'coverage html' 


        stage 'Deploy'
            sh 'sudo docker-compose up'

 

}

