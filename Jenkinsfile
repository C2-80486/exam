pipeline {
    agent any

    stages {
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_MNSdgs-d0yWp-Fwfijuzpp43Bpo | /usr/local/bin/docker login -u ditiss80486444 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/local/bin/docker build -t ditiss80486444/labtest .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/local/bin/docker image push ditiss80486444/labtest'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/local/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/local/bin/docker service create --name myservice --replicas 5 -p 9090:9000 ditiss80486444/labtest'
            }
        }
    }
}
