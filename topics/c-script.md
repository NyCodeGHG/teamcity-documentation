[//]: # (title: C# Script)
[//]: # (auxiliary-id: C# Script)

The _C# Script_ runner allows executing a [C#](https://docs.microsoft.com/en-us/dotnet/csharp/) script on Windows, Linux, or macOS.

Refer to [Configuring Build Steps](configuring-build-steps.md) for a description of common build steps' settings.

## Prerequisites

The runner's requirements:
* .NET runtime 3.1, 5 or, 6 must be installed on a build agent.
* The dedicated [C# Script interactive tool](https://www.nuget.org/packages/dotnet-csi/) must be [installed as an agent tool](installing-agent-tools.md).

## C# Script Settings

<table>

<tr>

<td>

Setting

</td>

<td>

Description

</td>

</tr>

<tr>

<td>

TeamCity C# script tool

</td>

<td>

Select a version of the TeamCity C# Script tool from those installed via __Administration | Tools__ or enter a custom path to this tool, relative to the [build checkout directory](build-checkout-directory.md).

</td>

</tr>

<tr>

<td>

Script type

</td>

<td>

Choose one of the two options: enter a custom script body right inside the runner or specify a path to a C# script file (`.csx`).

</td>

</tr>

<tr>

<td>

C# script

</td>

<td id="custom-script" auxiliary-id="kotlin-custom-script">

Available for the __Custom Script__ type.

Enter a code of a C# script.

</td>

</tr>

<tr>

<td id="script-file" auxiliary-id="kotlin-script-file">

C# script file

</td>

<td>

Available for the __Script File__ type.

Enter a path to the script file, relative to the [build checkout directory](build-checkout-directory.md).

</td>

</tr>

<tr>

<td>

Script parameters

</td>

<td>

Enter the parameters of the script, as in the command line. [Parameter references](configuring-build-parameters.md#parameter-reference) are supported.

For security reasons, we highly recommend that you avoid using parameter references directly inside scripts if these parameters represent secure values. You can pass such values via script parameters instead. For example, to pass a token value, [add a new build parameter](configuring-build-parameters.md) with the "Password" type, refer it in the runner’s _Script parameters_ field:

`%access_token%`

and call it as an argument within the script:

`val accessToken = args[0]`

This way, you can reuse the token’s value anywhere in the script.

This practice will ensure that these values are available on the agent only during the build. Otherwise, if the parameters are specified directly inside the script, their resolved values will be stored on the agent machine as long as the script itself is stored, which might compromise the security of your data.

</td>

</tr>

<tr>

<td>

NuGet package sources

</td>

<td>

Specify paths to NuGet sources to use for restoring packages.

</td>

</tr>


</table>