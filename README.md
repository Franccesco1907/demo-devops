como ejecuta la app

npm i / npm install
node app.js

1. crear una EC2 en AWS
   2 Crear una IP elastica
2. Asociar la IP Elastica hacia la EC2
3. conectarnos a la EC2 con la key.pem
4. sudo apt update
5. sudo apt upgrade
6. sudo apt install -y git htop wget
7. instalar node / wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
8. ejecutar estos comandos
   export NVM_DIR="$HOME/.nvm"
   [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
   [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
9. nvm --version
10. nvm install --lts
11. node --version / npm -v
12. cd /home/ubuntu/
13. ssh-keygen  (enter a todo)
14. git clone
15. ubicar el ssh cd /home/ubuntu/.ssh/
16. cat id_rsa.pub  copiar en SSH configuracion en GitHub
17. clonar en el lugar deseado
    git clone **********
18. npm install
19. node app.js
20. crear ruta hacia el puerto 3000 en los "grupos de seguridad" en AWS
21. npm install -g pm2
22. npm install -g pm2
23. pm2 start (codigo de app) --name=(nombre de la app)
24. pm2 save
25. pm2 startup
26. sudo env PATH=$PATH:/home/ubuntu/.nvm/versions/node/v18.17.1/bin /home/ubuntu/.nvm/versions/node/v18.17.1/lib/node_modules/pm2/bin/pm2 startup systemd -u ubuntu --hp /home/ubuntu

crear policy en AWS

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "UpdateIngress",
            "Effect": "Allow",
            "Action": [
                "ec2:RevokeSecurityGroupIngress",
                "ec2:AuthorizeSecurityGroupIngress"
            ],
            "Resource": "arn:aws:ec2:(region):(accountid):security-group/(security-group)"
        },
        {
            "Sid": "DescribeGroups",
            "Effect": "Allow",
            "Action": "ec2:DescribeSecurityGroups",
            "Resource": "*"
        }
    ]
}
