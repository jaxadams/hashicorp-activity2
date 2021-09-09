---
title: "Retrive Vault Token 2.5"
---

There is a single HashiCorp Vault cluster provisioned at the following IP address:

 ### `scenario-cluster-vault`:
* Vault Address: 127.0.0.1:8200
* Vault Token: s.f7Ea3C3ojOYE0GRLzmhSG

The AppRole auth method has been enabled on the approle/path. A role has been created and has the following properties:

* Role Name: appy7
* Vault Policy: policy7
* Roll ID: xxxxxxxx-xxxxxxxx-xxxxxxxx-xxxxxxxxxxx

### Application Server:

Additionally, there is an application server which requires the use of the Vault Agent to retrieve and manage a Vault Token to be stored in a local file. The Vault Binary is already in the $PATH. 

* Server Name: `scenario-node-appserver`
* Server Address: <IP_Address>
* Vault Agent Config File: /etc/vault/agent7.hcl
* Sink Location: /etc/vault/token.json

### Instructions

Bucky must configure Vault Agent Auto-Auth and Token Sink securely. Bucky has an application that needs to retrieve credentials from the Vault, even though the application was not architected to interact directly with the Vault. 

1. Bucky uses the Vault Agent to retrieve a Vault token and keep it renewed automatically. 
2. Bucky must configure the application server to use the Vault Agent to retrieve a Vault Token using the information provided above. 

    * The Vault Agent should use approle for authentication; therefore, a SecretID needs to be generated in the Vault. 
    * When retrieving the token from the vault, the resulting token should be protected using response wrapping on the Auth method. Write the token to the token.json file path. 

### Important Notes

* Validate the configuration by viewing the contents of the sink. 
* If a token does not exist, the configuration is not correct.
