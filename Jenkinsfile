pipeline{
    agent{
        label{
            label "slave1"
            customWorkspace "/mnt/slave-2"
        }
    }
    stages{
        stage("one"){
            steps{
                sh "sudo yum install httpd -y"
            }
        }
        stage("two"){
            steps{
                sh "sudo service httpd start"
                sh "sudo cp -r index.html /var/www/html/"
            }
        }
    }
}
