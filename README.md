--------------------------------------------------------------------------------------------------- 
# Flask App with MySQL Docker Setup

This is a simple Flask app that interacts with a MySQL database. The app allows users to submit messages, which are then stored in the database and displayed on the frontend.

## Prerequisites

Before you begin, make sure you have the following installed:

- Docker
- Git (optional, for cloning the repository)

## Setup

1. Clone this repository (if you haven't already):

   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   ```

2. Navigate to the project directory:

   ```bash
   cd your-repo-name
   ```

3. Create a `.env` file in the project directory to store your MySQL environment variables:

   ```bash
   touch .env
   ```

4. Open the `.env` file and add your MySQL configuration:

   ```
   MYSQL_HOST=mysql
   MYSQL_USER=your_username
   MYSQL_PASSWORD=your_password
   MYSQL_DB=your_database
   ```

## Usage

1. Start the containers using Docker Compose:

   ```bash
   docker-compose up --build
   ```

2. Access the Flask app in your web browser:

   - Frontend: http://localhost
   - Backend: http://localhost:5000

3. Create the `messages` table in your MySQL database:

   - Use a MySQL client or tool (e.g., phpMyAdmin) to execute the following SQL commands:
   
     ```sql
     CREATE TABLE messages (
         id INT AUTO_INCREMENT PRIMARY KEY,
         message TEXT
     );
     ```

4. Interact with the app:

   - Visit http://localhost to see the frontend. You can submit new messages using the form.
   - Visit http://localhost:5000/insert_sql to insert a message directly into the `messages` table via an SQL query.

## Cleaning Up

To stop and remove the Docker containers, press `Ctrl+C` in the terminal where the containers are running, or use the following command:

```bash
docker-compose down
```

## To run this two-tier application using  without docker-compose

- First create a docker image from Dockerfile
```bash
docker build -t flaskapp .
```

- Now, make sure that you have created a network using following command
```bash
docker network create twotier
```

- Attach both the containers in the same network, so that they can communicate with each other

i) MySQL container 
```bash
docker run -d \
    --name mysql \
    -v mysql-data:/var/lib/mysql \
    --network=twotier \
    -e MYSQL_DATABASE=mydb \
    -e MYSQL_ROOT_PASSWORD=admin \
    -p 3306:3306 \
    mysql:5.7

```
ii) Backend container
```bash
docker run -d \
    --name flaskapp \
    --network=twotier \
    -e MYSQL_HOST=mysql \
    -e MYSQL_USER=root \
    -e MYSQL_PASSWORD=admin \
    -e MYSQL_DB=mydb \
    -p 5000:5000 \
    flaskapp:latest

```

## Notes

- Make sure to replace placeholders (e.g., `your_username`, `your_password`, `your_database`) with your actual MySQL configuration.

- This is a basic setup for demonstration purposes. In a production environment, you should follow best practices for security and performance.

- Be cautious when executing SQL queries directly. Validate and sanitize user inputs to prevent vulnerabilities like SQL injection.

- If you encounter issues, check Docker logs and error messages for troubleshooting.

```

this is hstory of cmds which i used while doing this preoject
2  sudo apt-get install nginx
    3  sudo apt install nginx
    4  apt-get update
    5  sudo apt-get update
    6  sudo apt-get install nginx
    7  systemctl status nginx
    8  cd /var
    9  ls
   10  cd www
   11  ls
   12  vim index.html
   13  sudo vim index.html
   14  ls
   15  vi index.html
   16  sudo su
   17  ls -a
   18  cd .ssh
   19  ls
   20  ssh-keygen
   21  ls
   22  ssh -i id_ed25519 ubuntu@52.48.108.193
   23  clear
   24  cd ..
   25  ls
   26  cd /var
   27  ls
   28  cd log
   29  ls
   30  cd nginx/
   31  cat access.log 
   32  ping 52.48.108.193
   33  ls
   34  mkdir devops
   35  mkdir -p scripts
   36  ls
   37  cd scripts/
   38  vim hello.sh
   39  echo $SHELL
   40  vim hello.sh
   41  chmod 754hello.sh
   42  chmod 754 hello.sh
   43  ./hello.sh
   44  vim hello.sh
   45  ls
   46  ./hello.sh
   47  ls
   48  cd scripts/
   49  ls
   50  vim hello.sh 
   51  ./3_idiots.sh
   52  vim hello.sh 
   53  ls
   54  cd scripts/
   55  ls
   56  vim hello.sh 
   57  ./hello.sh 
   58  vim hello.sh 
   59  ./hello.sh raju farahan rancho
   60  vim arg.sh
   61  ./arg.sh admin admin
   62  chmod 764 arg.sh
   63  ./arg.sh admin admin
   64  vim arg.sh
   65  ls
   66  git -v
   67  git --version
   68  cd scripts/
   69  ls
   70  cd scripts
   71  git init
   72  ls
   73  ls -a
   74  git status
   75  git add arg.sh 
   76  git status
   77  git rm --cached arg.sh 
   78  git status
   79  git add arg.sh 
   80  git commit -m "added arg script"
   81  rm arg.sh 
   82  git restore arg.sh 
   83  rm arg.sh 
   84  ls
   85  git restore arg.sh
   86  ls
   87  git config --global user.name deepak__4151
   88  git config --global user.email deepakpateliit21@gmail.com
   89  touch deep.txt
   90  git add deep.txt 
   91  git commit -m deep.txt 
   92  ls
   93  ls -a
   94  git status
   95  git branch
   96  git checkout -d dev
   97  git checkout -b dev
   98  git status
   99  git sttaus
  100  vim from_dev.txt
  101  git add from_dev.txt 
  102  git commit -m "added dev file"
  103  ls 
  104  git sttus
  105  git status
  106  git checkout master
  107  ls
  108  git add hello.sh text.txt 
  109  git commit -m "added both files"
  110  ls
  111  git status
  112  git log --oneline
  113  git checkout dev
  114  git status
  115  git log --oneline
  116  git status
  117  git switch master
  118  git merge dev
  119  ls
  120  cs devops/
  121  cd devops/
  122  ls
  123  git branch
  124  cd ..
  125  cd scripts/
  126  git branch
  127  ls
  128  git branch
  129  git switch dev
  130  vim backup.sh
  131  rm -rf backup.sh 
  132  vim hello.sh
  133  cat hello.sh 
  134  cat arg.sh 
  135  vim arg.sh 
  136  ./arg.sh ram rahim
  137  git log
  138  git log --one line
  139  cd scripts/
  140  ls
  141  vim demo_dev.txt
  142  git add demo_dev.txt 
  143  git commit -m  "added a fine commit"
  144  vim demo_dev.txt 
  145  git add demo_dev.txt 
  146  git commit -m "added a wrong commit"
  147  vim demo_dev.txt _
  148  git log --oneline
  149  git add demo_dev.txt 
  150  git commit -m " added a fime commit"
  151  git log --oneline
  152  git log
  153  git revert https://drive.google.com/file/d/10-K1dTSfjwQgh6iwcPsesTcb_gQfdvGW/view?usp=drive_link
  154  git revert 4d2406c
  155  git status
  156  vim demo_dev.txt 
  157  git status
  158  git add demo_dev.txt 
  159  git status
  160  git revert --continue
  161  git log --oneline
  162  docker ps
  163  whoami
  164  docker run -d -p 80:80 nginx
  165  sudo systemctl stop nginx
  166  docker run -d -p 80:80 nginx
  167  sudo apt-get update
  168  sudo apt-get install docker.io
  169  docker --version
  170  system ctl status docker
  171  systemctl status docker
  172  docker images
  173  docker containers
  174  docker ps
  175  cat /etc/group
  176  whoami
  177  sudo uermod -aG docker $USER 
  178  sudo usermod -aG docker $USER 
  179  cat /etc/group
  180  docker ps
  181  man newgrp
  182  newgrp docker
  183  docker login
  184  docker run -it buntu
  185  docker ps
  186  docker status
  187  docker ps
  188  docker stop 52.17.11.4
  189  docker stop nginx
  190  docker stop 955
  191  docker ps
  192  docker ps -a
  193  ls
  194  cd devops/
  195  ls
  196  cd .
  197  cd scripts
  198  cd scriptscd ..
  199  cd ..
  200  cd scripts/
  201  ls
  202  cd ..
  203  cd devops/
  204  cd github_repos/
  205  git clone https://github.com/DEEPAK4151/java-quotes-app.git
  206  ls
  207  cd java-quotes-app/
  208  cd src/
  209  ls
  210  cd ..
  211  ls
  212  rm -rf Dockerfile 
  213  vim Dockerfile
  214  ls
  215  vim Dockerfile 
  216  cat Dockerfile 
  217  docker build -t java-quotes:latest .
  218  docker images
  219  docker run -d -p 8000:8000 --name java-quotes-app java-quotes:latest
  220  ls
  221  cd scripts/
  222  ls
  223  docker ps 
  224  docker stop 2ac
  225  docker stop 2aa
  226  docker ps -a
  227  docker system prune
  228  ls
  229  docker ps
  230  docker ps -a
  231  ls
  232  cd ..
  233  cd devops/
  234  ls
  235  cd github_repos/
  236  ls
  237  git clone https://github.com/DEEPAK4151/flask-app-ecs-docker-.git
  238  cd flask-app-ecs-docker-/
  239  rm -v Dockerfile
  240  LS
  241  ls
  242  vim Dockerfile
  243  docker build - t pyhton-app:latest .
  244  docker build - t python-app:latest .
  245  ls
  246  cat Dockerfile-multi 
  247  LS
  248  ls
  249  rm -v Dockerfile-multi 
  250  docker build - t python-app:latest .
  251  docker build -t python-app:latest .
  252  vim Dockerfile 
  253  docker build -t python-app:latest .
  254  vim Dockerfile 
  255  docker build -t python-app:latest .
  256  docker images
  257  docker run -d -p 80:80 python-app
  258  docker log de
  259  docker logs de
  260  docker ps
  261  docker stop de
  262  ls
  263  cd devops
  264  cd github_repos/
  265  ls
  266  cd flask-app-ecs-docker-/
  267  vim Dockerfile_multi_stage
  268  ls
  269  cd devops/
  270  ls
  271  cd github_repos/
  272  ls
  273  docker pull mysql
  274  docker run -d -e MYSQL_ROOT_PASSWORD=root mysql:latest
  275  docker images
  276  docker ps
  277  docker exec -it 2ed bash
  278  docker volumes
  279  docker volume
  280  docker volume ls
  281  docker volume create mysql-data
  282  docker inspect mysql-data 
  283  ls
  284  docker volum ls
  285  docker volume ls
  286  docker ps
  287  docekr ps -a
  288  docker ps -a
  289  docker run -help
  290  docker network ls
  291  docker run de61
  292  docker start de61da53ddaa
  293  docker ps
  294  cd devops/
  295  cd github_repos/
  296  git clone https://github.com/DEEPAK4151/two-tier-flask-app.git
  297  df -h
  298  free -h
  299  sudo su
  300  free -h
  301  sudo su
  302  free -h
  303  sudo sysctl -w vm.drop_caches=3
  304  df -h
  305  sudo sync
  306  echo 3 > /proc/sys/vm/drop_caches
  307  sudo su echo 3 > /proc/sys/vm/drop_caches
  308  sudo su
  309  free -h
  310  ls
  311  cd two-tier-flask-app/
  312  ls
  313  cat Dockerfile
  314  vim .env
  315  cat .env
  316  ls
  317  docker build  -t flask-app .
  318  LS
  319  ls
  320  cd devops/
  321  ls
  322  cd ..
  323  cd scripts/
  324  ls
  325  docker images
  326  docker ps
  327  docker ps -a
  328  ls
  329  docker ps
  330  docker network
  331  docker network ls
  332  docker network create man
  333  docker network ls
  334  docker network rm man
  335  docker network ls
  336  ls
  337  cd ..
  338  ls
  339  cd devops/
  340  cd github_repos/
  341  ls
  342  free -h
  343  sudo sync && echo 3 | sudo tee /proc/sys/vm/drop_caches
  344  free -h
  345  cd two-tier-flask-app/
  346  cat Dockerfile
  347  ls
  348  touch .env
  349  vim .env
  350  docker build -t flaskapp .
  351  docker ps
  352  docker ps -a
  353  docker rm 2ed6c566e405
  354  docker ps -a
  355  docker rm de61da53ddaa
  356  docker network create two-tier
  357  docker network ls
  358  docker inspect de61da53ddaa
  359  docker inspect 710dd15901ca
  360  docker run -d --name mysql -v mysql_data:var/lib/mysql --network=two-tier -e MYSQL_PASSWORD=admin  -e MYSQL_USER=admin -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATABASE=tws_db -p 3306:3306 mysql:latest
  361  docker inspect two-tier 
  362  docker network ls
  363  docker ps
  364  docker ps -a
  365  ls
  366  cd devops/
  367  ls
  368  cd github_repos/
  369  ls
  370  docker ps 
  371  cd two-tier-flask-app/
  372  ls
  373  cat .env
  374  df -h
  375  free -h
  376  sudo sh -c "sync; echo 1 > /proc/sys/vm/drop_caches"
  377  free -h
  378  cat Dockerfile
  379  cat .env
  380  docker build -t flask-app .
  381  docker ps
  382  docker run -d --name mysql -v mysql_data:/var/lib/mysql --network=two-tier -e MYSQL_PASSWORD=admin -e MYSQL_USER=admin -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATABASE=tws_db -p 3306:3306 mysql:latest
  383  docker ps
  384  docker network ls
  385  docker inspect 710dd15901ca
  386  docker images
  387  DOCKER PS
  388  docker ps
  389  docker run -d --name flask-app --network=two-tier -e MYSQL_PASSWORD=admin -e MYSQL_USER=admin -e MYSQL_DB=tws_db -p 5000:5000 flask-app:latest
  390  docker ps
  391  docker logs 47a
  392  docker rm flask-app
  393  docker run -d --name flask-app --network=two-tier -e MYSQL_PASSWORD=admin -e MYSQL_USER=admin -e MYSQL_DB=tws_db -e MYSQL_HOST=mysql -p 5000:5000 flask-app:latest
  394  docker ps
  395  docker network ps
  396  docker inspect two-tier
  397  docker ps
  398  docker exec -it d19f5 bash
  399  history
