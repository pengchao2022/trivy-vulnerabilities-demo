# trivy-vulnerabilities-demo

In this demo, I will show you how to use trivy to scan images


## Usage

- Download Trivy, you can get trivy from the Trivy github page

```sh
https://github.com/aquasecurity/trivy/releases
```
- move trivy installation file to remote Alibaba ECS server

  - set up the ssh key file permission
  ```shell
  chmod 400 ../alibaba/alibaba-north.pem 
  ```
  - Scp command to transfer to remote server
  ```shell
  scp -i ../alibaba/alibaba-north.pem trivy_0.68.1_Linux-64bit.tar.gz ecs-user@8.145.39.235:/tmp/
  ```
  - Unzip trivy installation package
  ```shell
  tar -xzf trivy_0.68.1_Linux-64bit.tar.gz
  ```
  - Move to system path
  ```shell
  sudo mv trivy /usr/local/bin/
  ```
  - grant the execute permission for trivy
  ```shell
  sudo chmod +x /usr/local/bin/trivy
  ```
  - Check the trivy version
  ```shell
  trivy --version
  ```
  - Set environment and use github container register
  ```shell
  export TRIVY_DB_REPOSITORY="ghcr.io/aquasecurity/trivy-db"
  ```
- Use trivy to scan the dockerhub image
```shell
trivy image pengchaoma/springboot-todo-app:1.0.0
2026-01-07T17:55:56+08:00       INFO    Adding schema version to the DB repository for backward compatibility   repository="ghcr.io/aquasecurity/trivy-db:2"
2026-01-07T17:55:56+08:00       INFO    [vulndb] Need to update DB
2026-01-07T17:55:56+08:00       INFO    [vulndb] Downloading vulnerability DB...
2026-01-07T17:55:56+08:00       INFO    [vulndb] Downloading artifact...        repo="ghcr.io/aquasecurity/trivy-db:2"
79.79 MiB / 79.79 MiB [---------------------------------------------------------------------------------------------------------------------------------------------] 100.00% 6.41 MiB p/s 13s
2026-01-07T17:56:11+08:00       INFO    [vulndb] Artifact successfully downloaded       repo="ghcr.io/aquasecurity/trivy-db:2"
2026-01-07T17:56:11+08:00       INFO    [vuln] Vulnerability scanning is enabled
2026-01-07T17:56:11+08:00       INFO    [secret] Secret scanning is enabled
2026-01-07T17:56:11+08:00       INFO    [secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2026-01-07T17:56:11+08:00       INFO    [secret] Please see https://trivy.dev/docs/v0.68/guide/scanner/secret#recommendation for faster secret detection
```
- Here you can see the trivy db
```shell
ecs-user@iZ0jle4z93fet5386z4gwzZ:~/.cache/trivy/db$ pwd
/home/ecs-user/.cache/trivy/db
```






