# Helm Generic App: An advanced example chart

This Helm chart provides examples of some of Helm's more powerful
features.

**This is not a production-grade chart. It is an example.**

The chart installs a docker image of your choice according to the following
pattern:

- A `Deployment` is used to create a Replica Set of nginx pods.
  ([templates/deployment.yaml](templates/deployment.yaml))
- A `Service` is used to create a gateway to the pods running in the
  replica set ([templates/service.yaml](templates/service.yaml))

The [values.yaml](values.yaml) exposes a few of the configuration options in the
charts, though there are some that are not exposed there (like
`.image`).

The [templates/_helpers.tpl](templates/_helpers.tpl) file contains helper templates. The leading
underscore (`_`) on the filename is semantic. It tells the template renderer
that this file does not contain a manifest. That file declares some
templates that are used elsewhere in the chart.

Helpers (usually called "partials" in template languages) are an
advanced way for developers to structure their templates for optimal
reuse.

You can deploy this chart with `helm install --set image.repository=nginx image.tag=latest`. Or
you can see how this chart would render with `helm install --dry-run --set image.repository=nginx image.tag=latest
--`.