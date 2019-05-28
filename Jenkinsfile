#!groovy
def pushProperties
def log
def tokens
def fileIncludePatterns = ''
def deploy = 0
def componentName
def componentTag
def componentAppName
def binder
def proyecto = "Unico"
def earName = "unico.ear"			//Modificar segun el nombre del ear.
def tipo = "EAR1"					//Modificar segun el tipo de artefacto en mayusculas, las opciones son: EAR - JASPER - XML - JAR.


pipeline {
	agent any
	   	environment {

		SCM_URL = "https://github.com/nazpot01/Pruebas.git"
	        SCM_CREDENTIALS = "123456789"
		SCM_BRANCH = "*/${BRANCH_NAME}"
		BRANCH_NAME= "clon-master2"
		}
		
	stages {

		stage('test') {
                steps {
                    echo "[EXEC] - Obtener código fuente desde repositorio Git"
				}
			}
		stage('copiado'){
		steps {
			sh"pwd"
			sh"git checkout */${BRANCH_NAME}"
			sh"git diff --name-only origin/master | while read -r line; do cp \${line} /var/jenkins_home/workspace/unicoarchivos ; done"
			}
		
		}
		stage('publisher'){
		steps {
			script {
			String sourceFilePath = "/var/jenkins_home/workspace/unicoarchivos/unico1.ear"
			 String destinationFilePath = "/var/jenkins_home/workspace/Prueba_deploy/unico1.ear"
			 (new AntBuilder()).copy(file: sourceFilePath, tofile: destinationFilePath)
			}
		    }
		}
	}
}
