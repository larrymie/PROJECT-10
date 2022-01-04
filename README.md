# PROJECT-10
#LOAD BALANCER SOLUTION WITH NGINX AND SSL/TLS#

1. Configure Nginx as a Load Balancer
2. Register a new domain name and configure secured connection using SSL/TLS certificates
My target architecture will look like this: IMAGE 01
![01](https://user-images.githubusercontent.com/91284177/147986457-71f13c40-ac85-4cad-ac5c-c05c1aed2154.png)

I registered a domain name using 'Freenom' the domain was named '**larrymiemie.tk**' hosted in a public zone.
I created an aws Route53 and linked the route53 with my domain name. IMAGES 03, 04, and 05
![03](https://user-images.githubusercontent.com/91284177/148058180-a433eb30-17fb-44e8-8342-ba589d9bca77.png)
![04](https://user-images.githubusercontent.com/91284177/148058201-3a5551e5-9073-4890-91d1-1961a1c5105b.png)
![05](https://user-images.githubusercontent.com/91284177/148058208-5989a13c-4af2-45ed-977f-8f8ad38809d3.png)

I Created an EC2 VM based on Ubuntu Server 20.04 LTS and name it Nginx LB. I copied the IP/Elastic used it to create a route53. IMAGE 06 and 07.
![06](https://user-images.githubusercontent.com/91284177/148059722-e17b985a-c8c2-4846-9947-c2d534d54d45.png)
![07](https://user-images.githubusercontent.com/91284177/148059935-35b920af-fa89-4d93-9f31-3427cbe99f9d.png)

Another A record with 'www' was also created. Now my Load balancer, route53 and domain name are connected together. IMAGE 08
![08](https://user-images.githubusercontent.com/91284177/148060561-3c65b338-6485-4afb-ba79-472e627d272d.png)



I  Installed and configured  Nginx  as  a  load balancer to point traffic to the resolvable DNS names of the webservers.
 IMAGES 09, 10 and 11

![09](https://user-images.githubusercontent.com/91284177/148068547-287d1425-c51b-442a-81d4-b62c4eca962b.png)
![10](https://user-images.githubusercontent.com/91284177/148068566-d8a23e3f-2712-46dd-b224-b14a07cdb4df.png)
![11](https://user-images.githubusercontent.com/91284177/148068623-36d3d116-de54-4cee-b606-05973eee5ecb.png)

I linked the load balancer newly created in my site available to my site enabled using so that the Nginx can access the configuration through it. I used the code <sudo ln -s ../sites-available/load_balancer.conf .> 
IMAGE 12
![12](https://user-images.githubusercontent.com/91284177/148070235-cd822198-d12e-4a9b-aac8-cb1f7f59b9eb.png)

Arrow linking my the site available and load balancer config to my site enabled. IMAGE 13

![13](https://user-images.githubusercontent.com/91284177/148070763-96260b25-cfd6-4b15-9482-aaf291eefac6.png)

I confirmed that my Web Servers can be reached from my browser using new domain name using HTTP protocol. IMAGE
![14](https://user-images.githubusercontent.com/91284177/148096140-300181e8-3805-48a8-a0fa-6e47ad7e7f8e.png)
I successfully received a secured certificate by providing the details of my domain names IMAGE 15

![15](https://user-images.githubusercontent.com/91284177/148099023-08395db5-5f0a-4f57-a5a5-e26ea0306910.png)

I installed certbot and request for an SSL/TLS certificate. Also Made sure snapd service is active and running.

I tested secured access to my Web Solution by trying to reach "https://larrymiemie.tk"

I was able to access my website by using HTTPS protocol (that uses TCP port 443) and see a padlock pictogram in my browser’s search string. I clicked on the padlock icon and saw the details of the certificate issued for my website. IMAGE 16
![16](https://user-images.githubusercontent.com/91284177/148104170-74744e27-a5e7-4307-88c0-b5654c93f453.png)

#Set up periodical renewal of SSL/TLS certificate#

I ran the commands <crontab -e> and <* */12 * * *   root /usr/bin/certbot renew > /dev/null 2>&1>
The above commands were used to configure my certificate to auto renewal without creating a log file.





