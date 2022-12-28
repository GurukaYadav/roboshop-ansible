pipeline {
  agent {
    node {
      label 'Built-In Node'
    }
  }

  environment {
    SSH=credentials('SSH')
  }

  parameters {
    string(name: 'COMPONENT', defaultValue: '', description: 'Roboshop Component Name')
  }

  stages {

    stage(Individual-component of roboshop) {
      steps {
        sh '''
          HOST=$(echo ${COMPONENT} | tr [:lower:] [:upper:])
          ansible-playbook -i inv.roboshop roboshop.yml -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -e HOST=${HOST} -e ROLE=${COMPONENT}
        '''
      }
    }
  }
}