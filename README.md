# Demo DevOps

Express serves `html/index.html` at http://localhost:3000. Run `npm ci`, then `node app.js`.
There is no automated test suite; `npm test` is the package's failing placeholder.

The existing workflow deploys pushes to `main` to an Ubuntu EC2 host. It expects Node via nvm, a checkout at `/home/ubuntu/demo-devops`, and an existing PM2 process named `demo-devops`.
Repository secrets: `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_DEFAULT_REGION`, `AWS_SG_NAME`, `HOST_IP`, `SSH_KEY`.
The AWS identity needs `ec2:AuthorizeSecurityGroupIngress` and `ec2:RevokeSecurityGroupIngress` for that security group, plus `ec2:DescribeSecurityGroups`. SSH ingress is temporarily restricted to the runner's IPv4 /32 and revoked by the cleanup step.
On initial host setup: `pm2 start app.js --name demo-devops`, `pm2 save`, then `pm2 startup` and the command it prints. Never commit private keys.
