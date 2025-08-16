# Shared Libraries

In Jenkins, a shared library is a way to store commonly used code(reusable code), such as scripts or functions, that can be used by different 
Jenkins pipelines. 

Instead of writing the same code again and again in multiple pipelines, you can create a shared library and use it in all the pipelines
that need it. This can make your code more organized and easier to maintain. 

Think of it like a library of books, Instead of buying the same book over and over again, you can borrow it from the library whenever you need it.

## Advantages

- Standarization of Pipelines
- Reduce duplication of code
- Easy onboarding of new applications, projects or teams
- One place to fix issues with the shared or common code
- Code Maintainence 
- Reduce the risk of errors

    ![Screenshot 2023-05-02 at 9 47 24 PM](https://user-images.githubusercontent.com/43399466/235724851-90a5cad6-ac0d-428b-9944-93fffea55180.png)


## How it is used.!?

As shared libraries are divided into 3 topics:

```bash
    shared 
    library
        ├── src/
        ├── resources/
        └── vars/

# src/ and resources/ are high-level topics, will discuss this later.
```

≫ Create a `vars/` folder inside the GitHub repository.

≫ Inside this folder you can create `n` no. of shared library files with `.groovy` extension as used in Jenkins pipeline scripts and file name should be in camel case.

≫ Inside the groovy file, there is a function `call()` , which is called  by the pipelines and it is a fixed syntax for all the shared libraries in the pipelines scripts.

Example: `helloWorld.groovy`
    
```groovy
def call(){
    sh 'echo Hi from DevOps Team, this is Shared Library Example.'
}
```

## Configuring the shared libraries in Jenkins:

To configure the share libraries follow the path:

```
Jenkins
    └──> Manage Jenkins
            └──> System
                    └──> Global Trusted Pipeline Libraries
Save & exit
```

Example: pipeline script

```groovy
Pipeline{
    agent any
    stages{
        stage('Greentings'){
            steps{
                # if this is repetitive task, you can add it into a shared library.

                echo 'echo Hi from DevOps Team, this is Shared Library Example.'
            }
        }
    }
}
```

With Shared Library
```groovy
@Library("library-name") _
Pipeline{
    agent any
    stages{
        stage('Greentings'){
            steps{
                # Shared library
                # name of the file inside the vars/
                
                helloWorld()  
            }
        }
    }
}
```

