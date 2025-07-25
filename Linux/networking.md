# Networking


ip adress have 32 bits. every dot is splited by binary number ranging from 0 to 255


Local network

subnet range  subnet mask

192.168.0.0 > 255.255.255.0

example range               fixed first 3 dots cannot change 192.168.0

192.168.0.0 > 255.255.255.0 > 192.168.0.x/255 -  last digit it can be up until 255

2 fixated ranges

192.168.0.0 > 255.255.0.0  > 192.168.x.x/255./255

### Network Commands

```bash
ifconfig
```
gives lots of data about current network

Showing active connections on machine
```bash
netstat
```
current active proccesses and ther connection port etc.
```bash
ps aux
```

getting ip adress of server by looking it up nameserver
```bash
nslookup google.com
```
>>> 
server:     10.0.0.138
address:    10.0.0.138#53

non-authorative answer:
Name:       google.com
Address: 142.250.186.174

Also is possible to do reverse lookup by looking up ip you can find nameservers

Checking for active connection and target machine availability
```bash
ping google.com
```

## Firewall

On most server by default it is running ssh.
And SSH server is listening on `PORT 22`.
## SSH

#ssh - secure shell

2 ways of authentication

1. Username - Password
2. Private Key - Public Key

Fist case is simple one and there is no need explaining.
Second one when it is using private key and public key. 
Public key is shared on Server to accept client public key, and Private key is on client machine.
First Public key is used to allow client connection to server and then it run Private key which is stored on client machine.

## Generating ssh key

Create a new key pair, if needed
Open a terminal and run the following command:
```bash
ssh-keygen
```

alternatively there is more secure version
```bash
ssh-keygen -t rsa
```
rsa key wich is much longer

You will be prompted to save and name the key.

Generating public/private rsa key pair.
Enter file in which to save the key (/Users/USER/.ssh/id_rsa):
Next you will be asked to create and confirm a passphrase for the key (highly recommended):

Enter passphrase (empty for no passphrase):
Enter same passphrase again:
This will generate two files, by default called id_rsa and id_rsa.pub. Next, add this public key.

Add the public key
Copy and paste the contents of the .pub file, typically id_rsa.pub, into the SSH key content field above.
```bash
cat ~/.ssh/id_rsa.pub
```

if public key is not added to server you can add it trought terminal
```bash
cat ~/.ssh/id_rsa.pub | ssh username@server_ip "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"
```
usualy first time username is `root`

base command after public key is added
```bash
ssh root@server_ip
```





