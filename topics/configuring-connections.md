[//]: # (title: Configuring Connections)
[//]: # (auxiliary-id: Configuring Connections)

TeamCity allows storing presets of connections to external services. You can reuse these presets in various places on the server: when creating projects, configuring notifications, or integrating with issue trackers. This article gives instructions on how to add each type of connection.

To add a connection, go the project's settings and open the __Connections__ page. Set its _Display name_ to distinguish it from the others and configure it as described in the sections below.

When created, a connection can be used in all the nested subprojects of the current project. If you add a connection in the Root project, it will become available on the whole server.

## Amazon ECR

A connection to Amazon Elastic Container Registry (ECR) allows accessing Docker images located in private AWS registries.

The connection requires the following settings:
* 

## Azure DevOps

A connection to Azure DevOps Services (or formerly Team Foundation Server) can be used to:
* create a [project from URL](creating-and-editing-projects.md#Creating+project+pointing+to+repository+URL);
* create a [VCS root from URL](guess-settings-from-repository-url.md);
* create a [TFS](team-foundation-server.md) VCS root;
* integrate with a [Team Foundation Work Items](team-foundation-work-items.md) issue tracker;
* automatically apply an access token when configuring Commit Status Publisher for Git repositories.

Before configuring the connection, sign in to your Azure DevOps account and create a personal access token with _All scopes_ as described [here](https://www.visualstudio.com/en-us/docs/setup-admin/team-services/use-personal-access-tokens-to-authenticate). Then, (1) go back to the connection form in TeamCity, (2) enter your Azure server URL (`https://{account}.visualstudio.com` for Azure DevOps or `https://{server}:8080/tfs/` for VSTS), (3) paste your Azure token, and (4) save the connection.

After the connection is configured, an Azure DevOps Services icon becomes active in several places where a repository URL can be specified. Click it to authorize TeamCity in your Azure profile. TeamCity will be granted full access to all the Azure resources available to you.  
You can configure multiple VSTS connections. In this case, the server URL will be displayed next to each VSTS icon, so it is easier to distinguish the server in use.

## Bitbucket Cloud

>In TeamCity Cloud, a connection to Bitbucket Cloud is already predefined in the Root project's settings, which makes it available in all the other projects.
>
{product="tcc"}

A connection to Bitbucket Cloud can be used to:
* create a [project from Bitbucket URL](creating-and-editing-projects.md#Creating+project+pointing+to+repository+URL);
* create a [VCS root from URL](guess-settings-from-repository-url.md);
* create a [Mercurial](mercurial.md) VCS root;
* integrate with a [Bitbucket](bitbucket-cloud.md) issue tracker;
* enable [BitBucket Cloud authentication](configuring-authentication-settings.md#Bitbucket+Cloud).

The connection form provides multiple parameters. Use them to [create an OAuth consumer in Bitbucket](https://confluence.atlassian.com/bitbucket/oauth-on-bitbucket-cloud-238027431.html#OAuthonBitbucketCloud-Createaconsumer). Then, (1) copy the consumer's key and secret, (2) go back to the connection form in TeamCity, (3) paste the key and secret, and (4) save the connection.

After the connection is configured, a Bitbucket icon becomes active in several places where a repository URL can be specified. Click it to authorize TeamCity in your Bitbucket profile. TeamCity will be granted access to your public repositories, so you can quickly perform the actions listed above. For private repositories, you will need to provide Bitbucket credentials to be used for authentication by TeamCity, as Bitbucket Cloud does not provide non-expiring access tokens. See the [related discussion](https://bitbucket.org/site/master/issues/11774/application-specific-passwords-or-tokens).  
You can configure multiple Bitbucket connections. In this case, the server URL will be displayed next to each Bitbucket icon, so it is easier to distinguish the server in use.

## Docker Registry

A connection to Docker Registry can be used to:
* sign in to an authenticated registry before running a build / sign out after the build;
* clean up the published images after the build.

See more information in the [dedicated article](configuring-connections-to-docker.md).

## GitHub

>In TeamCity Cloud, a connection to GitHub.com is already predefined in the Root project's settings, which makes it available in all the other projects.
>
{product="tcc"}

There are two types of GitHub connections: GitHub Enterprise and GitHub.com. Choose it depending on your GitHub account type.

A connection to GitHub can be used to:
* create a [project from GitHub URL](creating-and-editing-projects.md#Creating+project+pointing+to+repository+URL);
* create a [VCS root from URL](guess-settings-from-repository-url.md);
* create a [Git](git.md) VCS root;
* integrate with a [GitHub](github.md) issue tracker;
* enable [GitHub.com authentication](configuring-authentication-settings.md#GitHub.com).

The connection form provides multiple parameters. Use them to [create an OAuth application in GitHub](https://docs.github.com/en/developers/apps/authorizing-oauth-apps). Then, (1) copy the app's client ID and secret, (2) go back to the connection form in TeamCity, (3) paste the GitHub server URL (only for Enterprise), the app ID and secret, and (4) save the connection. If you use a GitHub Enterprise server with HTTPS, you need to also upload its HTTPS certificate as described [here](uploading-ssl-certificates.md).

>If you enable the [GitHub.com authentication](configuring-authentication-settings.md#GitHub.com) module and want to restrict access to TeamCity to users of specific GitHub organizations, you need to ensure that your OAuth app is allowed by all these organizations. By default, GitHub does not allow OAuth apps to access the organizations. You can either disable this restriction for all apps or approve only the TeamCity app in each of the required organizations. Please refer to the [GitHub documentation](https://docs.github.com/en/github/setting-up-and-managing-organizations-and-teams/about-oauth-app-access-restrictions) for more details.

After the connection is configured, a GitHub icon becomes active in several places where a repository URL can be specified. Click it to authorize TeamCity in your GitHub profile. TeamCity will be granted full control of your private repositories and get the _Write repository hooks_ permission.  
You can configure multiple GitHub connections. In this case, the server URL will be displayed next to each GitHub icon, so it is easier to distinguish the server in use.

## GitLab

>In TeamCity Cloud, a connection to GitLab.com is already predefined in the Root project's settings, which makes it available in all the other projects.
>
{product="tcc"}

There are two types of GitLab connections: GitLab CE/EE and GitLab.com. Choose it depending on your GitHub account type.

A connection to GitLab can be used to:
* create a [project from GitLab URL](creating-and-editing-projects.md#Creating+project+pointing+to+repository+URL);
* create a [VCS root from URL](guess-settings-from-repository-url.md);
* enable [GitLab.com authentication](configuring-authentication-settings.md#GitLab.com).

The connection form provides multiple parameters. Use them to [create an OAuth application in GitLab](https://docs.gitlab.com/ee/integration/oauth_provider.html). Then, (1) copy the app's client ID and secret, (2) go back to the connection form in TeamCity, (3) paste the GitLab server URL (only for CE/EE), the app ID and secret, and (4) save the connection. If you use a GitLab CE/EE server with HTTPS, you need to also upload its HTTPS certificate as described [here](uploading-ssl-certificates.md).

>If you enable the [GitLab.com authentication](configuring-authentication-settings.md#GitHub.com) module and want to restrict access to TeamCity to users of specific GitHub organizations, you need to ensure that your OAuth app is allowed by all these organizations. By default, GitHub does not allow OAuth apps to access the organizations. You can either disable this restriction for all apps or approve only the TeamCity app in each of the required organizations. Please refer to the [GitHub documentation](https://docs.github.com/en/github/setting-up-and-managing-organizations-and-teams/about-oauth-app-access-restrictions) for more details.

After the connection is configured, a GitLab icon becomes active in several places where a repository URL can be specified. Click it to authorize TeamCity in your GitLab profile. TeamCity will be granted access to your repositories.  
You can configure multiple GitLab connections. In this case, the server URL will be displayed next to each GitLab icon, so it is easier to distinguish the server in use.

## Slack

## JetBrains Space

## NPM Registry

## Perforce Administrator Access

This type of connection allows [processing task streams on your Perforce server](perforce-workspace-handling-in-teamcity.md#Cleaning+Workspaces+on+Perforce+Server). In the connection settings, enter the host and user credentials for accessing the Perforce server (the user must have the [`admin` permission](https://www.perforce.com/manuals/p4sag/Content/P4SAG/protections.set.html#protections.set.access_levels)).