# TICK-Stack-Implementation

# Team Members
* Sumit Keshari
* M20CS021


# Different Security Measures Implemented
1. HTTPS Security: TICK Stack by default run on http security. Implementing https security makes it more secure. I have implemented https security by self-generated using openssl. I have used RSA-2048 for encryption. The implementation of the https security is given above. Please look above for reference.
2. InfluxDB Security: As stated above, using username password in the wizard that appears when we click Getting Started is another level of security that I have implemented.
3.	Kapacitor Security: For kapacitor also, setting up username password in the wizard that appears when we click Getting Started is another level of security that I have implemented.

#Setup using docker-compose.yaml file
I have used docker-compose.yaml file to create containers of individual components of the TICK stack. We generally use docker-compose.yaml file to run multiple containers as a single service. So, inside our docker-compose.yaml file we are specifying that we want Telegraf InfluxDB Chorograf Kapacitor as services to run our TICK stack as a single service.
The content of docker-compose.yaml file is given in the repository. Please look into it for references.

#Certificate generation using openssl:
I am using the following command to generate the certificate using openssl. The command is given below:

``` openssl req -newkey rsa:2048 -new -nodes -x509 -days 3650 -keyout key.pem -out cert.pem
