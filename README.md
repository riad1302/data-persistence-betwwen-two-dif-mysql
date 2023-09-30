# data-persistence-betwwen-two-dif-mysql
Data persistence between two different Mysql databases hosted on two separate EC2 instances using Elastic Block Storage(EBS)

# create aws EC2 instance like old-1
conected to old-1

    sudo apt update
## docker install

    sudo apt-get update
    sudo apt-get install ca-certificates curl gnupg
    sudo install -m 0755 -d /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    sudo chmod a+r /etc/apt/keyrings/docker.gpg
    
    # Add the repository to Apt sources:
    echo \
    "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update

    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

## make folder

    mkdir mydata 

## make docker compose file

    nano docker-compose.yml

## copy old-1 docker-compose.yml file and paste 

## check persitance volume

    lsblk

## check file system

    sudo file -s /dev/xvdb

## make file system

    sudo mkfs -t xfs /dev/xvdb

## mount file system 

    sudo mount /dev/xvdb /home/ubuntu/mydata

## docker up

    sudo docker compose up -d

## check docker container

    sudo docker ps

## exec docker container

    sudo docker exec -it db bash
    mysql -u root -p
    #password is riad
    show databases;
    use db;
    show tables;
    # no table found

    #create table
    CREATE TABLE person (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    age INT
    );
    
    # insert data in this table
    INSERT INTO person (name, age) VALUES
    ('John Doe', 30),
    ('Jane Smith', 25),
    ('Bob Johnson', 40),
    ('Alice Brown', 35),
    ('Eva Davis', 28);
    
    exit;
    exit;
    cd mydata
    ls 
    # show data

# create aws EC2 instance like new-1




