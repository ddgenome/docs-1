
---
title: "TrafficManagerEndpoint"
block_external_search_index: true
---

Manages a Traffic Manager Endpoint.

> This content is derived from https://github.com/terraform-providers/terraform-provider-azurerm/blob/master/website/docs/r/traffic_manager_endpoint.html.markdown.



## Create a TrafficManagerEndpoint Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/network/#TrafficManagerEndpoint">TrafficManagerEndpoint</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/network/#TrafficManagerEndpointArgs">TrafficManagerEndpointArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">TrafficManagerEndpoint</span><span class="p">(resource_name, opts=None, </span>custom_headers=None<span class="p">, </span>endpoint_location=None<span class="p">, </span>endpoint_status=None<span class="p">, </span>geo_mappings=None<span class="p">, </span>min_child_endpoints=None<span class="p">, </span>name=None<span class="p">, </span>priority=None<span class="p">, </span>profile_name=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>subnets=None<span class="p">, </span>target=None<span class="p">, </span>target_resource_id=None<span class="p">, </span>type=None<span class="p">, </span>weight=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewTrafficManagerEndpoint<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#TrafficManagerEndpointArgs">TrafficManagerEndpointArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#TrafficManagerEndpoint">TrafficManagerEndpoint</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Network.TrafficManagerEndpoint.html">TrafficManagerEndpoint</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Network.Inputs.TrafficManagerEndpointArgs.html">TrafficManagerEndpointArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Custom<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">List&lt;Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Geo<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Min<wbr>Child<wbr>Endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Profile<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">List&lt;Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">[]Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Geo<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Min<wbr>Child<wbr>Endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Profile<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">[]Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>custom<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>geo<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>min<wbr>Child<wbr>Endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>profile<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>custom_<wbr>headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">List[Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header]</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint_<wbr>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint_<wbr>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>geo_<wbr>mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>min_<wbr>child_<wbr>endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>profile_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">List[Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet]</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>resource_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## TrafficManagerEndpoint Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Custom<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">List&lt;Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Endpoint<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Endpoint<wbr>Monitor<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Endpoint<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Geo<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Min<wbr>Child<wbr>Endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Profile<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">List&lt;Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target<wbr>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Custom<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">[]Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Endpoint<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Endpoint<wbr>Monitor<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Endpoint<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Geo<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Min<wbr>Child<wbr>Endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Profile<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">[]Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target<wbr>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>custom<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>endpoint<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>endpoint<wbr>Monitor<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>endpoint<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>geo<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>min<wbr>Child<wbr>Endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>profile<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target<wbr>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>custom_<wbr>headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">List[Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header]</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>endpoint_<wbr>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>endpoint_<wbr>monitor_<wbr>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>endpoint_<wbr>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>geo_<wbr>mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>min_<wbr>child_<wbr>endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>profile_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">List[Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet]</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target_<wbr>resource_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing TrafficManagerEndpoint Resource

Get an existing TrafficManagerEndpoint resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/network/#TrafficManagerEndpointState">TrafficManagerEndpointState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/network/#TrafficManagerEndpoint">TrafficManagerEndpoint</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>custom_headers=None<span class="p">, </span>endpoint_location=None<span class="p">, </span>endpoint_monitor_status=None<span class="p">, </span>endpoint_status=None<span class="p">, </span>geo_mappings=None<span class="p">, </span>min_child_endpoints=None<span class="p">, </span>name=None<span class="p">, </span>priority=None<span class="p">, </span>profile_name=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>subnets=None<span class="p">, </span>target=None<span class="p">, </span>target_resource_id=None<span class="p">, </span>type=None<span class="p">, </span>weight=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetTrafficManagerEndpoint<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#TrafficManagerEndpointState">TrafficManagerEndpointState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#TrafficManagerEndpoint">TrafficManagerEndpoint</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Network.TrafficManagerEndpoint.html">TrafficManagerEndpoint</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Network.TrafficManagerEndpointState.html">TrafficManagerEndpointState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Custom<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">List&lt;Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Monitor<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Geo<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Min<wbr>Child<wbr>Endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Profile<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">List&lt;Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">[]Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Monitor<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Geo<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Min<wbr>Child<wbr>Endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Profile<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">[]Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>custom<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint<wbr>Monitor<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>geo<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>min<wbr>Child<wbr>Endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>profile<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>custom_<wbr>headers</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointcustomheader">List[Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header]</a></span>
    </dt>
    <dd>{{% md %}}One or more `custom_header` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint_<wbr>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure location of the Endpoint,
this must be specified for Profiles using the `Performance` routing method
if the Endpoint is of either type `nestedEndpoints` or `externalEndpoints`.
For Endpoints of type `azureEndpoints` the value will be taken from the
location of the Azure target resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint_<wbr>monitor_<wbr>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint_<wbr>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The status of the Endpoint, can be set to
either `Enabled` or `Disabled`. Defaults to `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>geo_<wbr>mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of Geographic Regions used to distribute traffic, such as `WORLD`, `UK` or `DE`. The same location can't be specified in two endpoints. [See the Geographic Hierarchies documentation for more information](https://docs.microsoft.com/en-us/rest/api/trafficmanager/geographichierarchies/getdefault).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>min_<wbr>child_<wbr>endpoints</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}This argument specifies the minimum number
of endpoints that must be ‘online’ in the child profile in order for the
parent profile to direct traffic to any of the endpoints in that child
profile. This argument only applies to Endpoints of type `nestedEndpoints`
and defaults to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager endpoint. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the priority of this Endpoint, this must be
specified for Profiles using the `Priority` traffic routing method. Supports
values between 1 and 1000, with no Endpoints sharing the same value. If
omitted the value will be computed in order of creation.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>profile_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the Traffic Manager Profile to attach
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the Traffic Manager endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#trafficmanagerendpointsubnet">List[Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet]</a></span>
    </dt>
    <dd>{{% md %}}One or more `subnet` blocks as defined below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The FQDN DNS name of the target. This argument must be
provided for an endpoint of type `externalEndpoints`, for other types it
will be computed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>resource_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The resource id of an Azure resource to
target. This argument must be provided for an endpoint of type
`azureEndpoints` or `nestedEndpoints`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Endpoint type, must be one of:
- `azureEndpoints`
- `externalEndpoints`
- `nestedEndpoints`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>weight</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies how much traffic should be distributed to this
endpoint, this must be specified for Profiles using the  `Weighted` traffic
routing method. Supports values between 1 and 1000.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Traffic<wbr>Manager<wbr>Endpoint<wbr>Custom<wbr>Header</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#TrafficManagerEndpointCustomHeader">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#TrafficManagerEndpointCustomHeader">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#TrafficManagerEndpointCustomHeaderArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#TrafficManagerEndpointCustomHeaderOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the custom header.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The value of custom header. Applicable for Http and Https protocol.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the custom header.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The value of custom header. Applicable for Http and Https protocol.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the custom header.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The value of custom header. Applicable for Http and Https protocol.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the custom header.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>value</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The value of custom header. Applicable for Http and Https protocol.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Traffic<wbr>Manager<wbr>Endpoint<wbr>Subnet</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#TrafficManagerEndpointSubnet">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#TrafficManagerEndpointSubnet">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#TrafficManagerEndpointSubnetArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#TrafficManagerEndpointSubnetOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>First</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The First IP....
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Last</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Last IP...
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Scope</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The Scope...
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>First</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The First IP....
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Last</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Last IP...
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Scope</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The Scope...
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>first</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The First IP....
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>last</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Last IP...
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>scope</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The Scope...
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>first</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The First IP....
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>last</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Last IP...
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>scope</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The Scope...
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







