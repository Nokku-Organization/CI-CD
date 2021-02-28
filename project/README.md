### Scenario:
- Client from private-cloud(on-premise) wants to send data (of clicks,access-logs,etc) to Server which is in Public-cloud(AWS).

### Solution:
- Using AWS services like DataSync,StorageGateway(file-gateway),AWS SFTP we can send data to AWS-s3/EFS from on-premise locations(clients)
- Even though Datasync uses TLS protocol but to achieve more Secure solution , we can use AWS services Direct-connect,Site-site-VPN.


- site-site-vpn is hardware IPSEC vpn that enables you to create an encrypted connection over public internet between your vpc and private IT infrastructure
- Direct connect bypasses public-internet and establishes a secure and dedicated connection from your architecture to AWS 
https://www.coresite.com/blog/vpn-or-direct-connect-aws-compared


