# Dockerfiles Monorepo

A collection of production-ready Dockerfiles with automated builds and CI/CD.

## 📁 Repository Structure

This is a monorepo containing multiple Dockerfile projects. Each project is organized in its own directory under `dockerfiles/`:

```
dockerfiles/
├── mise/           # Mise tool version manager
│   ├── Dockerfile
│   └── README.md
└── ...             # More Dockerfiles coming soon
```

## 🚀 Available Images

### Mise
Docker image based on mise polyglot tool version manager.
- **Location**: `dockerfiles/mise/`
- **Base Image**: `jdxcode/mise:2025.12.0`
- **Docker Hub**: `<your-username>/mise`

## 🔧 Usage

Each Dockerfile project has its own README with specific usage instructions. Navigate to the project directory for details.

## 🏗️ Building Locally

To build any Dockerfile locally:

```bash
cd dockerfiles/<project-name>
docker build -t <project-name>:local .
```

## 🤖 CI/CD with GitHub Actions

This repository uses GitHub Actions to automate Docker image building and deployment:

### Automated Workflows

- **Pull Requests**: 
  - Runs hadolint to check Dockerfile best practices
  - Builds Docker images to verify they compile successfully
  - Only processes changed Dockerfiles for efficiency

- **Main Branch**:
  - Runs all quality checks
  - Builds Docker images
  - Pushes images to Docker Hub with appropriate tags

### Required Secrets

To enable pushing to Docker Hub, configure these repository secrets:
- `DOCKER_USERNAME`: Your Docker Hub username
- `DOCKER_PASSWORD`: Your Docker Hub password or access token

### Image Tags

Images are tagged as follows:
- `latest`: Latest build from main branch
- `main-<sha>`: Specific commit from main branch
- `pr-<number>`: Pull request builds (not pushed)

## 📝 Contributing

### Adding a New Dockerfile

1. Create a new directory under `dockerfiles/`:
   ```bash
   mkdir dockerfiles/<new-project>
   ```

2. Add your `Dockerfile` and a `README.md` with usage instructions

3. Commit and push your changes

4. The GitHub Action will automatically:
   - Lint your Dockerfile
   - Build the image
   - Push to Docker Hub (on main branch)

### Best Practices

- Follow [Dockerfile best practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- Use multi-stage builds when appropriate
- Minimize layer count and image size
- Pin base image versions for reproducibility
- Include clear documentation in each project's README

## 🔍 Linting

Dockerfiles are automatically linted using [hadolint](https://github.com/hadolint/hadolint) in CI. 

To lint locally:
```bash
docker run --rm -i hadolint/hadolint < dockerfiles/<project>/Dockerfile
```

## 📄 License

See [LICENSE](LICENSE) file for details.
