# Builders

From the Builders dashboard you can view and manage your existing CI pipelines (builders) across all [organizations](organizations.md), and [create new builders](#creating-builders).

Builders are used to clone your custom [Runtime Code](../nakama/server-framework/basics.md) written in Lua, TypeScript, and Go. It then conditionally compiles your code against the Nakama image selected and packages it into a Docker image. 
This image is then available for deployment in a project in the [Configuration](projects.md#configuration) tab, enabling you to quickly deploy a new image or return to a previous one whenever needed.

!!! note "Note"
    Builders are designed to ignore your Lua test files as follows:
    * All `.lua` files in a `/tests` directory
    * Any files named in the format `*.test.lua` or `*_test.lua`  

![Builders dashboard](images/builders-dashboard.png)

Each tile on the dashboard provides the details of the corresponding builder:

* **Status**: Icon indicates the status of the most recent build process.
* **Builder name**: The name of this builder, used to build the resultant image. This cannot be edited once set.
* **Organization**: The organization this builder belongs to.
* **Description**: The user provided builder description.
* **Repository**: The Git repository this builder is linked to.
* **Branch Nakama Version**: The Nakama version associated with this builder. Any custom code must use the same Nakama version.

## Creating builders

You can create a new builder from your Organization or Builders dashboards.

1. From the dashboard page, select the **New Builder** tile. The **Create your Builder** page is displayed.
    ![Create Builder](images/create-builder.png)
2. Provide the following details for your new builder:
    * **Organization**: The Organization this builder will be associated with. Use the drop-down to select from your available Organizations.
    * **Builder Name**: Enter a unique identifier for your builder. This name will be used for the Docker images created by this builder. Only alphanumeric characters may be used and cannot exceed 20 characters in length.
    * **Description**: Enter a short description of this builder for easy identification.
    * **Nakama Image**: Use the drop-down to select the Nakama version this builder will use.
3. Click **Create** to finalize your new builder, then proceed to the [builder details page](#managing-builders) to connect it to your desired repository and complete setup.

### Connecting to source control

To link your new builder to a desired repository, navigate to the Edit tab in your builder settings:

![Select Builder repository](images/builder-repository.png)

Use the drop-down of your source control provider (Git) to enter your connection details, then click **Connect**.

## Managing builders

Select any builder tile from your Organization or Builders dashboards to view its details page and manage the configuration.

There are eight tabs available in the project details page:

### Info
![Builder into tab](images/builder-info.png)

The Info tab provides all relevant details for this builder, such as the associated repository and Nakama image, and the recent status for this builder.

### Trigger

![Builder trigger tab](images/builder-trigger.png)

The Trigger tab enables you to view all recent commits for the linked repository and selected branch, then trigger a new image build using your desired commit SHA.

After selecting **Trigger** you can view the progress on the **Info** tab and, when finished, use this new image to update any projects in your organization.

### History

![Builder history tab](images/builder-history.png)

The History tab displays all previously triggered builds. Select any listed build to view additional details.

### Logs

![Builder logs tab](images/builder-logs.png)

The Logs tab enables you to view all logs generated by this builder, and filter according to logging level and any desired time period.

### Edit

![Builder edit tab](images/builder-edit.png)

The Edit tab enables you to change available builder settings, such as the linked repository, description, and Nakama image used.

### Team

![Builder team tab](images/builder-team.png)

The Team tab enables you to view existing team members, manage their permission level for this builder, and add or remove team members from the builder entirely.

Users must have previously [registered with Heroic Cloud](https://cloud2.heroiclabs.com/register) before they can be added here.

### Audit

![Builder audit tab](images/builder-audit.png)

The Audit tab enables you to view a list of all user actions performed on this builder. You can filter this list according to the Category and Action performed.

### Transfer/Delete

![Builder transfer tab](images/builder-transfer.png)

The Transfer/Delete tab enables you to transfer this builder to another organization, moving all of its resources and produced images, or to delete the builder entirely.