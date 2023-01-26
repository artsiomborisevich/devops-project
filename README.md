# **Project report**
### **Project's reporter:** Artyom Borisevich   
### **Group number:** md-sa2-22-22
---
## **Description of application for deployment**
- **Application:** Drupal
- **Programimg language:** PHP
- **DB:** MariaDB
---
## Pipeline. High Level Design

![](scheme.jpg)

---
## Technologies which were used in project
- **Orchestration:** Kubernetes
- **Automation tools:** Github actions, ArgoCD, Ansible
- **SCM:** GitHub
- **Notification:** Slack
- **Other tools:** Docker, Helm
---

## CI/CD description:
GitHub actions workflow starting after pushing to the main branch.

### CI has following steps:
| Action                       | Description                                                                                                                                            |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Push tag**                 | Developer pushes tag with the new version of app which triggers github actions.                                                                        |
| **Testing**                  | Verification of `Helm manifests` and `Dockerfile`.                                                                                                     |
| **Build and push**           | Build docker image app with the tag from developer and push it to the Github Packages.                                                                 |
| **Helm Package**             | This action generates a helm package and updates files `values.yaml` and `index.yaml` . Also *appVersion* and *version* are updated in the `Chart.yaml`. |
| **Push helm package to git** | Push changes to the **gh-pages** branch (**main**).                                                                                                    |
| **Slack Notification**       | Send notification to the Slack.                                                                                                                |

### CD following steps:

- GitHub pages is used as helm artifactory
- ArgoCD WebUI or console is used for deployment
---

## Links:
Project repository: https://github.com/artsiomborisevich/devops-project
