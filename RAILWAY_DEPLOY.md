# Railway Deployment

Deploy the Spring Boot backend from `smart-attendance-mini/backend`.

## 1. Push the project to GitHub

Railway deploys smoothly from a GitHub repository, so push this project first.

## 2. Create a Railway project

1. In Railway, create a new project from your GitHub repo.
2. Add a `MySQL` service to the same Railway project.
3. Create a backend service for this codebase.

## 3. Point Railway to the backend folder

Use one of these approaches:

- Set the service root directory to `smart-attendance-mini/backend`
- Or set `RAILWAY_DOCKERFILE_PATH=smart-attendance-mini/backend/Dockerfile`

This project already includes a Dockerfile for the backend service.

## 4. Configure backend environment variables

In the backend service, add:

```env
SPRING_DATASOURCE_URL=<Railway MySQL JDBC URL>
SPRING_DATASOURCE_USERNAME=<Railway MySQL username>
SPRING_DATASOURCE_PASSWORD=<Railway MySQL password>
```

The app now reads the server port from Railway automatically using:

```properties
server.port=${PORT:8080}
```

## 5. Deploy

Deploy the backend service. Railway will build the Dockerfile and start the Spring Boot app.

## 6. Open the app

After deployment, open the Railway-generated public domain for the backend service.

## Notes

- The deploy target is the Spring Boot backend, not the standalone `frontend` HTML files.
- Thymeleaf pages are served by the backend.
- Local development still works with the fallback values in `application.properties`.
