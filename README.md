# Week 9 CI/CD Pipeline

## Deployment Flow

GitHub → Jenkins → Build → Test → Docker → Deploy → Verify → Rollback

## Technologies Used

- GitHub
- Jenkins
- Docker
- AWS EC2
- Ubuntu
- Nginx

## Deployment

The application was built and packaged as a Docker image through the Jenkins CI/CD pipeline.

## Version 2

A controlled deployment issue was introduced in Version 2 to demonstrate rollback.

## Rollback

After verifying the deployment issue, the application was rolled back to the previous working Version 1.

## Verification

The application was successfully verified after rollback using the deployed application URL.

## Result

The CI/CD pipeline successfully demonstrated automated build, testing, Docker deployment, verification, and controlled rollback.
