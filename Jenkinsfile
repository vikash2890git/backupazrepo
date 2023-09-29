
pipeline {
    agent any


    stages {
        stage('Check config') {
            steps {

              script {

                  // Define the path to your CSV file
                  def filePath = 'config'

                  // Read the content of the file into a list of lines
                  def fileContent = readFile(filePath).trim().split('\n')

                  withCredentials([azureServicePrincipal('c45a649c-d2e1-4c55-ac6f-e48829aa78e4')]) {
                  // Loop through each line in the file
                      sh 'az login --service-principal -u $AZURE_CLIENT_ID -p $AZURE_CLIENT_SECRET -t $AZURE_TENANT_ID'
                      for (String line : fileContent) {
                            // Split the line into columns based on the comma separator
                            def columns = line.split(',')
                            def vm_id = line.split(',')[0]
                            def resource_group = line.split(',')[1]
                            def vm_name = vm_id.split("/")[(vm_id.split("/").size()-1)]

                            echo "$vm_id"
                            echo "$resource_group"
                            echo "$vm_name" 
                         sh """az vm list --resource-group $resource_group --output table"""      
                            // Check if the line has enough columns
                            
                      }
                  }
              } 

            }
        }
    }
}
