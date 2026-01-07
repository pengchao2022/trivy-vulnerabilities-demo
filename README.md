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

  


