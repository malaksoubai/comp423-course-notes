# Setting up a dev container for Go

* Primary author: [Malak](https://github.com/malaksoubai)

* Reviewer: [Yueen Ma](https://github.com/myueen)

## Introduction

Hi all! This is an easy tutorial for creating a new project in dev container for Go! Go is an open-source programming language that Google developed. It's used to create software for a variety of purposes, including cloud-based applications, web applications, and networking services. 

This tutorial is made in collaboration with Yueen Ma. Hope you all enjoy! :smile:

## Prerequesites

- Sign up at [GitHub](https://github.com/) if you don't have an account already.

- Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

- Download and install [Visual Studio Code](https://code.visualstudio.com/) (VS Code).

- Install [Docker](https://www.docker.com/products/docker-desktop/).

- Understand Command-line basics.

## PART 1. Go Project Setup: Create Repo

### STEP 1. Create a Local Directory and Initialize Git

1. Open your terminal or command prompt.
2. Create a new directory for your project.

```bash
mkdir go-project
cd go-project
```

3. Initialize a new Git repository:

```bash
git init
```
4. Create a README file:

```bash
echo "# Go Hello World Project" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### STEP 2. Create a Remote Repository on GitHub

1. Log in to your GitHub account and navigate to the Create a New Repository page.

2. Fill in the details as follows:

- **Repository Name**: go-project
- **Description**: "Go Dev Container for conding in Go."
- **Visibility**: Public

3.  Do not initialize the repository with a README, .gitignore, or license.

4.  Click Create Repository.

### STEP 3. Link your Local Repository to GitHub

1.  Add the GitHub repository as a remote:

```bash
git remote add origin https://github.com/<your-username>/go-project.git
```

Of course, replace ```<your-username>``` with your GitHub username.

2. Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: ```bash git branch -M main```.

3. Push your local commits to the GitHub repository:

```bash
git push --set-upstream origin main
```

!!! note "Understanding the --set-upstream Flag"
    - `git push --set-upstream origin main`: This command pushes the main branch to the remote repository origin. The `--set-upstream` flag sets up the main branch to track the remote branch, meaning future pushes and pulls can be done without specifying the branch name and just writing `git push origin` when working on your local `main` branch. This long flag has a corresponding `-u` short flag.

4. Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. You can use `git log` locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.

## PART2. Setup the Development Environment

### What is a Development (Dev) Container?

A dev container ensures that your development environment is consistent and works across different machines. It is like a "mini computer" inside your computer that includes everything you need to work on a specific project. With a dev container, everyone works in an identical environment, reducing bugs caused by "it works on my machine" issues.

### STEP 1. Add Development Container Configuration

1. In VS Code, open the `go-project` directory. You can do this via: File > Open Folder.
2. Install the **Dev Containers** extension for VS Code.
3. Create a `.devcontainer` directory in the root of your project with the following file inside of this "hidden" configuration directory: `.devcontainer/devcontainer.json`

```
{
  "name": "Go Project Tutorial",
  "image": "mcr.microsoft.com/vscode/devcontainers/go:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["golang.go"]
    }
  },
  "postCreateCommand": "go mod init github.com/<your-username>/go-project"
}
```
4. Save your changes and open the **Command Palette** in VS Code (Ctrl+Shift+P or Cmd+Shift+P on Mac).

5. Search for and select **Dev Containers: Rebuild and Reopen in Container**. This step may take some time.

## PART3. Write some code

1. After the container reloads, check that Go is sucessefully running:

```bash
go version
```

2. Create a new file called ```tutorial.go```

3. Paste the following code into your file and save the file.

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423!")
}
```
4. In your terminal, run your code to see the greeting. 

```go
$ go run .
```

You should see the output: ```Hello COMP423!```

5. You are all done! :smile:

### Citations: 
1. Jordan, Kris. "Starting a Static Website Project with MkDocs," _COMP423 - Spring 2025_, https://comp423-25s.github.io/resources/MkDocs/tutorial/#step-2-add-requirementstxt-python-dependency-configuration. 

2. Klabnik, Steve and Nichols, Carol, "The Rust Programming Language," [https://doc.rust-lang.org/book/.](https://go.dev/doc/tutorial/getting-started)





