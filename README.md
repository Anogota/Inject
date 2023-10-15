First step we need to do is, recon.
```
PORT     STATE SERVICE     VERSION
22/tcp   open  ssh         OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 caf10c515a596277f0a80c5c7c8ddaf8 (RSA)
|   256 d51c81c97b076b1cc1b429254b52219f (ECDSA)
|_  256 db1d8ceb9472b0d3ed44b96c93a7f91d (ED25519)
8080/tcp open  nagios-nsca Nagios NSCA
|_http-title: Home
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```
We can see there complity nothing, let's go into page. Where can see just regular page for CTF, nothing working. Let's do directory enumeration.
```
blogs                   [Status: 200, Size: 5371, Words: 1861, Lines: 113, Duration: 86ms]
environment             [Status: 500, Size: 712, Words: 27, Lines: 1, Duration: 76ms]
error                   [Status: 500, Size: 106, Words: 3, Lines: 1, Duration: 63ms]
register                [Status: 200, Size: 5654, Words: 1053, Lines: 104, Duration: 429ms]
upload                  [Status: 200, Size: 1857, Words: 513, Lines: 54, Duration: 248ms]
```
We can see intresting directory, upload. Let's look on it
We can upload image, and view you image. 

![image](https://github.com/Anogota/Inject/assets/143951834/f371f176-25eb-4390-9715-0663d030e8d4)

Let's look close on the view your image, turn on burp and intercept the traffic.

And i did LFI

![image](https://github.com/Anogota/Inject/assets/143951834/64cfc9f5-d46c-42d3-acc4-e20bb34b8907)

We need now more dig to find more intresting. After few min i found intresting file.

![image](https://github.com/Anogota/Inject/assets/143951834/233e0643-5063-4d94-9769-84b606fa3604)

Now we know what kind of version working on the server, this is a:
```
<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.6.5</version>
```
Let's search something about it, maybe we will find CVE for this verion.
