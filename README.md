# Cloud Enabled Deployment In Action with AWS & GCP

---

This assignment outlines the steps to connect course-service Spring Boot application to a MySQL database hosted on Google Cloud Platform (GCP).

This repository contains four projects:

- course-service (Spring Boot + MySQL)
- student-service (Spring Boot + MongoDB)
- media-service (Spring Boot + Local file storage, can be extended to S3/MinIO)
- frontend-app (React + TypeScript)

---

## Backend Services

### 1. course-service
- Entity: Course(id, name, duration)
- Endpoints:
  - GET /courses
  - GET /courses/{id}
  - POST /courses
  - DELETE /courses/{id}
- Default port: 8081
- Configure MySQL settings

---

#### GCP MySQL Configuration

**01.Clone the Project Repository.**
```sh
git clone https://github.com/yehaniharshika/cloud-enabled-deployment-with-gcp-practical-assignment.git
```

**02. Create a MySQL instance in Google Cloud SQL.**

**03. Configure application-gcp.properties file**
```sh
spring.application.name=course-service

# MySQL Configurations
spring.datasource.host=your IP Address
spring.datasource.port=3306
spring.datasource.url=jdbc:mysql://${spring.datasource.host}:${spring.datasource.port}/eca_courses?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=your Password
```
**04. Activate the GCP Profile**
```sh
spring.profiles.active=gcp
```

**05. Run the Frontend module and Backend course-service module**

**06. Add sample course data to DB**

#### 📺 Demo Video
This video demonstrates the Practical Assignment in action, showing how the project is deployed and connected with GCP MySQL

[Watch the Demo Video](https://drive.google.com/drive/folders/19hdMuU_gznUOYT4QjVscdT5nv807NOGG?usp=drive_link) here

### 2. student-service
- Document: Student(registrationNumber, fullName, address, contact, email)
- Endpoints:
  - GET /students
  - GET /students/{id}
  - POST /students
  - DELETE /students/{id}
- Default port: 8082
- Configure MongoDB settings

### 3. media-service
- Resource: files
- Endpoints:
  - POST /files (multipart/form-data: file)
  - GET /files (list)
  - GET /files/{id} (fetch)
  - DELETE /files/{id} (delete)
- Default port: 8083
- Uses local disk storage at `./data/media` by default (override with env var `MEDIA_STORAGE_DIR`).

---

## Frontend (frontend-app)
- React + TypeScript + MUI + Axios + Vite app with 3 sections: Courses, Students, Media
- Scripts:
  - npm run dev (Vite dev server)
  - npm run build (TypeScript build + Vite build)
  - npm run preview (Preview built app)

---

## Build

- Backend: run `mvn -q -e -DskipTests package` at repo root to build services.
- Frontend: run `npm install` then `npm run dev` inside `frontend-app`.

---

## License
© 2025 All Right Reserved Created By Yehani Harshika
<br/>
This project is licensed under the [MIT](License.txt) license
