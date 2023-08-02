# Let's Go Practice

Code for Let's Go Handbook by Alex Edwards, copied by Jacob Do. 

## Installation

Use this [link](https://github.com/jacobcdo/GoPractice.git) to clone the repo to your local machine. Make sure you are in a dedicated directory. 

```bash
$ git clone https://github.com/jacobcdo/GoPractice.git
```

## Usage

Make sure to have Homebrew installed on your device. Homebrew can be downloaded [here](https://brew.sh/).

Once installed, make sure to have MySQL downloaded.
```bash
$ brew install MySQL

$ brew services start MySQL
$ Mysqladmin -u root password "[MY_PASSWORD]"

$ MySQL -u root -p
Enter password: # 

mysql> CREATE DATABASE snippetbox CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
       USE snippetbox;
       CREATE USER 'web'@'localhost';
       GRANT SELECT, INSERT, UPDATE, DELETE ON snippetbox.* TO 'web'@'localhost';
       ALTER USER 'web'@'localhost' IDENTIFIED BY '[MY_PASSWORD]';
```

Now create a self-signed TLS certificate.

```bash
$ cd .../practicefinal

$ mkdir tls

$ cd tls

$ go run /usr/local/go/src/crypto/tls/generate_cert.go --rsa-bits=2048 --host=localhost
```

Edit main.go:33 and change pass for the password created earlier to log into mySQL.

```bash
dsn := flag.String("dsn", "web:pass@/snippetbox?parseTime=true", "MySQL data source name")
```

Commands to run the snippetbox code:
```bash
$ cd .../practicefinal

$ go run ./cmd/web

$ go test ./cmd/web
```


