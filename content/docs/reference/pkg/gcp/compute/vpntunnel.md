
---
title: "VPNTunnel"
block_external_search_index: true
---

VPN tunnel resource.


To get more information about VpnTunnel, see:

* [API documentation](https://cloud.google.com/compute/docs/reference/rest/v1/vpnTunnels)
* How-to Guides
    * [Cloud VPN Overview](https://cloud.google.com/vpn/docs/concepts/overview)
    * [Networks and Tunnel Routing](https://cloud.google.com/vpn/docs/concepts/choosing-networks-routing)

> This content is derived from https://github.com/terraform-providers/terraform-provider-google/blob/master/website/docs/r/compute_vpn_tunnel.html.markdown.



## Create a VPNTunnel Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#VPNTunnel">VPNTunnel</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#VPNTunnelArgs">VPNTunnelArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">VPNTunnel</span><span class="p">(resource_name, opts=None, </span>description=None<span class="p">, </span>ike_version=None<span class="p">, </span>labels=None<span class="p">, </span>local_traffic_selectors=None<span class="p">, </span>name=None<span class="p">, </span>peer_external_gateway=None<span class="p">, </span>peer_external_gateway_interface=None<span class="p">, </span>peer_gcp_gateway=None<span class="p">, </span>peer_ip=None<span class="p">, </span>project=None<span class="p">, </span>region=None<span class="p">, </span>remote_traffic_selectors=None<span class="p">, </span>router=None<span class="p">, </span>shared_secret=None<span class="p">, </span>target_vpn_gateway=None<span class="p">, </span>vpn_gateway=None<span class="p">, </span>vpn_gateway_interface=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewVPNTunnel<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#VPNTunnelArgs">VPNTunnelArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#VPNTunnel">VPNTunnel</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.VPNTunnel.html">VPNTunnel</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.Inputs.VPNTunnelArgs.html">VPNTunnelArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ike<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Local<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>External<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>External<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>Gcp<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Remote<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Router</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Shared<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpn<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ike<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Local<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>External<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>External<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>Gcp<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Remote<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Router</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Shared<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpn<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ike<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>local<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer<wbr>External<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer<wbr>External<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer<wbr>Gcp<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>remote<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>router</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>shared<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpn<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ike_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>local_<wbr>traffic_<wbr>selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer_<wbr>external_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer_<wbr>external_<wbr>gateway_<wbr>interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer_<wbr>gcp_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer_<wbr>ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>remote_<wbr>traffic_<wbr>selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>router</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>shared_<wbr>secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>vpn_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpn_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpn_<wbr>gateway_<wbr>interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## VPNTunnel Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Detailed<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Detailed status message for the VPN tunnel.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ike<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Local<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Peer<wbr>External<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Peer<wbr>External<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Peer<wbr>Gcp<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Peer<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Remote<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Router</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Shared<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Shared<wbr>Secret<wbr>Hash</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Hash of the shared secret.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target<wbr>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tunnel<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the resource. This identifier is defined by the server.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Vpn<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Detailed<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Detailed status message for the VPN tunnel.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ike<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Local<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Peer<wbr>External<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Peer<wbr>External<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Peer<wbr>Gcp<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Peer<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Remote<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Router</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Shared<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Shared<wbr>Secret<wbr>Hash</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Hash of the shared secret.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target<wbr>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tunnel<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the resource. This identifier is defined by the server.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Vpn<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>detailed<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Detailed status message for the VPN tunnel.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ike<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>local<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>peer<wbr>External<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>peer<wbr>External<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>peer<wbr>Gcp<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>peer<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>remote<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>router</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>shared<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>shared<wbr>Secret<wbr>Hash</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Hash of the shared secret.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target<wbr>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tunnel<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the resource. This identifier is defined by the server.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>vpn<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>creation_<wbr>timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>detailed_<wbr>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Detailed status message for the VPN tunnel.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ike_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>label_<wbr>fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>local_<wbr>traffic_<wbr>selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>peer_<wbr>external_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>peer_<wbr>external_<wbr>gateway_<wbr>interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>peer_<wbr>gcp_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>peer_<wbr>ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>remote_<wbr>traffic_<wbr>selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>router</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>self_<wbr>link</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>shared_<wbr>secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>shared_<wbr>secret_<wbr>hash</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Hash of the shared secret.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target_<wbr>vpn_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tunnel_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the resource. This identifier is defined by the server.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>vpn_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>vpn_<wbr>gateway_<wbr>interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing VPNTunnel Resource

Get an existing VPNTunnel resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#VPNTunnelState">VPNTunnelState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#VPNTunnel">VPNTunnel</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>creation_timestamp=None<span class="p">, </span>description=None<span class="p">, </span>detailed_status=None<span class="p">, </span>ike_version=None<span class="p">, </span>label_fingerprint=None<span class="p">, </span>labels=None<span class="p">, </span>local_traffic_selectors=None<span class="p">, </span>name=None<span class="p">, </span>peer_external_gateway=None<span class="p">, </span>peer_external_gateway_interface=None<span class="p">, </span>peer_gcp_gateway=None<span class="p">, </span>peer_ip=None<span class="p">, </span>project=None<span class="p">, </span>region=None<span class="p">, </span>remote_traffic_selectors=None<span class="p">, </span>router=None<span class="p">, </span>self_link=None<span class="p">, </span>shared_secret=None<span class="p">, </span>shared_secret_hash=None<span class="p">, </span>target_vpn_gateway=None<span class="p">, </span>tunnel_id=None<span class="p">, </span>vpn_gateway=None<span class="p">, </span>vpn_gateway_interface=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetVPNTunnel<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#VPNTunnelState">VPNTunnelState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#VPNTunnel">VPNTunnel</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.VPNTunnel.html">VPNTunnel</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.VPNTunnelState.html">VPNTunnelState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Detailed<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Detailed status message for the VPN tunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ike<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Local<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>External<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>External<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>Gcp<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Remote<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Router</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Shared<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Shared<wbr>Secret<wbr>Hash</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Hash of the shared secret.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tunnel<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the resource. This identifier is defined by the server.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpn<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Detailed<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Detailed status message for the VPN tunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ike<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Local<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>External<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>External<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>Gcp<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Peer<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Remote<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Router</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Shared<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Shared<wbr>Secret<wbr>Hash</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Hash of the shared secret.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tunnel<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the resource. This identifier is defined by the server.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpn<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>detailed<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Detailed status message for the VPN tunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ike<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>local<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer<wbr>External<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer<wbr>External<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer<wbr>Gcp<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>remote<wbr>Traffic<wbr>Selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>router</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>shared<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>shared<wbr>Secret<wbr>Hash</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Hash of the shared secret.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tunnel<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the resource. This identifier is defined by the server.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpn<wbr>Gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpn<wbr>Gateway<wbr>Interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>creation_<wbr>timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>detailed_<wbr>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Detailed status message for the VPN tunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ike_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}IKE protocol version to use when establishing the VPN tunnel with peer VPN gateway. Acceptable IKE versions are 1 or 2.
Default version is 2.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>label_<wbr>fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this VpnTunnel.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>local_<wbr>traffic_<wbr>selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Local traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the resource. The name must be 1-63 characters long, and comply with RFC1035. Specifically, the name must be
1-63 characters long and match the regular expression '[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must
be a lowercase letter, and all following characters must be a dash, lowercase letter, or digit, except the last
character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer_<wbr>external_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the peer side external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer_<wbr>external_<wbr>gateway_<wbr>interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The interface ID of the external VPN gateway to which this VPN tunnel is connected.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer_<wbr>gcp_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the peer side HA GCP VPN gateway to which this VPN tunnel is connected. If provided, the VPN tunnel will
automatically use the same vpn_gateway_interface ID in the peer GCP VPN gateway. This field must reference a
'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>peer_<wbr>ip</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}IP address of the peer VPN gateway. Only IPv4 is supported.
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
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The region where the tunnel is located. If unset, is set to the region of 'target_vpn_gateway'.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>remote_<wbr>traffic_<wbr>selectors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Remote traffic selector to use when establishing the VPN tunnel with peer VPN gateway. The value should be a CIDR
formatted string, for example '192.168.0.0/16'. The ranges should be disjoint. Only IPv4 is supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>router</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of router resource to be used for dynamic routing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>self_<wbr>link</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>shared_<wbr>secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Shared secret used to set the secure session between the Cloud VPN gateway and the peer VPN gateway.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>shared_<wbr>secret_<wbr>hash</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Hash of the shared secret.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>vpn_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the Target VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tunnel_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the resource. This identifier is defined by the server.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpn_<wbr>gateway</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the VPN gateway with which this VPN tunnel is associated. This must be used if a High Availability VPN gateway
resource is created. This field must reference a 'google_compute_ha_vpn_gateway' resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpn_<wbr>gateway_<wbr>interface</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The interface ID of the VPN gateway with which this VPN tunnel is associated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}









