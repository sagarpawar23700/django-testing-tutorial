#!/usr/bin/groovy

node {

        stage 'Checkout'
            checkout scm
           



        stage 'Test'
		    
        
            sh 'docker build -t druvaapp_test .'
            sh 'docker stop druva_testapp'
            sh 'docker run -d -v "$PWD/htmlcov:/code  -p 8000:8000 --name druva_testapp druvaapp_test'




}
