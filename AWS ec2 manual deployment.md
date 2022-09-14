# AWS ec2 manual deployment
Prereq: [[AWS Configuration]]
___
### Overview
![[Pasted image 20220913185734.png|400]]

___
### Process
- **[[AWS Configuration#Installing CLI|Download AWS CLI]]**
- **Create and configure `ec2` instance**
	- Add tag `Name` : `<APP_NAME>`
	- Add security group: `<APP_NAME>-http-ssh-access`
		- Add rule `Type` : `HTTP`
		- Select key-pair `existing vockey | RSA` option
	- copy the `public IPv4 address`
	- download key-pair - `aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem`

- **ssh into ec2**  
	- make sure key-pair is private : `chmod 400 ~/.ssh/<SSH_KEY_PAIR>.pem`
	- `ssh -i ~/.ssh/<SSH_KEY_PAIR>.pem <username>@<IPv4 address>`

![[Pasted image 20220914203349.png|400]]

- **install `node` and `npm` on ec2**
	- `curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -`
	- `sudo apt install nodejs`
	- `sudo apt install npm`

- **install `pm2`** 
	- so that server can run even after terminal closing
	- `npm install -g pm2`

- **`git clone` the repo**
- **start the app**
	- `pm2 start npm --name "<APP_NAME>" -- start`
	- `pm2 startup`

- **monitor the process**
	- `ps aux | grep -i <APP_NAME>`
	- `pm2 stop all`


<div style="background-color: white; padding: 10px; border: 1px solid black;">
 If all goes well, the nodejs app will now be running on the port 5000. But 5000 is generally not reachable from the outside, so we have to connect <b>5000</b> to <b>80 (HTTP) and 443 (HTTPS)</b> through an <b><code>nginx</code></b> reverse proxy.
</div>

[[nginx reverse proxy]]

___
[[deploy-ec2.pdf]]
[deploy nodejs on ec2](https://ourcodeworld.com/articles/read/977/how-to-deploy-a-node-js-application-on-aws-ec2-server)
