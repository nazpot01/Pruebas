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
def branch_name = "clon-master2"
def proyecto = "Unico"
def earName = "unico.ear"			//Modificar segun el nombre del ear.
def tipo = "EAR1"					//Modificar segun el tipo de artefacto en mayusculas, las opciones son: EAR - JASPER - XML - JAR.
									//Escoger las siguientes opciones para compilar EAR:	EAR1 = unico.ear
											//	EAR2 = UnicoAxis.ear
											//	EAR3 = AdminWeb.ear
											//	EAR4 = AdminSAT.ear
											//	EAR5 = InfoPro.ear
											//	EAR6 = EjecucionComandosWeb.ear
											//	EAR7 = bea-proxy.ear
pipeline {
	agent any
	   	environment {

		SCM_URL = "https://github.com/nazpot01/Pruebas.git"
	        SCM_CREDENTIALS = "123456789"
		SCM_BRANCH = "*/${branch_name}"
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
			sh"git checkout origin/clon-master2"
			sh"git diff --name-only origin/master | echo $1"
			}
		
		}
	}
}
