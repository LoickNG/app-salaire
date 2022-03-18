node{
    stage('Clone git') {
        checkout scm
    }
    stage('Prerequis'){
        sh apk add ansible sshpass
        sh echo '172.30.126.234 app-salaire.moguidbe.form' > /etc/hosts
        sh rm -rf /root/.ssh
        sh ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa
        sh sshpass -p 'centos' ssh-copy-id -o stricthostkeychecking=no root@app-salaire.moguidbe.form
    }
    stage('Ansible') {
      ansiblePlaybook (
          colorized: true,
          playbook: 'playbook.yaml',
