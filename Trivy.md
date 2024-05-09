# Trivy Vulnerability Scanner

Trivy is a comprehensive vulnerability scanner for containers, designed to detect vulnerabilities in operating system packages, dependencies, and application frameworks commonly used in containerized environments. It provides detailed reports on security vulnerabilities, helping you ensure the security of your containerized applications.

## Installation

To install Trivy, follow the steps outlined below:
``` shell 
sudo apt update

sudo apt-get install wget apt-transport-https gnupg lsb-release

wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null

echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/trivy.list

sudo apt-get update

sudo apt-get install trivy -y

trivy --version
```

## Trivy Commands
1. Scanning GitHub Repo
   ``` shell
   trivy repo <"repo-url">
   
   trivy repo https://github.com/Pawan-choudhary/Three-Tier-Application-Deployment.git
   ```

2. Export/Save Trivy Report in HTML Format
``` shell
	trivy repo --format table -o report.html https://github.com/Pawan-choudhary/Three-Tier-Application-Deployment.git
```

3. Export/Save Trivy Report in JSON Format
``` shell
	trivy repo --format json -o report.json https://github.com/Pawan-choudhary/Three-Tier-Application-Deployment.git
```
4. Scan the File System
``` shell
	cd <"dir-name">
	
  trivy fs .
```
5. Filter by Severity and Export/Save Trivy Report in HTML Format
``` shell
	trivy fs --format table -o fs-report.html --severity HIGH,CRITICAL
```
6. Scan for Misconfigurations and Vulnerabilities
``` shell
	trivy fs --scanners vuln,misconfig --severity HIGH,CRITICAL <"folder-name-or-path">
```
7. Scanning Docker Images
``` shell
	trivy image <image_name>

	trivy image sonarqube
```
8. Export/Save Trivy Report in JSON Format for Docker Images
``` shell
	trivy image --format json -o report.json <"image_name">
```
9. Scan Kubernetes Cluster
``` shell
	trivy k8s --report summary cluster
```
10. Extract Information About Container Images from Pods in a Kubernetes Cluster
``` shell
	kubectl get pods -o=jsonpath='{range .items[*]}{.spec.containers[*].image}{"\n"}{end}'
trivy image <container-image-name>
```




