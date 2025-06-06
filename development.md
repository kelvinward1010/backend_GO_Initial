
## Create a module in which you can manage dependencies.
- Run the go mod init command, giving it the path of the module your code will be in.
-- Example: project's folder: myapp
```bash
    go mod init myapp
```

## Install API GIN
```bash
go get github.com/gin-gonic/gin
```

## How to import this package to that package
- You need to set the names of folders and files to lowercase.
- The first letter of the function name should be capitalized so that the function can be called.


## Setup run reload server
- You need to setup air if you don't have this
```bash
go install github.com/air-verse/air@latest
```

- Run it in terminal
```bash
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> ~/.bashrc
```

### Tạo file cấu hình air.toml
- Run the following command to create the default configuration file:
```bash
air init
```

- If you don't have air.toml, you can create it manually.
- Create an air.toml file in the root directory of your project and paste the following content:
```toml
# Config Air for hot reload
[build]
  bin = "tmp/main"
  cmd = "go build -o tmp/main"
  delay = 1000
  exclude_dir = ["tmp", "vendor", "node_modules"]
  exclude_file = [".gitignore"]
  full_bin = "./tmp/main"

[log]
  level = "debug"

[watcher]
  include_ext = ["go", "tpl", "tmpl", "html", "css", "js"]
  exclude_dir = ["tmp", "vendor", "node_modules"]
```

### Run server
```bash
air
```
or
```bash
air -c .air.toml
```


## Setup db
- Command to setup DB Postgre
```bash
go get github.com/jackc/pgx/v5
go get github.com/jackc/pgx/v5/pgxpool
go get github.com/joho/godotenv
go get -u gorm.io/gorm
go get -u gorm.io/driver/postgres
```


## Setup JWT
```bash
go get github.com/lib/pq
go get github.com/golang-jwt/jwt/v5
```


## Setup Swagger for GIN
```bash
go get -u github.com/swaggo/gin-swagger
go get -u github.com/swaggo/files
go get -u github.com/swaggo/swag/cmd/swag
```

- Install SWAG
```bash
go install github.com/swaggo/swag/cmd/swag@latest
```

- After that run this command:
```bash
swag init
swag init -g main.go
swag init -g main.go -o ./app/docs
```

- Open swagger on: http://localhost:8000/swagger/index.html#/