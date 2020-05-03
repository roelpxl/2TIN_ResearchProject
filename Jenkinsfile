pipeline {
   agent any
   stages {
       stage('Cleanup') {
         steps {
            deleteDir()
            echo 'cleanup'
    }

        }
       /* stage('Fetch code') {
         steps {
            echo 'From git repository'
            git 'https://github.com/Tristan011/2TIN_ResearchProject'
         }
        } */
        stage('Build') {
         steps {
            echo 'Build test'
            sh 'composer install'
            //  //sh 'vendor/bin/parallel-lint --exclude vendor/ .' 
        
         }
        }
        stage('Test') {
         steps {
            echo 'Unit Test'
            //'tests/EmployeeTest.php'
            //sh 'vendor/bin/phpunit -c build/phpunit.xml'
            sh './vendor/bin/phpunit tests build/phpunit.xml'
         }
        }
        stage('Artifact') {
         steps {
            echo 'Artifact'
            archiveArtifacts artifacts: 'index.php', onlyIfSuccessful: true
         }
        }
        /*stage('Mysql update') {
         steps {
            echo 'Mysql update'
            sh 'mysql -u root -p Mysqllaatmebinnen1! employees /var/lib/jenkins/workspace/SNB2_First/employees.sql'
        
         }
        } */
        stage('Deploy to apache') {
         steps {
            echo 'Deploy to apache test'
            sh 'sudo cp -R /var/lib/jenkins/workspace/SNB2_First/* /var/www/html/'
        
         }
        }
        stage('Post-cleanup') {
         steps {
            echo 'Post-cleanup test'
         }
    }
       
   }
}
