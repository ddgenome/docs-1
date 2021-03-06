
---
title: "EngineSplitTraffic"
block_external_search_index: true
---

Traffic routing configuration for versions within a single service. Traffic splits define how traffic directed to the service is assigned to versions.


To get more information about ServiceSplitTraffic, see:

* [API documentation](https://cloud.google.com/appengine/docs/admin-api/reference/rest/v1/apps.services)

> This content is derived from https://github.com/terraform-providers/terraform-provider-google/blob/master/website/docs/r/app_engine_service_split_traffic.html.markdown.



## Create a EngineSplitTraffic Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/appengine/#EngineSplitTraffic">EngineSplitTraffic</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/appengine/#EngineSplitTrafficArgs">EngineSplitTrafficArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">EngineSplitTraffic</span><span class="p">(resource_name, opts=None, </span>migrate_traffic=None<span class="p">, </span>project=None<span class="p">, </span>service=None<span class="p">, </span>split=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewEngineSplitTraffic<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/appengine?tab=doc#EngineSplitTrafficArgs">EngineSplitTrafficArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/appengine?tab=doc#EngineSplitTraffic">EngineSplitTraffic</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Appengine.EngineSplitTraffic.html">EngineSplitTraffic</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.AppEngine.Inputs.EngineSplitTrafficArgs.html">EngineSplitTrafficArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Migrate<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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

    <dt class="property-required"
            title="Required">
        <span>Service</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Pulumi.<wbr>Gcp.<wbr>App<wbr>Engine.<wbr>Inputs.<wbr>Engine<wbr>Split<wbr>Traffic<wbr>Split<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Migrate<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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

    <dt class="property-required"
            title="Required">
        <span>Service</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Engine<wbr>Split<wbr>Traffic<wbr>Split</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>migrate<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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

    <dt class="property-required"
            title="Required">
        <span>service</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Engine<wbr>Split<wbr>Traffic<wbr>Split</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>migrate_<wbr>traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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

    <dt class="property-required"
            title="Required">
        <span>service</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Dict[Engine<wbr>Split<wbr>Traffic<wbr>Split]</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## EngineSplitTraffic Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Migrate<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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
        <span>Service</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Pulumi.<wbr>Gcp.<wbr>App<wbr>Engine.<wbr>Outputs.<wbr>Engine<wbr>Split<wbr>Traffic<wbr>Split</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Migrate<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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
        <span>Service</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Engine<wbr>Split<wbr>Traffic<wbr>Split</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>migrate<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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
        <span>service</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Engine<wbr>Split<wbr>Traffic<wbr>Split</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>migrate_<wbr>traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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
        <span>service</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Dict[Engine<wbr>Split<wbr>Traffic<wbr>Split]</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing EngineSplitTraffic Resource

Get an existing EngineSplitTraffic resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/appengine/#EngineSplitTrafficState">EngineSplitTrafficState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/appengine/#EngineSplitTraffic">EngineSplitTraffic</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>migrate_traffic=None<span class="p">, </span>project=None<span class="p">, </span>service=None<span class="p">, </span>split=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetEngineSplitTraffic<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/appengine?tab=doc#EngineSplitTrafficState">EngineSplitTrafficState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/appengine?tab=doc#EngineSplitTraffic">EngineSplitTraffic</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Appengine.EngineSplitTraffic.html">EngineSplitTraffic</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Appengine.EngineSplitTrafficState.html">EngineSplitTrafficState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Migrate<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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
        <span>Service</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Pulumi.<wbr>Gcp.<wbr>App<wbr>Engine.<wbr>Inputs.<wbr>Engine<wbr>Split<wbr>Traffic<wbr>Split<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Migrate<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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
        <span>Service</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">*Engine<wbr>Split<wbr>Traffic<wbr>Split</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>migrate<wbr>Traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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
        <span>service</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Engine<wbr>Split<wbr>Traffic<wbr>Split?</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>migrate_<wbr>traffic</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If set to true traffic will be migrated to this version.
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
        <span>service</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the service these settings apply to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>split</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#enginesplittrafficsplit">Dict[Engine<wbr>Split<wbr>Traffic<wbr>Split]</a></span>
    </dt>
    <dd>{{% md %}}Mapping that defines fractional HTTP traffic diversion to different versions within the service.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Engine<wbr>Split<wbr>Traffic<wbr>Split</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#EngineSplitTrafficSplit">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#EngineSplitTrafficSplit">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/appengine?tab=doc#EngineSplitTrafficSplitArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/appengine?tab=doc#EngineSplitTrafficSplitOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Allocations</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Shard<wbr>By</span>
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
        <span>Allocations</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Shard<wbr>By</span>
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
        <span>allocations</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>shard<wbr>By</span>
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
        <span>allocations</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>shard<wbr>By</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}







