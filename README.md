# docker-compose
nextcloud-psql


version: '3.7'
services:
  drive:
    image: nextcloud:apache
    environment:
      - POSTGRES_HOST=db
      - POSTGRES_PASSWORD=drive@123
      - POSTGRES_DB=drivedb
      - POSTGRES_USER=nextcloud
    ports:
      - 8080:80
    restart: always
    volumes:
      - drive_data:/var/www/html
  db:
    image: postgres:alpine
    environment:
      - POSTGRES_PASSWORD=drive@123
      - POSTGRES_DB=drivedb
      - POSTGRES_USER=nextcloud
    restart: always
    volumes:
      - db_data:/var/lib/postgresql/data
volumes:
  db_data:
  drive_data:
