# Встановлення та налаштуйтування kubectl-ai плагіна для створення ШІ Recommended YAML manifests

## Steps to reproduce
1. Creating an [API key](https://platform.openai.com/account/api-keys)  
`key name: name: kubectl-ai`  

2. Installing and configure [the kubectl-ai plugin](https://github.com/sozercan/kubectl-ai)
```sh
$ wget https://github.com/sozercan/kubectl-ai/releases/download/v0.0.11/kubectl-ai_linux_amd64.tar.gz
$ tar -zxvf kubectl-ai_linux_amd64.tar.gz
$ mv kubectl-ai /usr/local/bin/
$ chmod +x /usr/local/bin/kubectl-ai

$ kubectl plugin list                                                                                
The following compatible plugins are available:
/usr/local/bin/kubectl-ai

$ nano ~/.zshrc
export OPENAI_API_KEY="***************************"

$ source ~/.zshrc

$ export OPENAI_DEPLOYMENT_NAME="gpt-4"
```

3.  Writing Promts
```yaml
$ kubectl ai "" --require-confirmation=false > yaml/app.yaml
$ kubectl ai "" --require-confirmation=false > yaml/app-livenessProbe.yaml
$ kubectl ai "Add Readiness Probe" --require-confirmation=false > yaml/app-readinessProbe.yaml
$ kubectl ai "Configure Volume Mounts" --require-confirmation=false > yaml/app-volumeMounts.yaml
$ kubectl ai "Create Cron Job" --require-confirmation=false > yaml/app-cronjob.yaml
$ kubectl ai "Create a Job" --require-confirmation=false > yaml/app-job.yaml
$ kubectl ai "Set Up Multi-container Pods" --require-confirmation=false > yaml/app-multicontainer.yaml
$ kubectl ai "Configure Resource Usage" --require-confirmation=false > yaml/app-resources.yaml
$ kubectl ai "Set Up Secrets as Env Variables" --require-confirmation=false > yaml/app-secret-env.yaml
```

4. The resulting manifest in the yaml directory in the root of the repository.

| NAME                        | PROMPT                             | DESCRIPTION                                                              | EXAMPLE                                     |
|-----------------------------|------------------------------------|--------------------------------------------------------------------------|---------------------------------------------|
| app.yaml                    | Create Application Config          | YAML to define the basic schema of a Kubernetes application              | [app.yaml](yaml/app.yaml)                 |
| app-livenessProbe.yaml      | Add Liveness Probe                 | YAML to define a liveness probe for your application                    | [app-livenessProbe.yaml](yaml/app-livenessProbe.yaml) |
| app-readinessProbe.yaml     | Add Readiness Probe                | YAML to define a readiness probe for your application                   | [app-readinessProbe.yaml](yaml/app-readinessProbe.yaml) |
| app-volumeMounts.yaml       | Configure Volume Mounts            | YAML to define and configure storage volumes for your application       | [app-volumeMounts.yaml](yaml/app-volumeMounts.yaml) |
| app-cronjob.yaml            | Create Cron Job                    | YAML to define a cron job within your application                       | [app-cronjob.yaml](yaml/app-cronjob.yaml) |
| app-job.yaml                | Create a Job                       | YAML to define a job within your application                            | [app-job.yaml](yaml/app-job.yaml) |
| app-multicontainer.yaml     | Set Up Multi-container Pods        | YAML to define a pod that runs more than one container                  | [app-multicontainer.yaml](yaml/app-multicontainer.yaml) |
| app-resources.yaml          | Configure Resource Usage           | YAML to configure resource requests and limits for your application     | [app-resources.yaml](yaml/app-resources.yaml) |
| app-secret-env.yaml         | Set Up Secrets as Env Variables    | YAML to define environment variables using secrets                      | [app-secret-env.yaml](yaml/app-secret-env.yaml) |

