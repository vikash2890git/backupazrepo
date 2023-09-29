
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

                  // Define the index of the column you want to extract (0-based index)
                  def columnIndex = 0  // Change this to the desired column index (e.g., 0 for the first column, 1 for the second column, etc.)
                  echo "$columnIndex"
                  // Initialize a list to store the values from the specified column
                  def columnValues = []

                  // Loop through each line in the file
                  for (String line : fileContent) {
                        // Split the line into columns based on the comma separator
                        def columns = line.split(',')
                        def vm_name = line.split(',')[0]
                        def resource_group = line.split(',')[1]

                        echo "$vm_name"
                        echo "$resource_group"      
                        // Check if the line has enough columns
                        
                  }
              } 
            }
        }
    }
}
