#!/usr/bin/groovy

node {

        stage 'Checkout'
            checkout scm
            sh 'rm -rf venv django-testing-tutorial' 
            sh 'git clone https://github.com/sagarpawar23700/django-testing-tutorial.git'
      
            


        stage 'Test'
            sh 'python3 -m virtualenv venv'
            sh 'source venv/bin/activate'
	    sh 'cd django-testing-tutorial'
            sh 'pip3 install coverage pipenv'
	    sh '~/venv/bin/pipenv install --system'
	    sh 'python manage.py runtests'
            sh 'coverage run --source='.'  manage.py test'
            sh 'coverage html' 


        stage 'Deploy'
            sh 'sudo docker rmi druvaapp:v1'
            sh 'sudo docker build -t druvaapp:v1 .' 
            sh 'sudo docker stop druva_testapp'
            sh 'sudo docker run -d -p 8000:8000 --name druva_testapp druvaapp:v1' 


 

}

