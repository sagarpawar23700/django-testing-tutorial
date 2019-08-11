#!/usr/bin/groovy

node {

        stage 'Checkout'
            checkout scm
           



        stage 'Test'
		sh ''' #!/bin/bash    
	        python3 -m virtualenv venv
		. venv/bin/activate
		pip install coverage
		pip install pipenv
		pipenv install --system
		coverage run --source='.'  manage.py test
		coverage html
        ''' 
        stage 'Build'
                ssh ''' #!/bin/bash
                 docker build -t druvapp:latest .
        '''           
}

