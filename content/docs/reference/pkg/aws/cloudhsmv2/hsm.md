
---
title: "Hsm"
block_external_search_index: true
---

Creates an HSM module in Amazon CloudHSM v2 cluster.

## Example Usage

The following example below creates an HSM module in CloudHSM cluster.

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const cluster = aws.cloudhsmv2.getCluster({
    clusterId: var_cloudhsm_cluster_id,
});
const cloudhsmV2Hsm = new aws.cloudhsmv2.Hsm("cloudhsm_v2_hsm", {
    clusterId: cluster.clusterId,
    subnetId: cluster.subnetIds[0],
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/cloudhsm_v2_hsm.html.markdown.



## Create a Hsm Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cloudhsmv2/#Hsm">Hsm</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cloudhsmv2/#HsmArgs">HsmArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">Hsm</span><span class="p">(resource_name, opts=None, </span>availability_zone=None<span class="p">, </span>cluster_id=None<span class="p">, </span>ip_address=None<span class="p">, </span>subnet_id=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewHsm<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cloudhsmv2?tab=doc#HsmArgs">HsmArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cloudhsmv2?tab=doc#Hsm">Hsm</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cloudhsmv2.Hsm.html">Hsm</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.CloudHsmV2.Inputs.HsmArgs.html">HsmArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Cluster<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Cluster<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>cluster<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>availability_<wbr>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>cluster_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ip_<wbr>address</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subnet_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## Hsm Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Cluster<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hsm<wbr>Eni<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the ENI interface allocated for HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hsm<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The state of the HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Cluster<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hsm<wbr>Eni<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the ENI interface allocated for HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hsm<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hsm<wbr>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The state of the HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>cluster<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hsm<wbr>Eni<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the ENI interface allocated for HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hsm<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hsm<wbr>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The state of the HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>availability_<wbr>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>cluster_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hsm_<wbr>eni_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The id of the ENI interface allocated for HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hsm_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The id of the HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hsm_<wbr>state</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The state of the HSM module.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ip_<wbr>address</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>subnet_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing Hsm Resource

Get an existing Hsm resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cloudhsmv2/#HsmState">HsmState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cloudhsmv2/#Hsm">Hsm</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>availability_zone=None<span class="p">, </span>cluster_id=None<span class="p">, </span>hsm_eni_id=None<span class="p">, </span>hsm_id=None<span class="p">, </span>hsm_state=None<span class="p">, </span>ip_address=None<span class="p">, </span>subnet_id=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetHsm<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cloudhsmv2?tab=doc#HsmState">HsmState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cloudhsmv2?tab=doc#Hsm">Hsm</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cloudhsmv2.Hsm.html">Hsm</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cloudhsmv2.HsmState.html">HsmState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cluster<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hsm<wbr>Eni<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The id of the ENI interface allocated for HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hsm<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The id of the HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The state of the HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cluster<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hsm<wbr>Eni<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The id of the ENI interface allocated for HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hsm<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The id of the HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hsm<wbr>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The state of the HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cluster<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hsm<wbr>Eni<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The id of the ENI interface allocated for HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hsm<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The id of the HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hsm<wbr>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The state of the HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>availability_<wbr>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IDs of AZ in which HSM module will be located. Do not use together with subnet_id.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cluster_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of Cloud HSM v2 cluster to which HSM will be added.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hsm_<wbr>eni_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The id of the ENI interface allocated for HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hsm_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The id of the HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hsm_<wbr>state</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The state of the HSM module.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ip_<wbr>address</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IP address of HSM module. Must be within the CIDR of selected subnet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subnet_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of subnet in which HSM module will be located.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}









