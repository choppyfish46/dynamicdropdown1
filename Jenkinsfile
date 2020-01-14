stage('list files in directory') {
            
        checkout scm
            dir('environments/dev'){
                   sh 'for f in *.tfvars;  do echo ${f}; done;'
                   sh 'for i in $(ls -d */); do echo ${i}; done'
                   sh 'find . -maxdepth 1 -type d > list_of_files.txt'
                   sh 'cat list_of_files.txt'
                   sh 'git branch -r | awk \'{print $1}\' ORS=\'\\n\' >branches.txt'
                   liste = readFile 'branches.txt'
                   list1 = readFile 'list_of_files.txt'
                   echo "please click on the link here to chose the branch to build"
                   env.BRANCH_SCOPE = input message: 'Please choose the branch to build ', ok: 'Validate!',
                   parameters: [choice(name: 'BRANCH_NAME', choices: "${list1}", description: 'Branch to build?')]         
 
                  
             }
               
            }
