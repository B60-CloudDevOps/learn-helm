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

How to install a helm chart ?
    1) You can install the chart that is built locally by switching to the directory that has Chart.yaml 

    or

    2) You can install a chart from the repo by supplying the values of your choice.

How to install a chart ? Here full-coral is the name we have given for the chart : 
$ helm install full-coral .
    NAME: full-coral
    LAST DEPLOYED: Tue Jul 14 01:37:09 2026
    NAMESPACE: default
    STATUS: deployed
    REVISION: 1
    DESCRIPTION: Install complete
    TEST SUITE: None

# How do we know the list of charts intalled on your cluster ?
    $ helm list 

$ helm list
    NAME            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART           APP VERSION
    full-coral      default         1               2026-07-14 01:37:09.260145079 +0000 UTC deployed        demo-0.1.0      1.16.0

# How do we know what all the chart created resources on the kubernetes cluster ?
    $ helm get manfest chartName

    $ helm get manifest full-coral
    ---
    # Source: demo/templates/configMap.yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
    name: helm-demo-cm
    data:
    player_initial_lives: "3"
    player_name: "Toto"
    ui_properties_file_name: "user-interface.properties"

# How can I dry-run a helm chart in debug mode ?
    Running in dry-run mode helps n validating the chart without installing it, while enabling debug outputs enabled verbose logs.
     $ helm install --debug --dry-run=client goodly-guppy .

# How do we upgrade an existing chart ? If the chart is not installed it installs the chart, if already installed, it upgrades the chart 
    $ helm upgrade --install <release-name> <chart-path>
    $  helm upgrade --install full-coral .

# How to switch back the deployed helm chart to the previous revision ?
    $ helm rollback <release-name> <revision> 

# What is the purpose of values.yaml file in the helm chart ?
    When parameterizing the charts, we supply the values in values.yaml in the root directory of the chart.
    By default, helm is going to pick the values from the values.yaml.

# Can't I have differnet names like prod.yaml and dev.yaml ?
    You can absolutley have them! But you need to supply them using the -f fileName.yaml

# How can we 