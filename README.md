# broker-iac-accepts

This contains the accepts.json for each SCM for Snyk's broker.
Taking the original `accepts.json` file, we are adding rules to incorporate the rules for both Terraform and Kubernetes Config mentioned below

[Terraform](https://support.snyk.io/hc/en-us/articles/360011018778-Detecting-Terraform-configuration-files-using-a-broker) \
[Kubernetes Config](https://support.snyk.io/hc/en-us/articles/360010797537-Detecting-Kubernetes-configuration-files-using-a-broker)

## Related 
[Snyk Broker](https://github.com/snyk/broker)

## Usage
The broker takes the path to the accept.json file (with the rules above added) in the ACCEPT environment variable. You can see an example of passing that to the GitHub broker below.
```docker run --restart=always \
  -p 8000:8000 \
  -e BROKER_TOKEN=secret-broker-token \
  -e GITHUB_TOKEN=secret-github-token \
  -e PORT=8000 \
  -e BROKER_CLIENT_URL=https://my.broker.client:8000 \
  -e ACCEPT=/private/accept.json
  -v /local/path/to/private:/private \
  snyk/broker:github-com
  ```
