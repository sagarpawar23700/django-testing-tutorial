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
                sh ''' #!/bin/bash
               
	        docker -tag  druvapp:latest druvapp:":$BUILD_NUMBER"
                docker build -t druvapp:latest .
		docker stop druvapp 
		docker druvapp druvapp_":$BUILD_NUMBER"
	        docker run -d -p 8000:8000 --name druvapp druvapp:latest 	
           
        '''
}

