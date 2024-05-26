# TaskCafe

## Features

The following features have been implemented:

- Manage tasks through a Kanban board interface (set due dates, labels, add checklists)
- View all your current assigned tasks through the My Tasks view
- Personal projects
- Task comments and activity

## Installation

### With docker & docker-compose

You'll need both [docker](https://www.docker.com/) & [docker-compose](https://docs.docker.com/compose/install/) installed.

First clone the repository:

``` bash
git clone https://github.com/ShivamAgarwal-code/Matrice-task.git && cd taskcafe
```

Now do the following:

``` bash
docker-compose -p taskcafe up -d
```

This will start a postgres instance as well as a taskcafe instance.

The second command runs the database schema migrations.

If you visit [http://localhost:3333](http://localhost:3333), you will get redirected to the installation
screen so that you can create the first system user.

### From Source

You'll need [Golang](https://golang.org/dl/) installed on your machine.

Next, clone the repository:

``` bash
git clone https://github.com/ShivamAgarwal-code/Matrice-task.git && cd taskcafe
```

Next we need to build the binary. This project uses [Mage](https://magefile.org/) for its build tool.

``` bash
go run cmd/mage/main.go install
go run cmd/mage/main.go build
```

This will:

- Install all yarn packages for the frontend
- Build the React frontend
- Embed the React frontend in the binary
- Compile the final exectuable binary

The newly created `taskcafe` binary can be found in the __dist__ folder.

It contains everything neccessary to run except the config file. An example config file can be found in `conf/app.example.toml`.

The config will need to be copied to a `conf/app.toml` in the same place the binary is.

Make sure to fill out the database section of the config in order to connect it to your database.

Then run the database migrations with `taskcafe migrate`.

Now you can run the web interface by running `taskcafe web`.

