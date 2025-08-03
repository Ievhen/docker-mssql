# MS SQL Server Docker Compose Setup

This repository provides a Docker Compose configuration to deploy a Microsoft SQL Server 2022 instance using the official Microsoft container image. It includes a persistent volume for data storage and environment variables for easy configuration. This setup is for development and testing environments.

## Setup Instructions

1. **Clone the Repository**

   ```bash
   git clone https://github.com/Ievhen/docker-ftp-sync.git
   cd docker-mssql
   ```

2. **Configure Environment Variables**

   Create a `.env` file in the project root and add the following:

   ```bash
   MSSQL_SA_PASSWORD=YourStrong@Passw0rd
   ```

   Ensure the password meets SQL Server's complexity requirements (at least 8 characters, including uppercase, lowercase, numbers, and special characters).

3. **Create Docker Volume**

    The setup uses a Docker volume named mssql_vol to persist SQL Server data. The volume is automatically created when you run Docker Compose, but you can manually create/change it if needed:

    ```bash
    docker volume create mssql_vol
    ```

4. **Run Docker Compose**

   Start the SQL Server container with:

   ```bash
   docker-compose up -d
   ```

5. **Connect to SQL Server**

   Use a database client (e.g., SQL Server Management Studio, DBeaver) to connect to the server:

   - **Host**: `localhost`
   - **Port**: `1433`
   - **Username**: `sa`
   - **Password**: The value set in `MSSQL_SA_PASSWORD`

6. **Stop and Remove**

   To stop and remove the container:
   ```bash
   docker-compose down
   ```

   To also remove the volume and data:
   ```bash
   docker-compose down -v
   ```

## Notes

- Ensure the `MSSQL_SA_PASSWORD` meets SQL Server's password policy, or the container will fail to start.
- The data is stored in a Docker volume (`mssql_vol`) to persist between container restarts.
- This setup is intended for development purposes. For production, consider additional security and performance configurations.
- Ensure the port `1433` is not blocked by a firewall and that the client is using the correct credentials.
