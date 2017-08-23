
### Fixing Git SSL Certificate Issues

Git use SSL extensively to ensure that communication between the Git client and the Git server is encrypted preventing MITM or Man In The Middle Attacks. However this can also cause issues when you've setup your own Git server and generate a self signed certificate. We've also seen these issues arise when using Git on Windows. 

In this short howto we will look at fixing the GIT SSL issues that's regularly encountered while using windows.

## What Do The Errors Look Like

- You should not have these issues if developing code on Linux or Raspbian on the Raspberry Pi.
- The SSL issues can also crop up when trying to commit code into the master repo at Github from your local windows repository. 
- Here's what the error might look like -

```
 bash# git clone https://username@git.example.com/scm/repository.git
 Cloning into 'repository'...

 Couldn't find host git.example.com in the _netrc file; using defaults

 Adding handle: conn: 0x22a7568
 Adding handle: send: 0
 Adding handle: recv: 0
 Curl_addHandleToPipeline: length: 1
 - Conn 0 (0x22a7568) send_pipe: 1, recv_pipe: 0
 About to connect() to git.example.com port 443 (#0)
   Trying 10.253.136.142...
 Connected to git.example.com (10.253.136.142) port 443 (#0)
 successfully set certificate verify locations:
   CAfile: C:\Program Files (x86)\Git/bin/curl-ca-bundle.crt
  CApath: c:/Users/username/Downloads
 SSL certificate problem: self signed certificate in certificate chain
 Closing connection 0
 
 fatal: unable to access 'https://username@git.example.com/scm/repository.git': SSL certificate problem: self signed certificate in certificate chain
```

There are a few different approaches to sort this out. Let's look at both of them below.

### Option 1 : Turn off Git SSL Verification

- You can stop the Git client from verifying your servers certificate and to trust all SSL certificates you use with the Git client. 
- This has it’s own security risks as you would not be warned if there was a valid problem with the server you are trying to connect to. 
- That said, it’s the quickest and easiest fix for a non trusted server certificate. 
- Simply run the below git command on your Git client.
  > `bash# git config --global http.sslVerify false`

### Option 2 : Tell Git Where Your Certificate Authority Certificates Are Located

- Another option is to point your Git client towards a folder that contains the Certificate Authority certificate that was used to sign your Git server’s SSL certificate. 
- You may not have one of these if you’re using Self Signed certificates.
- Save the CA certificate to a folder on your Git client and run the following git command to tell your Git client to use it when connecting t the server:
  >`bash# git config --system http.sslCAPath /git/certificates`

Hope either of the above approaches have helped you fix your git SSL issue. 

Thanks!!!
