# docker-qemu-buildx-ecr-action

Docker QEMU Buildx ECR Action - supports multi platform builds including linux/arm64 and ECR Push

## Usage

```yaml
name: ci

on:
  push:

jobs:
  qemu:
    runs-on: ubuntu-latest
    steps:
      - name: Docker QEMU Buildx ECR
        uses: bbharathkumarreddy/docker-qemu-buildx-ecr-action
        with:
          platform: linux/arm64
          ecr-push: true
          aws-access-key-id: ${{ secrets.aws-access-key-id }}
          aws-secret-access-key: ${{ secrets.aws-secret-access-key }}
          aws-region: ${{ vars.aws-region }}
          ecr-repository: my-service
          ecr-tag: latest
```

## Customizing

### inputs

The following inputs can be used as `step.with` keys:

| Name                    | Type    | Default                                                                 | Description                                                                                                        |
| ----------------------- | ------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| `platform`              | String  | [`linux/arm64`](https://docs.docker.com/build/building/multi-platform/) | Platform architecture to build.                                                                                   |
| `ecr-push`              | Boolean | `true`                                                                  | Set to `true` to push the docker build to ECR repository. `aws.*` and `ecr.*` inputs to be given if set to `true`. |
| `aws-access-key-id`     | String  |                                                                         | Pass the AWS access key id.                                                                                        |
| `aws-secret-access-key` | String  |                                                                         | Pass the AWS secret access key.                                                                                    |
| `aws-region`            | String  |                                                                         | Pass the AWS region of the ECR repository.                                                                         |
| `ecr-repository`        | String  |                                                                         | Pass the ECR repository name.                                                                                      |
| `ecr-tag`               | String  | `latest`                                                                | Pass ECR tag to push.                                                                                              |

## Contributing

Want to contribute? ✅
