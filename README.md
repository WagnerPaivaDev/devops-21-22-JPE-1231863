
# devops-21-22-JPE-1231863

# Class Assignment 1

## Introduction

The objective of this class assignment was to create and  use or personal repositories and use a basic spring application to introduce new features and introduce the concept of branches and merging. Although the features are simple, 
the goal is to 
understand the process of managing a repository, including its commits, creating a branch, adding new features and merging the branch back into the main branch.
The final result of the assignment can be found [here]git@github.com:WagnerPaivaDev/devops-21-22-JPE-1231863.git

## Getting Started

The first step is to clone [this repository](https://github.com/spring-guides/tut-react-and-spring-data-rest) to your local machine as it will serve as the basis for the task. The only module needed for this assignment  is _basic_, 
the other ones are not required and therefore can be deleted.
The rest of the assignment can be done by opening a bash terminal and running the following commands:

1. Navigate to the project directory (assuming the Tutorial React.js and Spring Data REST Application is already locally available):
   ```bash
   cd path/to/TutorialReactSpringDataREST
   ```
- command cd changes the current directory

2. Copy the application into a new CA1 folder:
   ```bash
   cp -r . ../CA1
   cd ../CA1
   ```

3. Initialize the Git repository (if not already a Git repository):
   ```bash
   git init
   ```
    - adds a ".git" directory to the current directory (the added directory contains alal the information required for the repository work process)

4. Add all files to the staging area:
   ```bash
   git add .
   ```
    - before being ready to be commited and then pushed to the remote repository, changes must be added to a staging area, covered by this command. The "." notation indicates that ALL the unstaged files in the repository directory 
should be staged.

5. Commit the added files:
   ```bash
   git commit -m "Initial commit with the Tutorial application"
   ```
    - creates a new commit, containing the current contents of the index (the staged changes to the files in the repository) and the given log message (after "-m") describing the changes.

6. Push the commit to the remote repository:
   ```bash
   git remote add origin <repository-URL>
   git push -u origin master
   ```
    - the first step is only necessary if the local repository is not yet linked to the remote one, as it is its function.
    - The second step  uploads local repository content to the remote repository location.

7. Add a tag to the commit:
   ```bash
   mv CA1  CA1.V1
	git commit -m #2	
   git push
   ```
    - the first step creates a new tag, with the name "V1"
    - the second step uploads the tag to the remote repository

### Implementing Changes
#### Adding the job years field

This first section is done on the main branch, and the goal is to add a new field to the application, which will be the number of years the user has been working in the current job. The steps to do so are:

1. Add the new field to the _Employee_ class:
   ```java
   private int jobYears;
   ```
   
2. Add the new field to the _Employee_ class constructor:
   ```java
    public Employee(String name, String role, int jobYears) {
         this.name = name;
         this.role = role;
         this.jobYears = jobYears;
    }
    ```
   
3. Add validations to the _Employee_ class constructor so that the parameters are always valid:
   ```java
   public Employee(String firstName, String lastName, String description, int jobYears) throws InstantiationException {
		 if(firstName == null || lastName == null || description == null || email == null || jobYears < 0 || firstName.isEmpty() || lastName.isEmpty() || description.isEmpty() || email.isEmpty())
			throw new InstantiationException("Please enter a valid first name, last name, description and job years.");
		 this.firstName = firstName;
		 this.lastName = lastName;
		 this.description = description;
		 this.jobYears = jobYears;
	}
   ```
4. Testes para a classe _Employee

    @Test
    void createEmployee_Success() throws InstantiationException {
        String firstName = "Frodo";
        String lastName = "Baggins";
        String description = "ring bearer";
        int jobYears = 1;
        Employee employee = new Employee(firstName, lastName, description, jobYears, "frodo.baggins@shire.com");
        assertEquals(firstName, employee.getFirstName());
        assertEquals(lastName, employee.getLastName());
        assertEquals(description, employee.getDescription());
        assertEquals(String.valueOf(jobYears), employee.getJobYears());


    @Test
    void createEmployee_NullFirstName(){
        String firstName = null;
        String lastName = "Baggins";
        String description = "ring bearer";
        int jobYears = 0;
        assertThrows(InstantiationException.class, () -> new Employee(firstName, lastName, description, jobYears,"frodo.baggins@shire.com"));
    }

    @Test
    void createEmployee_ZeroJobYears() throws InstantiationException {
        String firstName = "Frodo";
        String lastName = "Baggins";
        String description = "ring bearer";
        int jobYears = 0;
        Employee employee = new Employee(firstName, lastName, description, jobYears,"frodo.baggins@shire.com");
        assertEquals(firstName, employee.getFirstName());
        assertEquals(lastName, employee.getLastName());
        assertEquals(description, employee.getDescription());
        assertEquals(String.valueOf(jobYears), employee.getJobYears());
    }

    @Test
    void createEmployee_EmtpyEmail(){
        String firstName = "Frodo";
        String lastName = "Baggins";
        String description = "ring bearer";
        int jobYears = 0;
        String email = "";
        assertThrows(InstantiationException.class, () -> new Employee(firstName, lastName, description, jobYears,email));
    }
}

