# Setting up a dev container for Go

* Primary author: [John Shanahan](https://github.com/JoeShans21)
* Reviewer: [Harrison Enyeart](https://github.com/HJEunc)

## Prerequisites

Before you begin, make sure to have a Github account:

* [Github](https://github.com)

Make sure you have the following installed:

* [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* [Docker](https://www.docker.com/products/docker-desktop)
* [VS Code](https://code.visualstudio.com/) (with the [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) Extension)

### 1. Create a New Directory

Start by opening your terminal and creating a new directory by running the command below
```bash
mkdir go-dev-container
cd go-dev-container
```

Next, initialize a new Git repository:
```bash
git init
```

Now create a ```README.md``` file:
```bash
echo "# Go Dev Container Project" > README.md
```

### 2. Set Up the Dev Container

Inside your project directory, create a ```.devcontainer``` folder:
```bash
mkdir .devcontainer
```

Create a ```devcontainer.json``` file inside ```.devcontainer```:
```bash
touch .devcontainer/devcontainer.json
```

Open the project in Visual Studio Code:
```bash
code .
```


Now that we are inside VS Code, open the ```devcontainer.json``` file from the ```.devcontainer``` folder and add the following content:
```bash
{
    "name": "Go Dev Container",
    "image": "mcr.microsoft.com/devcontainers/go:bullseye",
    "customizations": {
        "vscode": {
            "extensions": [
                "golang.go"
            ]
        }
    }
}
```

!!! Tip
    - This uses the Go base image provided by Microsoft.
    - The golang.go extension adds helpful debugging and code navigation features

Save the file and reopen the project in the Dev Container:

* When prompted, click Reopen in Container in VS Code.

### 3. Verify Go Installation
Inside the Dev Container terminal, make sure Rust is installed and up to date by running:
```bash
go version
```
You should see an output like:
```bash
go version go1.21.0 linux/amd64
```
!!! Tip
    If the version is outdated, rebuild the container to ensure the latest image is used.

### 4. Create a Go Project
Initialize a new Go module, mine is called ```hello-comp423```
```bash
mkdir hello-comp423
cd hello-comp423
go mod init hello-comp423
```
!!! Tip
    The go mod init command creates a go.mod file, which defines your module's dependencies.

Navigate into the project folder:
```bash
cd hello-comp423