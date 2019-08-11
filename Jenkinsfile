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
                rm -rf ../DRUVA_APP_COVRAGE_REPORT/htmlcov
		coverage run --source='.'  --omit='venv'  manage.py test
                coverage report
		coverage html
                mv htmlcov ../DRUVA_APP_COVRAGE_REPORT/
        ''' 
        stage 'Build'
                sh ''' #!/bin/bash
               
	        docker tag  druvapp:latest druvapp:"$BUILD_NUMBER"
                docker build -t druvapp:latest .
		docker stop druvapp 
		docker rename druvapp druvapp_"$BUILD_NUMBER"
	        docker run -d -p 8000:8000 --name druvapp druvapp:latest 	
           
        '''
}

