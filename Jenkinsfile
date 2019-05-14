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
		SCM_BRANCH = "*/${BRANCH_NAME}"
		}

   stages {
	
		stage('GET_CODE_MASTER') {
            steps {
                step([$class: 'WsCleanup'])
                echo "[EXEC] - Obtener código fuente desde repositorio Git"
                checkout([
                        $class                           : 'GitSCM',
                        branches                         : [
                                [name: "*/master"]
                        ],
                        doGenerateSubmoduleConfigurations: false,
                        extensions                       : [],
                        submoduleCfg                     : [],
                        userRemoteConfigs                : [
                                [credentialsId: "${SCM_CREDENTIALS}", url: "${SCM_URL}"]
                        ]
                ])
			}
		}

	
		stage('GET_CODE_BRANCH') {
            steps {
                step([$class: 'WsCleanup'])
                echo "[EXEC] - Obtener código fuente desde repositorio Git"
                checkout([
                        $class                           : 'GitSCM',
                        branches                         : [
                                [name: "*/clon-master2"]
                        ],
                        doGenerateSubmoduleConfigurations: false,
                        extensions                       : [],
                        submoduleCfg                     : [],
                        userRemoteConfigs                : [
                                [credentialsId: "${SCM_CREDENTIALS}", url: "${SCM_URL}"]
                        ]
                ])

			}
		}
	}
}
