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
			sh"git diff --name-only origin/master | while read -r line; do cp \${line} /var/jenkins_home/workspace/unicoarchivos ; done"
			}
		
		}
		stage('Publisher'){
		steps {

				class ListFilesTxt {

					public static void main(String[] args) 
					{
						String path = "/var/jenkins_home/workspace/Prueba_deploy"; 

						String files;
						File folder = new File(path);
						File[] listOfFiles = folder.listFiles(); 

						for (int i = 0; i < listOfFiles.length; i++) 
						{

							if (listOfFiles[i].isFile()) 
							{
								files = listOfFiles[i].getName();
								if (files.endsWith(".txt") || files.endsWith(".TXT"))
								{
									System.out.println(files);
								}
								 if (files.endsWith("unico.ear") || files.endsWith(".EAR"))
								{
									System.out.println(files);
								}
							}
						}
						System.out.println("Fin");
					}
				}
			}
		
		}
	}
}
