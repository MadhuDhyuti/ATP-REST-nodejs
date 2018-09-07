# ATP-REST-nodejs
REST APIs for Oracle Autonomous Transaction Processing Service written in node.js

These scripts are written as modules so that all you need to do is add relevant tenant information in auth.js and run individual scripts to interact with the service.


Download and use these node.js scripts to interact with Oracle's Autonomous Database Service over https 

Steps:

1. Download folder to your local machine - $ git clone https://github.com/kbhanush/ATP-REST-nodejs

2. In folder ATP-REST-nodejs, run $npm install, to install dependent packages https-signature and jssha. 

3. Generate an ssh key pair in pem format using

  $ openssl genrsa -out ~/oci_api_key.pem -aes128 2048
  
  Now, using this private key, generate a public key
  
  openssl rsa -pubout -in ~/oci_api_key.pem -out ~/oci_api_key_public.pem
  
Log into your Oracle Cloud Account, Go to OCI Console - Identity --> Users -->Go to your user page and click ‘Add public Key’
Cut and paste api_key_public.pem

You will see the key’s fingerprint on the console below

Now, modify auth.js with your tenant auth information. Replace tenancyId, authUserId, keyFingerprint, privateKeyPath. 

Add  compartmentIds you wish to create artifacts in.


4. headers.js sets up https headers needed for the request object using auth information provided. You do not need to change anything in there.

5. regions.js contains REST endpoints for various OCI services in different regions. You do not need to change anything in there unless endpoints changes or new regions/services are added.

6. Run any of the sample scripts provided. 

$ node listAutonomousDatabases.js

You can create your own scripts by editing some of the samples and using Oracle REST API documentation.


