# WordPress + MySQL with Docker Compose

This project sets up a local WordPress environment using Docker Compose.

### Requirements
- Docker
- Docker Compose

### Steps to Run

```bash
 sudo apt-get update
docker --version
docker-compose --version
docker compose version
# start with 
mkdir wordpress_project
cd wordpress_project
# Start containers in detached mode
sudo apt update
sudo apt install docker-compose -y
sudo apt update
nano docker-compose.yml

services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: mypassword
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpressuser
      MYSQL_PASSWORD: wordpress

  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - "8080:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpressuser
      WORDPRESS_DB_PASSWORD: wordpress

volumes:
  db_data:

docker compose up -d
docker ps
#git

---

### ✅ To Add to GitHub

From the project root:

```bash
git init
git add .
git commit -m "Initial commit: WordPress + MySQL using Docker Compose"
git branch -M main
git remote add origin https://github.com/yourusername/wordpress-docker.git
git push -u origin main

Fix Option B (Advanced – Use SSH)
If you prefer SSH, make sure:

You’ve created an SSH key using:

bash
Copy code
ssh-keygen -t ed25519 -C "your_email@example.com"
You’ve added your public key (~/.ssh/id_ed25519.pub) to GitHub under
GitHub → Settings → SSH and GPG Keys

You’ve tested the connection:

bash
Copy code
ssh -T git@github.com
Then try:

bash
Copy code
git remote add origin git@github.com:Bhaskar265/wordpress_project.git
git push -u origin main
