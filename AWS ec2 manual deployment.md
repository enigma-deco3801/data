# AWS ec2 manual deployment
___
### Overview
![[Pasted image 20220913185734.png|400]]

___
### Process
- **Download AWS CLI**
	- `curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"` 
	- `unzip awscliv2.zip` 
	- `sudo ./aws/install`

- **Create and configure `ec2` instance**
	- Add tag `Name: <APP_NAME>`
	- Add security group: `<APP_NAME>-http-ssh-access`
		- Add rule `Type` : `HTTP`
		- Select key-pair `existing vockey | RSA` option
	- copy the `public IPv4 address`
	- download key-pair - `aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem`

- **ssh into ec2**  
	- `ssh -i ~/.ssh/<SSH_KEY_PAIR>.pem ec2-user@<IPv4 address>`
- **install `node` on ec2**
	- `curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -`
	- `sudo apt install nodejs`
- **install `pm2`** 
	- so that server can run even after terminal closing
- **`git clone` the repo**
- **start the app**
	- `pm2 start npm --name "<APP_NAME>" -- start`

___
[[deploy-ec2.pdf]]
[deploy nodejs on ec2](https://ourcodeworld.com/articles/read/977/how-to-deploy-a-node-js-application-on-aws-ec2-server)
