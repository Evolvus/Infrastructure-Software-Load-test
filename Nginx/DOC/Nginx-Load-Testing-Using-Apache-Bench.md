### Load testing on NginX using Apache Bench tool

For Nginx load test we used Apache Bench

References:

[Nginx Benchmark](https://www.garron.me/en/go2linux/how-benchmark-stress-your-apache-nginx-or-iis-server.html)


[Nginx Performance Test](https://www.nginx.com/blog/testing-the-performance-of-nginx-and-nginx-plus-web-servers/)

### Prerequirement

1. Install Nginx in server.

2. Install Apache bench By following steps.

        * Open terminal (ctrl+Alt+t) as a root user.
        * Run the "apt-get install apache2-utils" on terminal
         [Installation guide](https://www.sotechdesign.com.au/how-to-install-just-ab-apachebench-on-debian-or-ubuntu/)

3. Start the server.

4. open the terminal (ctrl+Alt+t) and follow the path where key file is present and login as "ssh"  
    using command "i.p server -i ./KeyFileName".

   Eg: ssh ec2-user@52.66.110.170 -i ./Load-Testing-1.pem

5. start nginx using command 
```console
"start nginx.service".
```
6. uplod the different -2 type (html,jpg,css etc ) and different -2 size of file on nginx 
   so when you want hit the specific file .

```console
"rsync -rave "ssh -i pathof key" pathof key i.p of server:/usr/share/nginx/"
```

7. open the terminal (ctrl+Alt+t) and run the command.
```console
       "ab -kc 1000 -n 10000 http://www.some-site.cc/tmp/index.html"
         
        -n requests     Number of requests to perform
        -c concurrency  Number of multiple requests to make at a time
        -k              Use HTTP KeepAlive feature
        index.html --file name 

        tmp-- folderName
```

### Nginx Configuration

1. Open the terminal (ctrl+Alt+t) and follow the path where key file is present and login as "ssh"  
   using command 
```console
"i.p server -i ./KeyFileName"
```
Eg: ssh ec2-user@52.66.110.170 -i ./Load-Testing-1.pem

2. Run the command and choose edit option and use "i" or " insert"
```console
vim /etc/nginx/nginx.conf
```   
3. Once changes done , then use **"Esc"** for come out from the insert than user **":wq!"** and enter.

4. Stop Nginx server.
```console
#service nginx stop
```
5. Start Nginx server.
```console
#service nginx start
```
6. Run the command to verify the necessary change.  
```console
# cat /etc/nginx/nginx.conf(check and verify the change done)
```

Server to Server Load Test

1. We required two servers, one server where Nginx present and other server to run the test.

2. Run the Nginx server.

3. Login in other server.
      open the terminal (ctrl+Alt+t) and follow the path where key file is present and login as **"ssh"** using command 
```console
"i.p server -i ./KeyFileName"
```
 Eg: ssh ec2-user@52.66.110.170 -i ./Load-Testing-2.pem

4. verify it to ping one server to other server by using command
```console
"ping ip of other server"
```
5. Run the command for start the test
```console
 ab -kc 1000 -n 1000000 url
```

### Test Observations

The Behavoius of NGINX is good between 1 to 2 CPU and after that is normal.
In effect , if we increase the CUP after 4 CPU the number of request per second and Transfer rate same in the cloud environment.
We have conducted the night run for more than 8 hours and CPU Utilisation and Memory is within the normal limit.

![Picture1](https://storage.googleapis.com/nginx-evolvus/Picture1.png)
![Picture2](https://storage.googleapis.com/nginx-evolvus/Picture2.png)
![Picture3](https://storage.googleapis.com/nginx-evolvus/Picture3.png)
![Picture4](https://storage.googleapis.com/nginx-evolvus/Picture4.png)
![Picture5](https://storage.googleapis.com/nginx-evolvus/Picture5.png)
![Picture6](https://storage.googleapis.com/nginx-evolvus/Picture6.png)
![Picture7](https://storage.googleapis.com/nginx-evolvus/Picture7.png)