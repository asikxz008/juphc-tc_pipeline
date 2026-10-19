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

Tekton definitions: [.tekton/tasks.yaml](.tekton/tasks.yaml), [.tekton/pipeline.yaml](.tekton/pipeline.yaml), [.tekton/run.yaml](.tekton/run.yaml). Run in the Skills Network OpenShift namespace using the existing lab ClusterTasks, `pipeline` ServiceAccount and `docker-reg-creds` Secret. Deploy the resulting image digest to Code Engine using its existing `icr-secret`, container port 80. Never commit credentials. Actual execution evidence is in [evidence/](evidence/). Both Code Engine applications now serve the nginx version.

## Submission format

- Task 1: paste the complete text from `evidence/01-jasmine-tests-passing`.
- Task 2: paste the Dockerfile code itself, not a GitHub link. It starts with `FROM nginx` and has five separate COPY instructions.
- Task 3: paste the entire `evidence/03-docker-build.txt`, including the command, building/extracting output, complete image tag and actual FINISHED summary.
- Task 4: paste all of `evidence/04-docker-running.txt`, including the actual docker ps table with ID, image, status, ports and name.
- Task 5: paste all of `evidence/05-tag-and-push`.
- Task 6: paste all of `evidence/06-deployed-on-cloud`, including the full application get output, not only the deployment progress.
- Task 7 URL: https://github.com/asikxz008/juphc-tc_pipeline/blob/main/.tekton/tasks.yaml
- Task 8 URL: https://github.com/asikxz008/juphc-tc_pipeline/blob/main/.tekton/pipeline.yaml
- Task 9 URL: https://github.com/asikxz008/juphc-tc_pipeline/blob/main/.tekton/run.yaml
- Task 10: upload `evidence/10-final-output.jpg`, the actual pipeline-built nginx deployment screenshot.

Earlier independent Node.js implementation and historical evidence remain in [tax-calculator-devops](https://github.com/asikxz008/tax-calculator-devops). This repository addresses the exact nginx/assets/repository-name requirements revealed by the assessment feedback. Grades remain subject to the assessor.
