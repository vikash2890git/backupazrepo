
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
                  def columnIndex = 1  // Change this to the desired column index (e.g., 0 for the first column, 1 for the second column, etc.)
                  echo "$columnIndex"
                  // Initialize a list to store the values from the specified column
                  def columnValues = []

                  // Loop through each line in the file
                  fileContent.each { line ->
                        // Split the line into columns based on the comma separator
                        def columns = line.split(',')
                        
                        // Check if the line has enough columns
                        if (columnIndex < columns.size()) {
                            // Extract the value from the specified column and add it to the list
                            columnValues.add(columns[columnIndex].trim())
                        }
                    }

                    // Print the values from the specified column
                    columnValues.each { value ->
                        echo "Value from column $columnIndex: $value"
              }
            } 
          }
        }
    }
}
