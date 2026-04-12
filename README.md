# Basic Elixir Phoenix Web App

A basic Elixir web application bootstrapped with Phoenix, featuring a Docker-based development environment and VS Code support.

## Getting Started

### Prerequisites

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [VS Code](https://code.visualstudio.com/) (recommended) with [ElixirLS](https://marketplace.visualstudio.com/items?itemName=elixir-lsp.elixir-ls) extension.

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

### Interactive Debugging
*Note: Interactive debugging via VS Code for Dockerized Elixir can be complex without VS Code Dev Containers. The provided `launch.json` is a starting point.*

- Use the **Ecto Setup (Docker)** task to prepare your database.
- Use **Run Tests (Docker)** to verify your logic.
- For true interactive debugging, consider using [VS Code Dev Containers](https://code.visualstudio.com/docs/remote/containers).

## Community Conventions

- **Hex:** Elixir's package manager.
- **Mix:** The build tool used for tasks like compiling, testing, and managing dependencies.
- **ExUnit:** The built-in test framework.
- **Phoenix:** The standard web framework for Elixir.

## Learn More

- Elixir: [https://elixir-lang.org/](https://elixir-lang.org/)
- Phoenix: [https://www.phoenixframework.org/](https://www.phoenixframework.org/)
- HexDocs: [https://hexdocs.pm/](https://hexdocs.pm/)
