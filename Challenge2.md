#  Challenge 2: Secure & Scale ASCS's Infra

## Scenario 

**Scenario:** You are an infrastructure engineer at our company - All Safe Cyber Security. Your job responsibilities include:

- Deploying Infrastructure on the server
- Manage your webservers and keep them secure from security attacks.
- Make sure the services are always running despite getting high network traffic
- Manage access to the webserver

Upon your onboarding, your manager has assigned you a task to **" deploy the website on the server "**  and make it accessible to the world outside.  

- You realised that containerization is one of the best ways to deploy our services on the server and hence you decide to deploy the website and the database in the form of containers.

### Challenge 
### **Part 0:** Deploying the containers

- The product development team has bundled the website into an image which has a webserver listening on port 8000.
- The team mentioned that they are using the "POSTGRES" database and have given you certain environment variables that are essential for the database to run.

```

Webserver image: sh0rtcyb3r/ccdc23_af_django:latest

```

```

Database image: postgres

Environment Variables : 

POSTGRES_DB=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
```

- Upon researching about docker, you realise that docker compose is an easier solution to deploy containers on the server. Although, this is not the only way to deploy containers, you believe that docker compose automates the process of deploying containers.

**Objective:** : Install docker on your machine and deploy the containers mentioned above. The webserver and database must be able to communicate with each other and you must come up with a solution that links the containers.

### **Part 1:**  Vulnerability

- You have deployed the webservers and to decided to test it by opening the webpage in your browser. Upon opening the webpage,  you can't help but notice that there isn't a secure lock on the website. You asked the product team about it and they said that it isn't important. However, they  did challenge you to report to them if you could find any problems with this.
- Using yourknowledge about HTTP, you remember that are certain basic vulnerabilities that exist with unencrypted communications.

**Objective:** You are tasked with showing your team that someone can gather these credentials very easily and gain access into the admin panel of the website.

### **Part 2:** Proxy

- Your team  has accepted your report on the insecure nature of the web application and has asked foryour consultation on how to make it more secure.
- You need to secure your infrastructure. As a recommended first step, it would be advisable to not allow the website to be publically accessible without going through a proxy.

**Objective:** Your objective is to create a proxy with HAProxy and have all the traffic flow through the proxy to reach the web server. IT has asked you to make HAProxy accesible through port 80 for all website traffic.

### **Part 3:**  HTTPS

- Good work. You now have a proxy that will make traffic go through it to get to the web server. The next step is to secure the communications that are coming to it.

**Objective:** Your objective is to add an additional layer of security on your infrastructure by enforcing TLS on the proxy you just created. All requests must be done through TLS.

- In order to implement TLS, you realise that you need a signed certificate to verify the authenticity. Your task is to create a certificate authority and self sign the certificate.

To create a certificate authority follow the gude here:  <https://easy-rsa.readthedocs.io/en/latest/>

### **Part 4:**  Restrict access

- It is no secret that not everyone should be able to access the admin page but in this case, the admin page is accessible to everyone which can lead to serious security concerns.

**Objective:** You are tasked with finding a way to only allow certain IPs to access the /admin page and to deny access to all others.

### **Part 5:**  High Availability

- Your infrastructure is looking much better security-wise  It was a quick-fix to a long-term problem.
- Now, the web app is receiving tremendous amounts of encrypted traffic. A single server won't cut it anymore.

**Objective:** Your objective is to scale the website and be able to handle all this traffic. However, you can only use one database instance. You must think of a way to load balance the incoming traffic.

## Resources

Resources that can help you  perform the above tasks:

- <https://docs.docker.com/compose/>
- <https://docs.docker.com/engine/reference/run/>
- <https://docs.docker.com/network/links/>
- <https://www.haproxy.com/blog/haproxy-configuration-basics-load-balance-your-servers/>
- <https://www.haproxy.com/blog/haproxy-configuration-basics-load-balance-your-servers/>
