pipeline {
    agent any
    stages {
        stage("Copy file to Docker server") {
            steps {
                // แก้ตรง team33-neogym ให้เป็นชื่อเดียวกับ pipeline job/item ที่สร้างใน jenkins
                sh "scp -r /var/lib/jenkins/workspace/66022916/* root@43.208.25.201:~/66022916"
            }
        }

        stage("Build Docker Image") {
            steps {
                // path yaml files
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66022916/playbooks/build.yaml'
            }
        }

        stage("Create Docker Container") {
            steps {
                // path yaml files
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66022916/playbooks/deploy.yaml'
            }
        }
    }
}
