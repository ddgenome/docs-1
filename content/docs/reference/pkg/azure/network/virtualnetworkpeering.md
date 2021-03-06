
---
title: "VirtualNetworkPeering"
block_external_search_index: true
---

Manages a virtual network peering which allows resources to access other
resources in the linked virtual network.

## Note

Virtual Network peerings cannot be created, updated or deleted concurrently.

> This content is derived from https://github.com/terraform-providers/terraform-provider-azurerm/blob/master/website/docs/r/virtual_network_peering.html.markdown.



## Create a VirtualNetworkPeering Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/network/#VirtualNetworkPeering">VirtualNetworkPeering</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/network/#VirtualNetworkPeeringArgs">VirtualNetworkPeeringArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">VirtualNetworkPeering</span><span class="p">(resource_name, opts=None, </span>allow_forwarded_traffic=None<span class="p">, </span>allow_gateway_transit=None<span class="p">, </span>allow_virtual_network_access=None<span class="p">, </span>name=None<span class="p">, </span>remote_virtual_network_id=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>use_remote_gateways=None<span class="p">, </span>virtual_network_name=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewVirtualNetworkPeering<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#VirtualNetworkPeeringArgs">VirtualNetworkPeeringArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#VirtualNetworkPeering">VirtualNetworkPeering</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Network.VirtualNetworkPeering.html">VirtualNetworkPeering</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Network.Inputs.VirtualNetworkPeeringArgs.html">VirtualNetworkPeeringArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Allow<wbr>Forwarded<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allow<wbr>Gateway<wbr>Transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allow<wbr>Virtual<wbr>Network<wbr>Access</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Remote<wbr>Virtual<wbr>Network<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Remote<wbr>Gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Virtual<wbr>Network<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Allow<wbr>Forwarded<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allow<wbr>Gateway<wbr>Transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allow<wbr>Virtual<wbr>Network<wbr>Access</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Remote<wbr>Virtual<wbr>Network<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Remote<wbr>Gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Virtual<wbr>Network<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allow<wbr>Forwarded<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allow<wbr>Gateway<wbr>Transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allow<wbr>Virtual<wbr>Network<wbr>Access</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>remote<wbr>Virtual<wbr>Network<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use<wbr>Remote<wbr>Gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>virtual<wbr>Network<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allow_<wbr>forwarded_<wbr>traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allow_<wbr>gateway_<wbr>transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allow_<wbr>virtual_<wbr>network_<wbr>access</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>remote_<wbr>virtual_<wbr>network_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use_<wbr>remote_<wbr>gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>virtual_<wbr>network_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## VirtualNetworkPeering Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Allow<wbr>Forwarded<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Allow<wbr>Gateway<wbr>Transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Allow<wbr>Virtual<wbr>Network<wbr>Access</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Remote<wbr>Virtual<wbr>Network<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Use<wbr>Remote<wbr>Gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Virtual<wbr>Network<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Allow<wbr>Forwarded<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Allow<wbr>Gateway<wbr>Transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Allow<wbr>Virtual<wbr>Network<wbr>Access</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Remote<wbr>Virtual<wbr>Network<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Use<wbr>Remote<wbr>Gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Virtual<wbr>Network<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>allow<wbr>Forwarded<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>allow<wbr>Gateway<wbr>Transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>allow<wbr>Virtual<wbr>Network<wbr>Access</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>remote<wbr>Virtual<wbr>Network<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>use<wbr>Remote<wbr>Gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>virtual<wbr>Network<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>allow_<wbr>forwarded_<wbr>traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>allow_<wbr>gateway_<wbr>transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>allow_<wbr>virtual_<wbr>network_<wbr>access</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>remote_<wbr>virtual_<wbr>network_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>use_<wbr>remote_<wbr>gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>virtual_<wbr>network_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing VirtualNetworkPeering Resource

Get an existing VirtualNetworkPeering resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/network/#VirtualNetworkPeeringState">VirtualNetworkPeeringState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/network/#VirtualNetworkPeering">VirtualNetworkPeering</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>allow_forwarded_traffic=None<span class="p">, </span>allow_gateway_transit=None<span class="p">, </span>allow_virtual_network_access=None<span class="p">, </span>name=None<span class="p">, </span>remote_virtual_network_id=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>use_remote_gateways=None<span class="p">, </span>virtual_network_name=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetVirtualNetworkPeering<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#VirtualNetworkPeeringState">VirtualNetworkPeeringState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/network?tab=doc#VirtualNetworkPeering">VirtualNetworkPeering</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Network.VirtualNetworkPeering.html">VirtualNetworkPeering</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Network.VirtualNetworkPeeringState.html">VirtualNetworkPeeringState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Allow<wbr>Forwarded<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allow<wbr>Gateway<wbr>Transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allow<wbr>Virtual<wbr>Network<wbr>Access</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Remote<wbr>Virtual<wbr>Network<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Remote<wbr>Gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Virtual<wbr>Network<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Allow<wbr>Forwarded<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allow<wbr>Gateway<wbr>Transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allow<wbr>Virtual<wbr>Network<wbr>Access</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Remote<wbr>Virtual<wbr>Network<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Remote<wbr>Gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Virtual<wbr>Network<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allow<wbr>Forwarded<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allow<wbr>Gateway<wbr>Transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allow<wbr>Virtual<wbr>Network<wbr>Access</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>remote<wbr>Virtual<wbr>Network<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use<wbr>Remote<wbr>Gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>virtual<wbr>Network<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allow_<wbr>forwarded_<wbr>traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if forwarded traffic from  VMs
in the remote virtual network is allowed. Defaults to false.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allow_<wbr>gateway_<wbr>transit</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls gatewayLinks can be used in the
remote virtual network’s link to the local virtual network.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allow_<wbr>virtual_<wbr>network_<wbr>access</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if the VMs in the remote
virtual network can access VMs in the local virtual network. Defaults to
true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network peering. Changing this
forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>remote_<wbr>virtual_<wbr>network_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The full Azure resource ID of the
remote virtual network.  Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to
create the virtual network. Changing this forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use_<wbr>remote_<wbr>gateways</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Controls if remote gateways can be used on
the local virtual network. If the flag is set to `true`, and
`allow_gateway_transit` on the remote peering is also `true`, virtual network will
use gateways of remote virtual network for transit. Only one peering can
have this flag set to `true`. This flag cannot be set if virtual network
already has a gateway. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>virtual_<wbr>network_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the virtual network. Changing
this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}









