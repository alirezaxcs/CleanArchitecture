# Clean Architecture Solution

This repository contains a .NET solution following the principles of Clean Architecture. The solution is structured to separate concerns into different layers, making it easy to maintain, test, and scale. Below is an overview of the solution structure and how to get started.

## Solution Structure

The solution is organized into two main directories: `src` and `test`. Each directory contains projects that follow Clean Architecture principles.

### `src` Directory
Contains the main codebase, following Clean Architecture principles.

- **CleanArchitecture.Api**: Web API project that serves as the entry point for the application.
- **CleanArchitecture.Application**: The Application layer, containing use cases, application services, and business logic.
- **CleanArchitecture.Shared**: Contains shared utilities and helper classes used across different layers.
- **CleanArchitecture.Contracts**: Defines the interfaces and data contracts for communication between layers.
- **CleanArchitecture.Domain**: The Domain layer, containing domain entities, aggregates, and domain services.
- **CleanArchitecture.Infrastructure**: The Infrastructure layer, containing the implementation for data access, external service communication, etc.

### `test` Directory
Contains the test projects for unit and integration tests.

- **CleanArchitecture.Domain.Tests**: Unit tests for the Domain layer.
- **CleanArchitecture.Application.Tests**: Unit tests for the Application layer.

## Getting Started

### Prerequisites
Ensure that you have the following installed on your machine:
- [.NET SDK](https://dotnet.microsoft.com/download/dotnet)
- [Git](https://git-scm.com/)

### Clone the repository
To get started, clone the repository to your local machine:

```bash
git clone https://github.com/alijafari/CleanArchitecture.git
cd CleanArchitecture
```
### Or from scratch the project:
To get started, clone the repository to your local machine:

```bash
# Create the main solution directory
mkdir CleanArchitecture
cd CleanArchitecture

# Initialize the Git repository
git init

# Create src and test subdirectories
mkdir src
mkdir test

# Navigate to the src folder and create individual project directories
cd src

mkdir CleanArchitecture.Api
mkdir CleanArchitecture.Application
mkdir CleanArchitecture.Shared
mkdir CleanArchitecture.Contracts
mkdir CleanArchitecture.Domain
mkdir CleanArchitecture.Infrastructure

# Create class libraries for each layer, except for Api (WebAPI)
dotnet new classlib -n CleanArchitecture.Application -o CleanArchitecture.Application
dotnet new classlib -n CleanArchitecture.Shared -o CleanArchitecture.Shared
dotnet new classlib -n CleanArchitecture.Contracts -o CleanArchitecture.Contracts
dotnet new classlib -n CleanArchitecture.Domain -o CleanArchitecture.Domain
dotnet new classlib -n CleanArchitecture.Infrastructure -o CleanArchitecture.Infrastructure

# Create WebAPI for CleanArchitecture.Api
dotnet new webapi -n CleanArchitecture.Api -o CleanArchitecture.Api

# Navigate back to the main directory
cd ..

# Create test projects for Domain and Application layers
cd test

mkdir CleanArchitecture.Domain.Tests
mkdir CleanArchitecture.Application.Tests

# Create classlib for test projects
dotnet new xunit -n CleanArchitecture.Domain.Tests -o CleanArchitecture.Domain.Tests
dotnet new xunit -n CleanArchitecture.Application.Tests -o CleanArchitecture.Application.Tests

# Navigate back to the root directory to add all projects to the solution
cd ..

# Create the solution file
dotnet new sln -n CleanArchitecture

# Add projects to the solution
dotnet sln CleanArchitecture.sln add src/CleanArchitecture.Api/CleanArchitecture.Api.csproj
dotnet sln CleanArchitecture.sln add src/CleanArchitecture.Application/CleanArchitecture.Application.csproj
dotnet sln CleanArchitecture.sln add src/CleanArchitecture.Shared/CleanArchitecture.Shared.csproj
dotnet sln CleanArchitecture.sln add src/CleanArchitecture.Contracts/CleanArchitecture.Contracts.csproj
dotnet sln CleanArchitecture.sln add src/CleanArchitecture.Domain/CleanArchitecture.Domain.csproj
dotnet sln CleanArchitecture.sln add src/CleanArchitecture.Infrastructure/CleanArchitecture.Infrastructure.csproj

dotnet sln CleanArchitecture.sln add test/CleanArchitecture.Domain.Tests/CleanArchitecture.Domain.Tests.csproj

dotnet sln CleanArchitecture.sln add test/CleanArchitecture.Application.Tests/CleanArchitecture.Application.Tests.csproj

# End script
echo "Solution structure created successfully."

```

## add References 
```bash
# Add project references for CleanArchitecture.Api
dotnet add src/CleanArchitecture.Api/CleanArchitecture.Api.csproj reference src/CleanArchitecture.Contracts/CleanArchitecture.Contracts.csproj
dotnet add src/CleanArchitecture.Api/CleanArchitecture.Api.csproj reference src/CleanArchitecture.Application/CleanArchitecture.Application.csproj

# Add project references for CleanArchitecture.Domain
dotnet add src/CleanArchitecture.Domain/CleanArchitecture.Domain.csproj reference src/CleanArchitecture.Shared/CleanArchitecture.Shared.csproj

# Add project references for CleanArchitecture.Application
dotnet add src/CleanArchitecture.Application/CleanArchitecture.Application.csproj reference src/CleanArchitecture.Domain/CleanArchitecture.Domain.csproj

# Add project references for CleanArchitecture.Infrastructure
dotnet add src/CleanArchitecture.Infrastructure/CleanArchitecture.Infrastructure.csproj reference src/CleanArchitecture.Application/CleanArchitecture.Application.csproj

# Add project references for test projects
# CleanArchitecture.Domain.Tests references CleanArchitecture.Domain
dotnet add test/CleanArchitecture.Domain.Tests/CleanArchitecture.Domain.Tests.csproj reference src/CleanArchitecture.Domain/CleanArchitecture.Domain.csproj

# CleanArchitecture.Application.Tests references CleanArchitecture.Application
dotnet add test/CleanArchitecture.Application.Tests/CleanArchitecture.Application.Tests.csproj reference src/CleanArchitecture.Application/CleanArchitecture.Application.csproj
```
