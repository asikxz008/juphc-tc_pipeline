# Tax Calculator — course submission

Public repository uses the exact course-required name `juphc-tc_pipeline`. This is an independent educational implementation with fictional tax brackets.

The static browser app is served by nginx. The Dockerfile begins with `FROM nginx` and copies each of the five required assets separately.

```bash
npm ci
npx jasmine
docker build -t tax-calculator:latest .
docker run -d --name tax-calculator-course -p 8080:80 tax-calculator:latest
docker ps
```

Tekton definitions: [.tekton/tasks.yaml](.tekton/tasks.yaml), [.tekton/pipeline.yaml](.tekton/pipeline.yaml), [.tekton/run.yaml](.tekton/run.yaml). Run in the Skills Network OpenShift namespace using the existing lab ClusterTasks, `pipeline` ServiceAccount and `docker-reg-creds` Secret. Deploy the resulting image digest to Code Engine using its existing `icr-secret`, container port 80. Never commit credentials. Actual execution evidence is added after verification.
