# Gericht Restaurant

A modern React-based restaurant website with integrated DevOps practices.

## Technologies & Tools Integrated

### Core Technologies
- React.js
- JavaScript
- HTML/CSS

### DevOps & Continuous Integration
- **Docker**: Containerization for consistent environments
- **Jenkins**: Continuous Integration and automated builds
- **GitHub Actions**: Additional CI/CD pipeline
- **ESLint**: Code quality checks
- **Prettier**: Code formatting enforcement
- **Environment Configuration**: For flexible deployment

## Installation

```bash
# Clone the repository
git clone https://github.com/Monu2310/Gericht-React.git

# Install dependencies
npm install

# Start the development server
npm start
```

## Docker Integration

This project is containerized with Docker:

```bash
# Build the Docker image
npm run docker:build

# Run the container
npm run docker:run

# Or use docker-compose
docker-compose up -d
```

## Jenkins Integration

The project is configured with Jenkins for CI/CD. The Jenkinsfile defines a pipeline that:
- Installs dependencies
- Runs tests
- Builds the application
- Creates a Docker image (when Docker is available)

## Available Scripts

- `npm start` - Starts the development server
- `npm test` - Runs the test suite
- `npm run build` - Creates a production build
- `npm run lint` - Runs ESLint to check code quality
- `npm run lint:fix` - Fixes ESLint issues automatically
- `npm run format` - Formats code using Prettier
- `npm run docker:build` - Builds the Docker image
- `npm run docker:run` - Runs the Docker container
- `npm run deploy:local` - Builds, creates Docker image and runs container

## Project Structure

- `src/` - Source code
  - `components/` - Reusable UI components
  - `container/` - Page sections and layouts
  - `assets/` - Images, videos, and static assets
  - `constants/` - Configuration data

## Environment Variables

The project uses environment variables for configuration:
- `REACT_APP_API_URL` - Backend API URL
- `REACT_APP_APP_NAME` - Application name
- `REACT_APP_VERSION` - Application version


