# learn-helm

    The package manager for Kubernetes

    Helm is the best way to find, share, and use software built for Kubernetes.

> Helm helps you manage Kubernetes applications — Helm Charts help you define, install, and upgrade even the most complex Kubernetes application.
> Charts are easy to create, version, share, and publish — so start using Helm and stop the copy-and-paste.
> Helm is a graduated project in the CNCF and is maintained by the Helm community.

How to install helm on workstation ?
    $ curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-4 | bash

How a typical helm chart looks like ?

```
    wordpress/
        Chart.yaml          # A YAML file containing information about the chart
        values.yaml         # The default configuration values for this chart
        values.schema.json  # OPTIONAL: A JSON Schema for imposing a structure on the values.yaml file
        charts/             # A directory containing any charts upon which this chart depends.
        templates/          # A directory of templates that, when combined with values,
                            # will generate valid Kubernetes manifest files.
``` 