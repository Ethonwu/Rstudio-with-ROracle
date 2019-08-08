# Rstudio-with-ROracle
This repo is clone from https://github.com/rocker-org/rocker-versioned/tree/master/rstudio/3.5.1
Due to crocker-org RStudio docker can't import ROracle, so I modify it,let it can import 
## Why ROracle 
### Why
It can be use from another lib such as: ODBC, RJDBC 
1. ODBC need to setting config from OS, I think is very complicated, due to this env is Docker
2. RJDBC need to install Java, and get some Jar file, although do not set config from OS, but need to install Java
### ROracle
* ROracle, this lib is recommand by my friend [Rocky](https://github.com/simpleplanya), and I foind this [Oracle blog](https://blogs.oracle.com/r/r-to-oracle-database-connectivity:-use-roracle-for-both-performance-and-scalability)
* This is my install lib [reference](https://thraxys.wordpress.com/2016/10/25/install-roracle-on-linux/), in this article is using **oracle 12.1 version** , my version is **oracle 12.2 version** , the connect OracleDB version is only require for OracleDB 12
## Package version info
1. R: 3.5.1
2. Java: openjdk 1.8
3. Oracle Instantclient: 12.2
4. DBI: 1.0.0
5. ROracle: 1.3-1
### Another Oracle Instantclient version
* Instantclient 18.5, it can connect OracleDB for version 18 if want to use see [here](https://github.com/Ethonwu/Rstudio-with-ROracle/tree/master/build_on_oracle18.5)
## Usage
* It is same as [here](https://github.com/rocker-org/rocker-versioned/tree/master/rstudio/3.5.1)
* Below command is copy from [here](https://github.com/rocker-org/rocker-versioned/tree/master/rstudio/3.5.1) link, if need more option you can access link find something
#### Quickstart
```sh
docker run --rm -p 8787:8787 -e PASSWORD=yourpasswordhere ethonwu/roracle:fix
```
#### Bypassing the authentication step
```sh
docker run --rm \
  -p 127.0.0.1:8787:8787 \
  -e DISABLE_AUTH=true \
  ethonwu/roracle:fix
```
#### Using Dockerfile Build
1. Clone this repo
```sh
git clone https://github.com/Ethonwu/Rstudio-with-ROracle.git
```
2. Run docker build
```sh
docker build -t rstudio:test .
```
3. Enjoy your building 
## Connect to oracle code example
* Here is an example to connect OracleDB 
```
library(DBI)
library(ROracle)
conn = dbConnect(dbDriver("Oracle"),username="USERNAME",password="PASSWORD",dbname="IP:PORT/DBNAME")
dbGetQuery(conn, "Query here")
```
## TODO
* [ ] ADD OracleDB images to test connect 
* [ ] Test on another lib such ODBC , RJDBC....
* [ ] Testing to connect another DB
