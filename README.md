### 1️⃣ **Using `docker-compose.yml` (Recommended)**  
This makes it easier to manage your MongoDB container.  

#### 📂 **Project Structure**  
```
mongodb-docker-setup/
│── docker-compose.yml
│── README.md
```

#### 📝 **docker-compose.yml**
```yaml
version: '3.8'

services:
  mongodb:
    image: mongo
    container_name: mongodb-container
    restart: always
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: password
    volumes:
      - mongodb_data:/data/db

volumes:
  mongodb_data:
```
✅ This ensures data persistence and makes it easy to start/stop the container.  

#### 🚀 **How to Use**
# Start MongoDB container
```sh
docker-compose up -d  
```
# Run MongoDB in Shell
```sh
docker exec -it mongodb-container mongosh -u admin -p password
```

# Stop MongoDB container
```sh
docker-compose down  
```
# Check running containers
```sh
docker ps  
```

# Remove all containers & volumes (if needed)
```sh
docker-compose down -v
```

---

### 2️⃣ **Using a Direct `docker run` Command**  
If you **don't** want to use `docker-compose`, you can use your **`docker run`** command in a `README.md` for documentation.


# MongoDB Docker Setup

## 🚀 Start MongoDB Container
Run the following command to start MongoDB in Docker:

```sh
docker run -d \
  --name mongodb-container \
  -p 27017:27017 \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=password \
  -v mongodb_data:/data/db \
  mongo
```

## 🛑 Stop MongoDB
```sh
docker stop mongodb-container
```

## 🚀 Start Again
```sh
docker start mongodb-container
```

## 🔥 Remove the Container
```sh
docker rm -f mongodb-container
```

---

### 📌 **What Should You Do?**
- **Use `docker-compose.yml`** for better management ✅  
- **Document `docker run` in `README.md`** for reference  
