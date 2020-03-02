# HTTP-VS-HTTPS

![](https://cdn.discordapp.com/attachments/674207534818525194/684012358510706722/HTTP-vs-HTTPS11.png)

## http
### defination
HTTP stands for Hyper Text Transfer Protocol, It is the main protocol for transmitting data across websites.

### Use Of http
Communication between client computers and web servers is done by sending HTTP Requests and receiving HTTP Responses.

Clients are often browsers (Chrome, Edge, Safari), but they can be any type of program or device, Servers are most often computers

## problem!
The problem is that HTTP (note: no "s" on the end) data is not encrypted, and it can be intercepted by third parties to gather data being passed between the two systems

## https
Hypertext transfer protocol secure (HTTPS) is the secure version of HTTP, which is the primary protocol used to send data between a web browser and a website.

## http Vs https
HTTPS is encrypted in order to increase security of data transfer. This is particularly important when users transmit sensitive data, such as by logging into a bank account, email service, or health insurance provider

HTTPS uses an encryption protocol to encrypt communications. The protocol is called Transport Layer Security (TLS), although formerly it was known as Secure Sockets Layer (SSL)
 ## What are TLS/SSL certificates?
 ### SSL (Secure Socket Layer)
 which is a protection layer that relies on encrypting the process of exchanging information through web pages on the Internet.
 
### TLS (Transport Layer Security):
This represents the latest and most secure version of SSL, but SSL is traded, because it is the most common between companies and website owners.

HTTPS is a secure extension of HTTP. Websites that install and configure an SSL/TLS certificate can use the HTTPS protocol to establish a secure connection with the server.

## When and Why is SSL/TLS is a MUST?
SSL/TLS is a must whenever sensitive information such as usernames and passwords or payment processing information is being transferred.
The goal of SSL/TLS is to make sure that only one person — the person or organization that the uploader intends — can access the data that’s being transferred. This is particularly important when you think of how many devices and servers the information is transferred between before it reaches its destination.

## How Do SSL/TLS Certificates Work?
SSL have two-key encryption system:
### Private Key:
This key is responsible for the decryption of data and this key is only present on the site's server / is hidden and is almost impossible to obtain.

### Public Key: 
This key is the one that is used to encrypt information or data, and it is called public because the browser obtains it by entering any website that uses https.

Thus, the data transfer process became greatly secure, as it is true that the https protocol does not mean complete security, but it is much better and provides adequate protection for most sites.
If your site is a banking service, for example, then you need more protection.

You can tell whether a website is using SSL by looking for a padlock icon or a green bar at the top of your browser. You should be able to click on this icon to view the information on who holds the certificate and to manage your SSL settings.

![](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2018/11/what-does-ssl-protect.png)

# Why is this important to implement in your projects?

Today there isn’t much content that website users or creators want passed over the web that isn’t fairly secure and generally they would rather a website have a secure connection versus not. So, website creators are making sure that their sites are HTTPS versus HTTP, even if they run a fairly innocuous informational site about dog breeds, for instance.


## HTTPS

* helps prevent intruders from tampering with the communications 
between your websites and your users’ browsers. Intruders include intentionally malicious attackers, and legitimate but intrusive companies, such as ISPs or hotels that inject ads into pages.

* Protects the privacy and security of your users

    prevents intruders from being able     to passively listen to             communications between your websites     and your users.


## SSL / TLS

The goal of SSL/TLS is to make it safe and secure to transmit sensitive information including personal data, payment or login information.

* Avoids browser popups that warn website visitors that your website is not secure
* Creates a safer experience for your customers
* Builds customer trust and improves conversions
* Encrypts the sensitive data that gets transmitted
* Uses SSL/TLS with identity verification helping distinguish your  website from fraudulent look-alikes

* Achieves a stronger Google SEO ranking
* Chrome will also give users in-form security warnings at the bottom of any form fields on sites that still run the HTTP client


* When you need authentication: SSL/TLS allows you to prove the identity of your server so that people know that you are who you say you are.

* When you need to comply with industry standards: In some industries such as the finance industry, you’ll be required to maintain certain base levels of security.It's required for PCI Compliance
In order to accept credit card information on your website, you must pass certain audits that show that you are complying with the Payment Card Industry (PCI) standards. 
## how to generate certificates and use them in a node project ?

**Step 1:Create or download SSL Certificate Files** 
  - create certificate
```
openssl req -nodes -new -x509 -keyout server.key -out server.cert
```
> then enter the required information.
> 
- or you can buy SSL Certificate Files and download it --- [The Best SSL Certificate Products](https://cheapsslsecurity.com/sslproducts.html)
![Screenshot from 2020-03-02 14-09-22](https://user-images.githubusercontent.com/49004640/75678173-b2ed4c80-5c95-11ea-9a47-e96f8117a44c.png)

**Or ask the server owner to give you a certificate without entering data**

**Step 2: Create https_server.js file & upload SSL files to Server directory**

```
const app = require("express")();
const https = require("https");
const fs = require("fs");

app.get("/", (req, res) => {
  res.send("hi");
});

https.createServer(
    { key: fs.readFileSync("server.key"),
      cert: fs.readFileSync("server.cert")
      },
    app
  )
  .listen(9000, () => {
    console.log("Listening...");
  });
  
```



**Step 3: Start Node.js**

***If you do not put options here***
```
                 \\\///
https.createServer({},app).listen(9000, () => {console.log("Listening...")});
```
**The site will look like this**

![](https://flaviocopes.com/express-https-self-signed-certificate/without-cert.png)

**And if your certificate is not certified by a trusted site**
**The site will look like this**
![Screenshot from 2020-03-02 15-11-53](https://user-images.githubusercontent.com/49004640/75679381-2e4ffd80-5c98-11ea-86d7-eceb9b270937.png)

**And if your certificate is reliable, your site will look like this, but with different data in issued it and issued By , and the type of certificate**
![Screenshot from 2020-03-02 15-13-40](https://user-images.githubusercontent.com/49004640/75679498-6bb48b00-5c98-11ea-92ee-d7cda3a8d1ea.png)

