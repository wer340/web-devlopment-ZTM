ssh  secure shell protocol you heard protocol http https ftp\
these are al ways to connect to computers and have a shared agreement of how to communicate that is their protocol  or a language that they can speak and ssh is a way for machine to communicate with one another.\
http  hypertext transfer protocol allows you to send file over the internet like a html css and java script files between browser and servers .\
FTP or file transfer protocol allows you to send file as well and is often used when you upload files something like hostgator or generic hosting platform from your computer .\
HTTPS  is similar to http  but it is encrypted that means third parties cant read the file being transferredif they intercept the message \
another protocol  like IMAP  allows to send mail \
SSH  the another protocol to communicate  between two computers over the internet it allows user to share files as well as control and modify remote computer over the internet \
it was created as a secure way of communication which again encrypts all data so bad actors cants monitor\
 a web browser uses the https protocol to talk with servers and display web sites A **shell**  needs a certain protocol to enable data exchange or communication between two devices and not just a browser and a server.  \
advantage ssh protocol :  secure transfer   from operating system client(shell)  to server (shell) \
## use it 

## ssh {user} @ {host}
in mac and linux  use the ssh  is  simple  but in windows  you will need to utilize an ssh client to open a ssh connections and the most popular one in windows  is called putty which  i will include in the resources for this lesson by using ssh we can connect \
### ssh {user} @ {host} 
ssh key  command structure your system that you want to open an encrypted secure shell connection .\
User represents the account you want to access  for example you may want to access the root user which is basically synonymous for system administrator with complete rights to modify anything on the system which can be dangerous at time \
Host refer to the computer you want to access this can be an IP address or domain name \
remember how when we clone something from a github we have two option we have use https which you are most likely used before and use ssh and remember how with https you had to enter your password all the time to clone the repo \

## use 
open the shell in your computer   ☕  assume  buy a  ubuntu server in digitalocean\
connect to shell of server ▶`ssh root@167.99.146.57` \
`root@ubuntu-s-1cpu-gb-nyc1-01:~#`\
install git in server ▶`root@ubuntu-s-1cpu-gb-nyc1-01:~#sudo apt-get git`\
install a package from github into your server `root@ubuntu-s-1cpu-gb-nyc1-01:~#git clone github package`\
make a folder in your server`root@ubuntu-s-1cpu-gb-nyc1-01:~# mkdir hi`\
install nodejs ▶`root@ubuntu-s-1cpu-gb-nyc1-01:~# sudo apt-get install nodejs `\
show version of nodejs ▶`root@ubuntu-s-1cpu-gb-nyc1-01:~# nodejs -v `\
another thing  folder my computer bring up to server  first  time exit of ssh \
`root@ubuntu-s-1cpu-gb-nyc1-01:~# exit`\
install command called rsync 
`~/Desktop rsync`\
then (superawsome.com is a name of folder ) `~/Desktop cd  superawsome.com/`\
copy all file in folder to server`~/D/superawsome.com/ rsync -av . root@167.99.146.57:~/superawsome.com`\
see folder of file`root@ubuntu-s-1cpu-gb-nyc1-01:~# ls`\

## 1️⃣symmetrical Encryption   2️⃣Asymmetrical Encryption   3️⃣Hashing 
there are three techniques  used in ssh 

## encryption 
is a way to hide or essentially jumble up a lets say a piece of text  and so something that its impossible for a third party or someone to read without some sort of a way to decrypting

### 1️⃣symmetrical Encryption
this method uses one secret key for both the encryption and decryption by both parties\
but what is one problem you notice here ? anyone has the key can decrypt the message \
so we have to get this key in a secure way so that other people cant use it as well or cant find out what is it and this is done through what we call a **key exchange algorithm** . a secure way to exchange these keys without any bad actors intercepting it.\
the key is never actually transmitted between the client and the host instead the two computers share public pieces of data and then manipulate it to independently calculate the secret key.\
so even if another machine capture the publicly shared data it wont be able to calculate the key because well this key  exchange algorithm which for now  is kind of not known\
so without them having this key exchange algorithm they wont be able to ever find out key\
**the secret key is specific to each ssh session and generated prior to something called Kline s authentication** ** 

## 2️⃣Asymmetrical Encryption
public key + private key  pair \
public key share with altogether   but secret key  absolutes that you shouldn't never ever share with anybody\
these public keys are linked with the private key in terms of functionality \
**the private key cannot mathematically compute from the public key**  are the relationship a little bit complex but a message shut is encrypted by machines public key can only be decrypted by the same machine private key \
and **its what we call a one way relationship**\
its this form of encryption with ssh is a actually only used during the key exchange algorithm of symmetric encryption\
exchange public key for connection **using something called the Diffie Hellman exchange** \
`key exchange algorithm` and `the Diffie Hellman exchange` makes it possible for each party to combine their own private data with public data  are from other system to arrive in a identical secret session key\
this type of encryption is everywhere

