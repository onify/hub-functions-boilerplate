# Boilterplate for Onify Hub Functions

[![Project Status: WIP – Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip)

This is a copy of the [Onify Hub Functions](https://github.com/onify/hub-functions) repo. Please feel free to use this as a base when building custom Hub Functions.

## Deploy

### Docker

Here is an example how to run in Docker.

```yaml
  custom-functions:
    image: <image url>:latest
    pull_policy: always
    restart: always
    ports:
      - 8383:8383
```

### Kubernetes

Here is an example how to run in Kubernetes.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: onify-custom-functions
spec:
  selector:
    matchLabels:
      app: custom-functions
  template:
    metadata:
      labels:
        app: custom-functions
    spec:
     imagePullSecrets:
      - name: onify-regcred
     containers:
     - name: custom-functions
       image: <image url>:latest 
       ports:
       - name: custom-functions
         containerPort: 8383
---
apiVersion: v1
kind: Service
metadata:
  name: onify-custom-functions
spec:
  ports:
    - protocol: TCP
      name: custom-functions
      port: 8383
  selector:
    app: custom-functions
```

## Run

To run it, just execute command `npm start`.

## Release

1. Update version in `package.json`
2. Update release `CHANGELOG.md`
3. Commit the changes
4. Run `git tag v*.*.*` (eg. 1.1.0)
5. Run `git push --tags`

## Support

* Community/forum: https://support.onify.co/discuss
* Documentation: https://support.onify.co/docs
* Support and SLA: https://support.onify.co/docs/get-support

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.