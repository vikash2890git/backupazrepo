
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


                  // Loop through each line in the file
                  for (String line : fileContent) {
                        // Split the line into columns based on the comma separator
                        def columns = line.split(',')
                        def vm_id = line.split(',')[0]
                        def resource_group = line.split(',')[1]
                        def vm_name = vm_id.split("/")[(vm_id.split("/").size()-1)]

                        echo "$vm_id"
                        echo "$resource_group"
                        echo "$vm_name"      
                        // Check if the line has enough columns
                        
                  }
              } 
            }
        }
    }
}
