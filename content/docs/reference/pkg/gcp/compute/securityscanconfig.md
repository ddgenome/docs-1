
---
title: "SecurityScanConfig"
block_external_search_index: true
---

A ScanConfig resource contains the configurations to launch a scan.

To get more information about ScanConfig, see:

* [API documentation](https://cloud.google.com/security-scanner/docs/reference/rest/v1beta/projects.scanConfigs)
* How-to Guides
    * [Using Cloud Security Scanner](https://cloud.google.com/security-scanner/docs/scanning)

> This content is derived from https://github.com/terraform-providers/terraform-provider-google/blob/master/website/docs/r/security_scanner_scan_config.html.markdown.



## Create a SecurityScanConfig Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#SecurityScanConfig">SecurityScanConfig</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#SecurityScanConfigArgs">SecurityScanConfigArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">SecurityScanConfig</span><span class="p">(resource_name, opts=None, </span>authentication=None<span class="p">, </span>blacklist_patterns=None<span class="p">, </span>display_name=None<span class="p">, </span>export_to_security_command_center=None<span class="p">, </span>max_qps=None<span class="p">, </span>project=None<span class="p">, </span>schedule=None<span class="p">, </span>starting_urls=None<span class="p">, </span>target_platforms=None<span class="p">, </span>user_agent=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewSecurityScanConfig<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfigArgs">SecurityScanConfigArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfig">SecurityScanConfig</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.SecurityScanConfig.html">SecurityScanConfig</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.Inputs.SecurityScanConfigArgs.html">SecurityScanConfigArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language nodejs %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resource.</dd>
    <dt class="property-optional" title="Optional">
        <span>args</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The arguments to use to populate this resource's properties.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resource.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>
{{% /choosable %}}

{{% choosable language go %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resource.</dd>
    <dt class="property-optional" title="Optional">
        <span>args</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The arguments to use to populate this resource's properties.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

{{% choosable language csharp %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resource.</dd>
    <dt class="property-optional" title="Optional">
        <span>args</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The arguments to use to populate this resource's properties.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

#### Resource Arguments




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Blacklist<wbr>Patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Export<wbr>To<wbr>Security<wbr>Command<wbr>Center</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Max<wbr>Qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">Security<wbr>Scan<wbr>Config<wbr>Schedule<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Starting<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>User<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">*Security<wbr>Scan<wbr>Config<wbr>Authentication</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Blacklist<wbr>Patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Export<wbr>To<wbr>Security<wbr>Command<wbr>Center</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Max<wbr>Qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">*Security<wbr>Scan<wbr>Config<wbr>Schedule</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Starting<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>User<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">Security<wbr>Scan<wbr>Config<wbr>Authentication?</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>blacklist<wbr>Patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>export<wbr>To<wbr>Security<wbr>Command<wbr>Center</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>max<wbr>Qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">Security<wbr>Scan<wbr>Config<wbr>Schedule?</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>starting<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>user<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">Dict[Security<wbr>Scan<wbr>Config<wbr>Authentication]</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>blacklist_<wbr>patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>display_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>export_<wbr>to_<wbr>security_<wbr>command_<wbr>center</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>max_<wbr>qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">Dict[Security<wbr>Scan<wbr>Config<wbr>Schedule]</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>starting_<wbr>urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>user_<wbr>agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## SecurityScanConfig Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">Security<wbr>Scan<wbr>Config<wbr>Authentication?</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Blacklist<wbr>Patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Export<wbr>To<wbr>Security<wbr>Command<wbr>Center</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Max<wbr>Qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A server defined name for this index. Format: 'projects/{{project}}/scanConfigs/{{server_generated_id}}'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">Security<wbr>Scan<wbr>Config<wbr>Schedule?</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Starting<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target<wbr>Platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>User<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">*Security<wbr>Scan<wbr>Config<wbr>Authentication</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Blacklist<wbr>Patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Export<wbr>To<wbr>Security<wbr>Command<wbr>Center</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Max<wbr>Qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A server defined name for this index. Format: 'projects/{{project}}/scanConfigs/{{server_generated_id}}'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">*Security<wbr>Scan<wbr>Config<wbr>Schedule</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Starting<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target<wbr>Platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>User<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">Security<wbr>Scan<wbr>Config<wbr>Authentication?</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>blacklist<wbr>Patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>export<wbr>To<wbr>Security<wbr>Command<wbr>Center</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>max<wbr>Qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A server defined name for this index. Format: 'projects/{{project}}/scanConfigs/{{server_generated_id}}'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">Security<wbr>Scan<wbr>Config<wbr>Schedule?</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>starting<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target<wbr>Platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>user<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">Dict[Security<wbr>Scan<wbr>Config<wbr>Authentication]</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>blacklist_<wbr>patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>display_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>export_<wbr>to_<wbr>security_<wbr>command_<wbr>center</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>max_<wbr>qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A server defined name for this index. Format: 'projects/{{project}}/scanConfigs/{{server_generated_id}}'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">Dict[Security<wbr>Scan<wbr>Config<wbr>Schedule]</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>starting_<wbr>urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target_<wbr>platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>user_<wbr>agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing SecurityScanConfig Resource

Get an existing SecurityScanConfig resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#SecurityScanConfigState">SecurityScanConfigState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#SecurityScanConfig">SecurityScanConfig</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>authentication=None<span class="p">, </span>blacklist_patterns=None<span class="p">, </span>display_name=None<span class="p">, </span>export_to_security_command_center=None<span class="p">, </span>max_qps=None<span class="p">, </span>name=None<span class="p">, </span>project=None<span class="p">, </span>schedule=None<span class="p">, </span>starting_urls=None<span class="p">, </span>target_platforms=None<span class="p">, </span>user_agent=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetSecurityScanConfig<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfigState">SecurityScanConfigState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfig">SecurityScanConfig</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.SecurityScanConfig.html">SecurityScanConfig</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.SecurityScanConfigState.html">SecurityScanConfigState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language nodejs %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Required">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>state</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>Any extra arguments used during the lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>resource_name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
</dl>
{{% /choosable %}}

{{% choosable language go %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Required">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>state</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>Any extra arguments used during the lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

{{% choosable language csharp %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Required">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>state</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>Any extra arguments used during the lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

The following state arguments are supported:



{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Blacklist<wbr>Patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Export<wbr>To<wbr>Security<wbr>Command<wbr>Center</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Max<wbr>Qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A server defined name for this index. Format: 'projects/{{project}}/scanConfigs/{{server_generated_id}}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">Security<wbr>Scan<wbr>Config<wbr>Schedule<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Starting<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>User<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">*Security<wbr>Scan<wbr>Config<wbr>Authentication</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Blacklist<wbr>Patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Export<wbr>To<wbr>Security<wbr>Command<wbr>Center</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Max<wbr>Qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A server defined name for this index. Format: 'projects/{{project}}/scanConfigs/{{server_generated_id}}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">*Security<wbr>Scan<wbr>Config<wbr>Schedule</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Starting<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>User<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">Security<wbr>Scan<wbr>Config<wbr>Authentication?</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>blacklist<wbr>Patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>export<wbr>To<wbr>Security<wbr>Command<wbr>Center</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>max<wbr>Qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A server defined name for this index. Format: 'projects/{{project}}/scanConfigs/{{server_generated_id}}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">Security<wbr>Scan<wbr>Config<wbr>Schedule?</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>starting<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>user<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthentication">Dict[Security<wbr>Scan<wbr>Config<wbr>Authentication]</a></span>
    </dt>
    <dd>{{% md %}}The authentication configuration. If specified, service will use the authentication configuration during scanning.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>blacklist_<wbr>patterns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}The blacklist URL patterns as described in https://cloud.google.com/security-scanner/docs/excluded-urls
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>display_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The user provider display name of the ScanConfig.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>export_<wbr>to_<wbr>security_<wbr>command_<wbr>center</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Controls export of scan configurations and results to Cloud Security Command Center.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>max_<wbr>qps</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The maximum QPS during scanning. A valid value ranges from 5 to 20 inclusively. Defaults to 15.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A server defined name for this index. Format: 'projects/{{project}}/scanConfigs/{{server_generated_id}}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the project in which the resource belongs.
If it is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigschedule">Dict[Security<wbr>Scan<wbr>Config<wbr>Schedule]</a></span>
    </dt>
    <dd>{{% md %}}The schedule of the ScanConfig
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>starting_<wbr>urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}The starting URLs from which the scanner finds site pages.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>platforms</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Set of Cloud Platforms targeted by the scan. If empty, APP_ENGINE will be used as a default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>user_<wbr>agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Type of the user agents used for scanning
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Security<wbr>Scan<wbr>Config<wbr>Authentication</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#SecurityScanConfigAuthentication">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#SecurityScanConfigAuthentication">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfigAuthenticationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfigAuthenticationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Account</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthenticationcustomaccount">Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Custom<wbr>Account<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Google<wbr>Account</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthenticationgoogleaccount">Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Google<wbr>Account<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Account</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthenticationcustomaccount">*Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Custom<wbr>Account</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Google<wbr>Account</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthenticationgoogleaccount">*Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Google<wbr>Account</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>custom<wbr>Account</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthenticationcustomaccount">Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Custom<wbr>Account?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>google<wbr>Account</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthenticationgoogleaccount">Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Google<wbr>Account?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>custom<wbr>Account</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthenticationcustomaccount">Dict[Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Custom<wbr>Account]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>google<wbr>Account</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityscanconfigauthenticationgoogleaccount">Dict[Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Google<wbr>Account]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Custom<wbr>Account</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#SecurityScanConfigAuthenticationCustomAccount">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#SecurityScanConfigAuthenticationCustomAccount">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfigAuthenticationCustomAccountArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfigAuthenticationCustomAccountOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Login<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Login<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>login<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>login<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Security<wbr>Scan<wbr>Config<wbr>Authentication<wbr>Google<wbr>Account</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#SecurityScanConfigAuthenticationGoogleAccount">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#SecurityScanConfigAuthenticationGoogleAccount">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfigAuthenticationGoogleAccountArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfigAuthenticationGoogleAccountOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Security<wbr>Scan<wbr>Config<wbr>Schedule</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#SecurityScanConfigSchedule">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#SecurityScanConfigSchedule">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfigScheduleArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#SecurityScanConfigScheduleOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Interval<wbr>Duration<wbr>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Interval<wbr>Duration<wbr>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>interval<wbr>Duration<wbr>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>interval<wbr>Duration<wbr>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}







