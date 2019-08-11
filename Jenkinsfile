#!/usr/bin/groovy

node {

    try {
        stage 'Checkout'
            checkout scm
            sh 'rm -rf venv django-testing-tutorial' 
            sh 'git clone https://github.com/sagarpawar23700/django-testing-tutorial.git'
            
            

        stage 'Test'
            sh 'python3 -m virtualenv venv'
			sh 'source venv/bin/activate'
			sh 'pip3 install coverage Django'
			#sh 'venv/bin/pipenv install --system'
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