### 3️⃣Hashing 
most of the ssh connections use symmetric encryption  the idea behind that asymmetric encryption is used only to share a secret key and then finally using that key that is symmetric encryption for further communication so it s fast \
now once a secure symmetric communication has been established the server uses the client s public key \
#### problem
if someone can sit in the middle and pretend to be the other  and tamper or modify the message  they can just have key exchange between one another and thr information came flow through that middleman\
now to solve one of these problem we talk about a something **called hashing** is another form of cryptography used in secure shell connection \
that a gets and there one way because if i hash hello its going to run through a function that spits out jibberish really fast with the trick being that we have no idea how to get back to the whole text \
using the third technique hashes we are able to verify the authentication of the message  this is done using something **called HMX** or hash based message Authentication code\
first password is hashed after  is sent  ,receiver have a symmetric key  same thing with transmitter   so check hashed message  whether is true or false \  

## password ssh 
two way authenticate    most user is used type password in ssh
 `~/Desktop ssh root@167.99.146.57`\
 `(current) UNIX password : `\

### second way  for avoid using password 
that is hassle  every time login  so using ssh we are going to use something called RSA which allows us to provide or prove the identity of the person without a password \
`~/desktop  cd ~/.ssh`\
`~/.shh open .`\
`~/.shh ls`\
see config id_rsa  id_rsa.pub  key_backup/ known_hosts\
for commutate for host  by second way  need to pub and private key  that cat generate in computer\
`~/.ssh ssh-keygen -C "tets@gmail.com"`    -C  flag is symbol of comment word \
if check .ssh folder  `~/.ssh  ls`  can see new key pair `id_rsa.pub` you can shared for everyone but `id_rsa` never ever shared anyone \
`~/.ssh pbcopy < ~/.ssh/id_rsa.pub`   copy to clipboard\
`~/.ssh ssh root@167.99.146.57`\
lets again do it  for server side \
`root@ubuntu-s-1cpu-gb-nyc1-01:~# ls -a`  see check is exist .ssh folder?\
`root@ubuntu-s-1cpu-gb-nyc1-01:~# mkdir .ssh` if doesn't exists  create it\
`root@ubuntu-s-1cpu-gb-nyc1-01:~#cd .ssh`\
`root@ubuntu-s-1cpu-gb-nyc1-01:~/.ssh# ls ` see `authorized_keys`  `known_hosts`  \
`root@ubuntu-s-1cpu-gb-nyc1-01:~/.ssh# nano authorized_keys`   paste public key thats previously generate in computer  reminder nano is text editor\
`~/.ssh ssh root@167.99.146.57`\
if you have  error  that say permission deny  gain little bit tricky \
`~/.ssh  ssh-add ~/.ssh/your_id_rsa` introduce private key to  ssh\
`~/.ssh ssh root@167.99.146.57`\
## windows 
Type `ssh-agent bash` and press Enter.\
Type`ssh-add ~/.ssh/id_rsa_digitalocean` and press Enter.You should get confirmation of Identity added.\
Try connecting to your digital ocean account again via SSH. Now it shouldn't ask you for the password!\
Recommended ssh-keygen command:`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

## github
`~/Desktop ssh-add -l`  list of identity i have\
`~/Desktop ssh-add -D` remove all identity \
`~/Desktop ssh-add  ~/.ssh/id_rsa_digital_ocean2` \
 `~/Desktop ssh-add -l` \
 `git clone git@github.com:StevieChicks/fork-and-clone.git`\

 ### Theoretically if he had lets say five different computers lets say are raspberry pies you can do something\
`~/Desktop ssh -tt pi@10.2.1.12  ssh -tt pi@10.2.1.14  ssh -tt pi@10.2.1.16   ....`


# review

1-Diffie-Hellman key exchange  provide a way to share a shared secret \
2-Arrive at symmetric key  so that we have two computer who are able to talk to one another \
3-make sure of no funny business  hashing \
4-Authenticate User  two way   1️⃣provide password  2️⃣we could do something like rsa wich aallows us to prove the identity of the person without a password  \

so you use see  now how  these four step using those three technologies the symmetric encryption asymmetric encryption and hashing are able to combine all of these together  to make sure that we can communicate securely 
