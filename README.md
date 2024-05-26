Got it! Here's the updated `README.md` with the Laravel installation step in the same directory where the command is run:

```markdown
# Devcontainer to run a Laravel 11 Project with PostgreSQL 16

This repository contains a devcontainer configuration to run in a development container using Visual Studio Code's Remote - Containers extension. The development environment includes a PostgreSQL 16 database.

## Prerequisites

Before you can use this devcontainer setup, make sure you have the following installed:

- [Docker](https://www.docker.com/get-started)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Remote - Containers extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Getting Started

Follow these steps to set up the development environment:

1. **Clone the repository**:

    ```sh
    git clone https://github.com/alancherosr/devcontainer-laravel-postgres.git
    cd devcontainer-laravel-postgres
    ```

2. **Open the repository in Visual Studio Code**:

    ```sh
    code .
    ```

3. **Reopen in Container**:

    - Press `F1` to open the Command Palette.
    - Type `Remote-Containers: Reopen in Container` and select it.

4. **Wait for the container to build**:
    - The first time you open the repository in a container, it might take a few minutes to build the image and set up the environment.

5. **Install Laravel**:

    Inside the container terminal, run:

    ```sh
    composer create-project --prefer-dist laravel/laravel .
    ```

6. **Set up the environment file**:

    Copy the `.env.example` to `.env` and update the necessary environment variables, especially the database configuration:

    ```sh
    cp .env.example .env
    php artisan key:generate
    ```

    Make sure your `.env` file has the following database configuration:

    ```env
    DB_CONNECTION=pgsql
    DB_HOST=postgres
    DB_PORT=5432
    DB_DATABASE=laravel
    DB_USERNAME=user
    DB_PASSWORD=secret
    ```

7. **Run database migrations**:

    ```sh
    php artisan migrate
    ```

## Devcontainer Configuration

The `.devcontainer` directory contains the necessary configuration files to set up the development container:

- `.devcontainer/Dockerfile`: Defines the custom image based on `php:8.3-fpm` with additional setup.
- `.devcontainer/devcontainer.json`: Specifies the settings for the development container, including the service definition for PostgreSQL.

## Services

The development environment includes the following services:

- **PHP**: Running PHP 8.3 with FPM.
- **PostgreSQL**: Running PostgreSQL 16.

## Connecting to PostgreSQL

The PostgreSQL database is accessible at the hostname `postgres` from within the container. Use the credentials defined in your `.env` file to connect to the database.

## Useful Commands

- **Install Composer dependencies**:

    ```sh
    composer install
    ```

- **Run database migrations**:

    ```sh
    php artisan migrate
    ```

- **Start the development server**:

    ```sh
    php artisan serve --host=0.0.0.0 --port=8000
    ```

## Contributing

Feel free to open issues or submit pull requests if you find any bugs or have suggestions for improvements.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
```

This version ensures that the Laravel project is installed in the same directory where the command is run, which is the root directory of the repository.
