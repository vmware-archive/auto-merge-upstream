# Auto-merge Upstream
This project is a self-hostable application that provides an easy way to automate the merging of an upstream Git repository into a downstream Git repository.  In the case where a merge fails, an email is sent, notifying the recipients that this failure has occurred.

In order to facilitate self-hosting, the application is designed to work in [Cloud Foundry][].


## Configuration
Since the application is designed to work in a PaaS environment, all configuration is done with environment variables.

| Key | Description
| --- | -----------
| `UPSTREAM_URI` | The Git URI of the upstream repository.  **NOTE:** This URI can include credential information for private repositories.
| `DOWNSTREAM_URI` | The Git URI of the downstream repository.  **NOTE:** This URI can include credential information for private repositories.
| `FROM_ADDRESS` | The email address to send failure notifications from
| `TO_ADDRESS` | The email address to send failure notifications to


## Deployment
_The following instructions assume that you have [created an account][cloud-foundry-account] and [installed the `cf` command line tool][]._

In order to automate the deployment process as much as possible, the project contains a Cloud Foundry [manifest][].  To deploy run the following commands:

```bash
cf push --no-start
cf set-env auto-merge-upstream UPSTREAM_URI <value>
cf set-env auto-merge-upstream DOWNSTREAM_URI <value>
cf set-env auto-merge-upstream FROM_ADDRESS <value>
cf set-env auto-merge-upstream TO_ADDRESS <value>
cf start
```


## License
The project is released under version 2.0 of the [Apache License][].

[Apache License]: http://www.apache.org/licenses/LICENSE-2.0
[Cloud Foundry]: https://run.pivotal.io
[cloud-foundry-account]: https://docs.cloudfoundry.com/docs/dotcom/getting-started.html#signup
[installed the `cf` command line tool]: https://docs.cloudfoundry.com/docs/dotcom/getting-started.html#install-cf
[manifest]: manifest.yml
