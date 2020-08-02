# 前端
切记要用root用户，ubuntu的root密码为123456
1，执行nvm -v没有相关命令，则执行以下两条命令
export NVM_DIR="/root/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"

2，执行前端项目
若npm -v有版本说明已安装，下面两条指令可以略过
npm config set registry https://registry.npm.taobao.org
npm install

NODE_ENV=development npm run build:dll

export TARGET=http://127.0.0.1:8000

npm run dev

用http://127.0.0.1:8080/访问即可

3, 启动docker命令
 docker start oj-redis-dev oj-postgres-dev


4，启动后端项目
python3.7 manage.py runserver

5,合并一个本地项目和github上的一个项目
git remote add upstream <原仓库github地址>    #配置当前当前fork的仓库的原仓库地址
git fetch upstream    #获取原仓库的更新
git merge upstream/master    #合并到master分支

6，持续构建有关
1）先提交代码并打tag，然后travis自动构建；
2）然后再到阿里云去构建镜像
3）最后再到OnlineJudgeDeploy项目下执行指令：docker-compose pull && docker-compose up -d

7,保存镜像到tar包
docker save -o oj-backend_v16.tar image_id

8,
docker tag 06ec1f1c9dc4 oj-backend:v16 //打标签

项目信息：
前端：E:\kaoshi\newfe\OnlineJudgeFE
后端：E:\kaoshi\OnlineJudge
