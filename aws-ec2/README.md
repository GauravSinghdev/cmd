## __GET ssh connect to VM ec2 server__
    wsl -d ubuntu
(get inside WSL Windows Subsystem for Linux)
    
    chmod  700 mykey.pem
(permission edit for the file)
    
    ssh -i mykey.pem ubuntu@YOUR_EC2_PUBLIC_IP
(connect it to ec2 machine)


## __Install NVM for Node installation__

    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
(install NVM)
    
    source ~/.bashrc 
(executes the updated configuration immediately, without requiring you to close and reopen your SSH session.)
    
    nvm install --lts
(Installs the latest Node.js LTS version)


## __Install PM2__

    sudo npm install -g pm2
    pm2 start npm --name "react-app" -- run preview -- --host 0.0.0.0 --port 3000
    pm2 status
    pm2 logs react-app
    pm2 restart react-app
    pm2 stop react-app
    pm2 delete react-app

*__GENRAL:__*
    
    npm run build
    pm2 serve dist 3000 --name react-app --spa
    pm2 save

__*OR JUST *__
    
    npm run build
    npm install -g serve
    pm2 serve dist 3000 --name react-app --spa

*__SOMETHING IDK:__* 
(Keep React running after EC2 restarts)
    pm2 startup
    pm2 save


## Install Nodejs with sudo

    sudo apt update
    sudo apt install nodejs