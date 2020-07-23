# odata-services
## How to build and run the application
Make sure you have git, Java 8 jdk (or above) and Apache Tomcat 8.5 (or above) installed on your computer

See how to install git 
[here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

See how to install jdk1.8 
[here](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html)

See how to install and run Apache Tomcat
[here](https://tomcat.apache.org/tomcat-8.5-doc/introduction.html)

Please make sure your Java SDK 1.8 on the path, for example use
```sh 
$ java -version
java version "1.8.0_144"
Java(TM) SE Runtime Environment (build 1.8.0_144-b01)
Java HotSpot(TM) 64-Bit Server VM (build 25.144-b01, mixed mode)
```
Download the source code from github, on your computer open new terminal
```sh 
$ git clone https://github.com/wayoubi/odata-services.git
```

Compile and Build all system components
```sh
cd odata-services
./mvnw.sh clean install 
```
Copy the war file and deploy it into your tomcat server
```sh
cd product-web/target/
cp product-web.war $TOMCAT_HOME/webapps/.
```

start tht tomcat server. Open a new terminal and execute the following curl command
```sh
curl -v  http://localhost:8080/product-web/ProductService.svc/Products
```

You should get the similar response
```sh
HTTP/1.1 200
Connection: keep-alive
Content-Length: 369
Content-Type: application/json; odata.metadata=minimal
Date: Thu, 23 Jul 2020 05:51:29 GMT
Keep-Alive: timeout=20
OData-Version: 4.0

{
    "@odata.context": "$metadata#Products",
    "value": [
        {
            "Description": "Notebook Basic, 1.7GHz - 15 XGA - 1024MB DDR2 SDRAM - 40GB",
            "ID": 1,
            "Name": "Notebook Basic 15"
        },
        {
            "Description": "Ultrafast 3G UMTS/HSDPA Pocket PC, supports GSM network",
            "ID": 2,
            "Name": "1UMTS PDA"
        },
        {
            "Description": "19 Optimum Resolution 1024 x 768 @ 85Hz, resolution 1280 x 960",
            "ID": 3,
            "Name": "Ergo Screen"
        }
    ]
}
```
