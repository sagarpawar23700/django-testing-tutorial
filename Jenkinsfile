#!/usr/bin/groovy

node {

    try {
        stage 'Checkout'
            checkout scm
            sh 'rm -rf django-testing-tutorial' 
            sh 'git clone https://github.com/sagarpawar23700/django-testing-tutorial.git'
            
            

        stage 'Test'
            sh 'python3 -m virtualenv venv'
			sh '. venv/bin/activate'
			sh 'pip3 install coverage'
			sh 'pip3 install pipenv'
			sh 'venv/bin/pipenv install --system'
			sh 'cd django-testing-tutorial'
			sh 'python manage.py runtests'
            sh 'coverage run --source='.'  manage.py test'
            sh 'coverage html' 
   
        stage 'Deploy'
            sh 'docker-compose up'

    }

    catch (err) {
 
        throw err
    }

}

