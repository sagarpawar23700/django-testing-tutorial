#!/usr/bin/groovy

node {

        stage 'Checkout'
            checkout scm
            sh 'rm -rf venv ' 
      
            


        stage 'Test'
            sh 'python3 -m virtualenv venv'
            sh 'source venv/bin/activate'
	   
            sh 'venv/bin/pip install coverage pipenv'
	    sh 'venv/bin/pipenv install --system'
	    sh 'python manage.py test'
            sh 'venv/bin/coverage run --source='.'  manage.py test'
            sh 'venv/bin/coverage html' 


        stage 'Deploy'
            sh 'sudo docker rmi druvaapp:v1'
            sh 'sudo docker build -t druvaapp:v1 .' 
            sh 'sudo docker stop druva_testapp'
            sh 'sudo docker run -d -p 8000:8000 --name druva_testapp druvaapp:v1' 


 

}

