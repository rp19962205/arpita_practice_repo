pipeline {
    agent {
        node {
            label 'built-in'
            customWorkspace '/mnt/slave1'
        }
    }

    stages {
        stage("one") {
            steps {
                sh "sudo yum install httpd -y"
            }
        }

        stage("two") {
            steps {
                sh "sudo service httpd start"
                sh "sudo cp -r index.html /var/www/html/"
            }
        }
    }
}
