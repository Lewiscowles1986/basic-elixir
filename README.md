# Basic Elixir Phoenix Web App

A basic Elixir web application bootstrapped with Phoenix, featuring a Docker-based development environment and VS Code support.

## Getting Started

### Prerequisites

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [VS Code](https://code.visualstudio.com/) (recommended) with [ElixirLS](https://marketplace.visualstudio.com/items?itemName=JakeBecker.elixir-ls) extension.

### Setup

1. **Build the environment:**
   ```bash
   docker-compose build
   ```

2. **Initialize the database:**
   ```bash
   docker-compose run --rm web mix ecto.setup
   ```

3. **Run the application:**
   ```bash
   docker-compose up
   ```

The app will be available at [http://localhost:4000](http://localhost:4000).

## TDD (Test Driven Development)

To run the test suite:

```bash
docker-compose run --rm web mix test
```

For continuous testing, you can use `mix test.watch` (if configured) or simply run the above command as you develop.

## Debugging

This project includes VS Code configuration in `.vscode/`.

### Recommended Extensions
When you open this project in VS Code, you should be prompted to install:
- **ElixirLS**: For language support and debugging.
- **Dev Containers**: To run VS Code *inside* your Docker container.

### Interactive Debugging
Since Elixir is not installed on your host machine, the most reliable way to debug is via **Dev Containers**:
1. Install the **Dev Containers** extension.
2. Click the green icon in the bottom-left corner of VS Code.
3. Select **"Reopen in Container"**.
4. Once inside, you can use the **Run and Debug** sidebar with the provided configurations.

Alternatively, use the **Tasks** (`Cmd+Shift+P` -> `Tasks: Run Task`):
- **Ecto Setup (Docker)**: Prepare your database.
- **Run Tests (Docker)**: Execute the test suite.

## Community Conventions

- **Hex:** Elixir's package manager.
- **Mix:** The build tool used for tasks like compiling, testing, and managing dependencies.
- **ExUnit:** The built-in test framework.
- **Phoenix:** The standard web framework for Elixir.

## Learn More

- Elixir: [https://elixir-lang.org/](https://elixir-lang.org/)
- Phoenix: [https://www.phoenixframework.org/](https://www.phoenixframework.org/)
- HexDocs: [https://hexdocs.pm/](https://hexdocs.pm/)
