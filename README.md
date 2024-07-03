## Prerequisites

Make sure you have the following installed on your system:

- Git
- Docker
- Docker Compose
- PHP
- Composer

## Setup Instructions

1. **Clone the Repository**:
```
   sh
   git clone https://github.com/mr-sobolev/laraver_test
   cd laravel_test
```

Initialize and Update submodules:
```
git submodule init
git submodule update
```
2. **Need copy config to project**:
```
sudo cp ./config/.env ./laravel_api/www/
```
3. **Change Ownership of Project Files**:
```
sudo chown -R $(whoami):$(whoami) *
```
4. **Install Composer Dependencies**:
```
composer install
```
5. **Start Docker Containers**:
```
docker-compose up
```

**Access the Application**:
Open your browser and go to http://localhost:9009/

Database Setup

This project uses PostgreSQL as its database.
Credentials
```
    Username: postgres
    Password: test_task_!
```
**Create Databases**
laravel_db_api
laravel_db_fdw_api

**Run Migrations**

```
docker-compose exec app php artisan migrate
```

**The final need restart docker-compose application**
