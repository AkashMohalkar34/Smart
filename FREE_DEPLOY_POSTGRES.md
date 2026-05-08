# Free Deployment with PostgreSQL

This project is now ready to run on a free PostgreSQL-based setup such as:

- `Supabase` for the database
- `Render` for the Spring Boot backend

## Recommended free stack

- Database: `Supabase Postgres`
- App hosting: `Render Web Service`

## 1. Create a free Supabase project

1. Go to Supabase and create a new project.
2. Open the project settings and find the database connection details.
3. Copy these values:
   - host
   - port
   - database name
   - username
   - password

## 2. Create a Render web service

1. Push this repo to GitHub.
2. In Render, create a new `Web Service` from the GitHub repo.
3. Set the root directory to:

```text
smart-attendance-mini/backend
```

4. Render can build using the existing `Dockerfile`.

## 3. Add backend environment variables in Render

Add these variables to the backend service:

```env
SPRING_DATASOURCE_URL=jdbc:postgresql://HOST:PORT/DATABASE
SPRING_DATASOURCE_USERNAME=USERNAME
SPRING_DATASOURCE_PASSWORD=PASSWORD
SPRING_DATASOURCE_DRIVER_CLASS_NAME=org.postgresql.Driver
SPRING_JPA_DATABASE_PLATFORM=org.hibernate.dialect.PostgreSQLDialect
```

Replace:

- `HOST` with the Supabase host
- `PORT` with the Supabase port
- `DATABASE` with the database name
- `USERNAME` with the database username
- `PASSWORD` with the database password

Example:

```env
SPRING_DATASOURCE_URL=jdbc:postgresql://db.example.supabase.co:5432/postgres
SPRING_DATASOURCE_USERNAME=postgres
SPRING_DATASOURCE_PASSWORD=your_password
SPRING_DATASOURCE_DRIVER_CLASS_NAME=org.postgresql.Driver
SPRING_JPA_DATABASE_PLATFORM=org.hibernate.dialect.PostgreSQLDialect
```

## 4. Deploy

Deploy the Render service after adding the variables.

## 5. Open the app

Use the Render-generated public URL to open the deployed app.

## Notes

- The backend will auto-create tables because `spring.jpa.hibernate.ddl-auto=update` is enabled.
- Demo seed data should still load through the existing application startup flow.
- Local development can still use custom environment variables if you want to connect to another database.
