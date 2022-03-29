# Creating an SSH Key Pair for User Authentication :

### Choosing an Algorithm and Key Size
SSH supports several public key algorithms for authentication keys. These include:

rsa - an old algorithm based on the difficulty of factoring large numbers. A key size of at least 2048 bits is recommended for RSA; 4096 bits is better. RSA is getting old and significant advances are being made in factoring. Choosing a different algorithm may be advisable. It is quite possible the RSA algorithm will become practically breakable in the foreseeable future. All SSH clients support this algorithm.

dsa - an old US government Digital Signature Algorithm. It is based on the difficulty of computing discrete logarithms. A key size of 1024 would normally be used with it. DSA in its original form is no longer recommended.

ecdsa - a new Digital Signature Algorithm standarized by the US government, using elliptic curves. This is probably a good algorithm for current applications. Only three key sizes are supported: 256, 384, and 521 (sic!) bits. We would recommend always using it with 521 bits, since the keys are still small and probably more secure than the smaller keys (even though they should be safe as well). Most SSH clients now support this algorithm.

ed25519 - this is a new algorithm added in OpenSSH. Support for it in clients is not yet universal. Thus its use in general purpose applications may not yet be advisable.

The algorithm is selected using the -t option and key size using the -b option. The following commands illustrate:

- ssh-keygen -t rsa -b 4096
- ssh-keygen -t dsa 
- ssh-keygen -t ecdsa -b 521
- ssh-keygen -t ed25519


### Specifying the File Name
Normally, the tool prompts for the file in which to store the key. However, it can also be specified on the command line using the -f <filename> option.

```
ssh-keygen -f ~/AJ-key-ecdsa -t ecdsa -b 521
```

### So Far Here  :
```
ssh-keygen -t ecdsa -b 521 -C "Comment_For_SSH_Key"
```
- After running command above First you need to choose a path for the key_file (recommanded to just press **Enter** to get the default path !)

- Then you are asked for a password ! (Choose your own or just press **Enter** to leave empty )
  
### Start SSH-Agent :

```
eval "$(ssh-agent -s)"
```
  
### Add New Key to the agent :
```
ssh-add <Path_to_KeyFile>
```
  
  
### Configure git with identity :

```
git config --global user.email <Your_Email_Address>
```
```
git config --global user.name  <Your_Name>
```
  
