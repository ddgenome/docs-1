
---
title: "ConfigurationAggregator"
block_external_search_index: true
---

Manages an AWS Config Configuration Aggregator

## Example Usage

### Account Based Aggregation

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const account = new aws.cfg.ConfigurationAggregator("account", {
    accountAggregationSource: {
        accountIds: ["123456789012"],
        regions: ["us-west-2"],
    },
});
```

### Organization Based Aggregation

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const organizationRole = new aws.iam.Role("organization", {
    assumeRolePolicy: `{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "",
      "Effect": "Allow",
      "Principal": {
        "Service": "config.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
`,
});
const organizationRolePolicyAttachment = new aws.iam.RolePolicyAttachment("organization", {
    policyArn: "arn:aws:iam::aws:policy/service-role/AWSConfigRoleForOrganizations",
    role: organizationRole.name,
});
const organizationConfigurationAggregator = new aws.cfg.ConfigurationAggregator("organization", {
    organizationAggregationSource: {
        allRegions: true,
        roleArn: organizationRole.arn,
    },
}, {dependsOn: [organizationRolePolicyAttachment]});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/config_configuration_aggregator.html.markdown.



## Create a ConfigurationAggregator Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cfg/#ConfigurationAggregator">ConfigurationAggregator</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cfg/#ConfigurationAggregatorArgs">ConfigurationAggregatorArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">ConfigurationAggregator</span><span class="p">(resource_name, opts=None, </span>account_aggregation_source=None<span class="p">, </span>name=None<span class="p">, </span>organization_aggregation_source=None<span class="p">, </span>tags=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewConfigurationAggregator<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cfg?tab=doc#ConfigurationAggregatorArgs">ConfigurationAggregatorArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cfg?tab=doc#ConfigurationAggregator">ConfigurationAggregator</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cfg.ConfigurationAggregator.html">ConfigurationAggregator</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cfg.Inputs.ConfigurationAggregatorArgs.html">ConfigurationAggregatorArgs</a></span>? <span class="nx">args = null<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Account<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Organization<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Account<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">*Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Organization<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">*Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>account<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>organization<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>account_<wbr>aggregation_<wbr>source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">Dict[Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>organization_<wbr>aggregation_<wbr>source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">Dict[Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## ConfigurationAggregator Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Account<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the aggregator
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Organization<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Account<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">*Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the aggregator
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Organization<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">*Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>account<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the aggregator
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>organization<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>account_<wbr>aggregation_<wbr>source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">Dict[Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the aggregator
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>organization_<wbr>aggregation_<wbr>source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">Dict[Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing ConfigurationAggregator Resource

Get an existing ConfigurationAggregator resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cfg/#ConfigurationAggregatorState">ConfigurationAggregatorState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cfg/#ConfigurationAggregator">ConfigurationAggregator</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>account_aggregation_source=None<span class="p">, </span>arn=None<span class="p">, </span>name=None<span class="p">, </span>organization_aggregation_source=None<span class="p">, </span>tags=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetConfigurationAggregator<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cfg?tab=doc#ConfigurationAggregatorState">ConfigurationAggregatorState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cfg?tab=doc#ConfigurationAggregator">ConfigurationAggregator</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cfg.ConfigurationAggregator.html">ConfigurationAggregator</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cfg.ConfigurationAggregatorState.html">ConfigurationAggregatorState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Account<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of the aggregator
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Organization<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Account<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">*Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of the aggregator
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Organization<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">*Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>account<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of the aggregator
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>organization<wbr>Aggregation<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>account_<wbr>aggregation_<wbr>source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatoraccountaggregationsource">Dict[Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}The account(s) to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the aggregator
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the configuration aggregator.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>organization_<wbr>aggregation_<wbr>source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#configurationaggregatororganizationaggregationsource">Dict[Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}The organization to aggregate config data from as documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Configuration<wbr>Aggregator<wbr>Account<wbr>Aggregation<wbr>Source</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#ConfigurationAggregatorAccountAggregationSource">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#ConfigurationAggregatorAccountAggregationSource">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cfg?tab=doc#ConfigurationAggregatorAccountAggregationSourceArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cfg?tab=doc#ConfigurationAggregatorAccountAggregationSourceOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Account<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}List of 12-digit account IDs of the account(s) being aggregated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>All<wbr>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If true, aggregate existing AWS Config regions and future regions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of source regions being aggregated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Account<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of 12-digit account IDs of the account(s) being aggregated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>All<wbr>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If true, aggregate existing AWS Config regions and future regions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of source regions being aggregated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>account<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}List of 12-digit account IDs of the account(s) being aggregated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>all<wbr>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If true, aggregate existing AWS Config regions and future regions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of source regions being aggregated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>account_<wbr>ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of 12-digit account IDs of the account(s) being aggregated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>all<wbr>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, aggregate existing AWS Config regions and future regions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of source regions being aggregated.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Configuration<wbr>Aggregator<wbr>Organization<wbr>Aggregation<wbr>Source</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#ConfigurationAggregatorOrganizationAggregationSource">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#ConfigurationAggregatorOrganizationAggregationSource">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cfg?tab=doc#ConfigurationAggregatorOrganizationAggregationSourceArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cfg?tab=doc#ConfigurationAggregatorOrganizationAggregationSourceOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>All<wbr>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If true, aggregate existing AWS Config regions and future regions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of source regions being aggregated.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}ARN of the IAM role used to retrieve AWS Organization details associated with the aggregator account.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>All<wbr>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If true, aggregate existing AWS Config regions and future regions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of source regions being aggregated.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}ARN of the IAM role used to retrieve AWS Organization details associated with the aggregator account.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>all<wbr>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If true, aggregate existing AWS Config regions and future regions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of source regions being aggregated.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}ARN of the IAM role used to retrieve AWS Organization details associated with the aggregator account.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>all<wbr>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, aggregate existing AWS Config regions and future regions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>regions</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of source regions being aggregated.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}ARN of the IAM role used to retrieve AWS Organization details associated with the aggregator account.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







