
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
                            def vm_id = line.split(',')[0]
                            def vm_resource_group = line.split(',')[1]
                            def vm_name = vm_id.split("/")[(vm_id.split("/").size()-1)]
                            def recovery_vault=line.split(',')[2]
                            def recover_vault_group=line.split(',')[3]

                            echo "$vm_id"
                            echo "$vm_resource_group"
                            echo "$vm_name"
                            echo "$recovery_vault"
                            echo "$recover_vault_group" 

                         sh """az vm list --resource-group $vm_resource_group --output table""" 
                         sh """az backup protection enable-for-vm --resource-group $recover_vault_group --vault-name $recovery_vault  --vm ${vm_id} --policy-name EnhancedPolicy"""     
                            // Check if the line has enough columns
                            
                      }
                  }
              } 

            }
        }
    }
}
