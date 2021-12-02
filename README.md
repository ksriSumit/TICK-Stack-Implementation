# TICK-Stack-Implementation

# Team Members
* Sumit Keshari
* M20CS021


# Different Security Measures Implemented
1. HTTPS Security: TICK Stack by default run on http security. Implementing https security makes it more secure. I have implemented https security by self-generated using openssl. I have used RSA-2048 for encryption. The implementation of the https security is given above. Please look above for reference.
2. InfluxDB Security: As stated above, using username password in the wizard that appears when we click Getting Started is another level of security that I have implemented.
3.	Kapacitor Security: For kapacitor also, setting up username password in the wizard that appears when we click Getting Started is another level of security that I have implemented.

# Setup using docker-compose.yaml file
I have used docker-compose.yaml file to create containers of individual components of the TICK stack. We generally use docker-compose.yaml file to run multiple containers as a single service. So, inside our docker-compose.yaml file we are specifying that we want Telegraf InfluxDB Chorograf Kapacitor as services to run our TICK stack as a single service.
The content of docker-compose.yaml file is given in the repository. Please look into it for references.

# Certificate generation using openssl
I am using the following command to generate the certificate using openssl. The command is given below:

``` 
openssl req -newkey rsa:2048 -new -nodes -x509 -days 3650 -keyout key.pem -out cert.pem
```

After generating certificates, we will move both key.pem and cert.pem to a newly created folder named as certs. For this we need to change permission level of the certificates generated. The following command is used for that:

```
sudo chmod -R 777 cert.pem 

sudo chmod -R 777 key.pem 

sudo mkdir /home/certs 

sudo mv *.pem /home/certs

```

This directory '/home/certs' is made as a permanent storage place so that we don't have to repeat the certificate setup process.

After all this we need to run the docker-compose command:

```
sudo docker-compose create

sudo docker-compose up -d
```

As specified in the docker-compose.yaml file, the chronograf will be serving for the UI and running on port number 8888 which is default port number at which the chronograf tool runs as per documentation of chronograf.

When we access the ip http://localhost:8888 we will not be able to access because it has now been secured with https using the steps that we carried out in above steps. So, when we try to access using https://localhost:8888 we will finally be able to see the chronograf UI. 


# References

```
https://www.thoughtworks.com/en-in/radar/platforms/tick-stack

https://www.influxdata.com/blog/introduction-to-influxdatas-influxdb-and-tick-stack/

https://docs.influxdata.com/chronograf/v1.9/administration/managing-security/#configure-tls-transport-layer-security-and-https

http://cactusprojects.com/setup-https-for-grafana/
```
