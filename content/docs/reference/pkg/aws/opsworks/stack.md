
---
title: "Stack"
block_external_search_index: true
---

Provides an OpsWorks stack resource.

## Example Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const main = new aws.opsworks.Stack("main", {
    customJson: `{
 "foobar": {
    "version": "1.0.0"
  }
}
`,
    defaultInstanceProfileArn: aws_iam_instance_profile_opsworks.arn,
    region: "us-west-1",
    serviceRoleArn: aws_iam_role_opsworks.arn,
    tags: {
        Name: "foobar-stack",
    },
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/opsworks_stack.html.markdown.



## Create a Stack Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/opsworks/#Stack">Stack</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/opsworks/#StackArgs">StackArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">Stack</span><span class="p">(resource_name, opts=None, </span>agent_version=None<span class="p">, </span>berkshelf_version=None<span class="p">, </span>color=None<span class="p">, </span>configuration_manager_name=None<span class="p">, </span>configuration_manager_version=None<span class="p">, </span>custom_cookbooks_sources=None<span class="p">, </span>custom_json=None<span class="p">, </span>default_availability_zone=None<span class="p">, </span>default_instance_profile_arn=None<span class="p">, </span>default_os=None<span class="p">, </span>default_root_device_type=None<span class="p">, </span>default_ssh_key_name=None<span class="p">, </span>default_subnet_id=None<span class="p">, </span>hostname_theme=None<span class="p">, </span>manage_berkshelf=None<span class="p">, </span>name=None<span class="p">, </span>region=None<span class="p">, </span>service_role_arn=None<span class="p">, </span>tags=None<span class="p">, </span>use_custom_cookbooks=None<span class="p">, </span>use_opsworks_security_groups=None<span class="p">, </span>vpc_id=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewStack<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/opsworks?tab=doc#StackArgs">StackArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/opsworks?tab=doc#Stack">Stack</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Opsworks.Stack.html">Stack</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.OpsWorks.Inputs.StackArgs.html">StackArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Agent<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Berkshelf<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Color</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration<wbr>Manager<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration<wbr>Manager<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Cookbooks<wbr>Sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">List&lt;Pulumi.<wbr>Aws.<wbr>Ops<wbr>Works.<wbr>Inputs.<wbr>Stack<wbr>Custom<wbr>Cookbooks<wbr>Source<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Json</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Default<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Os</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Ssh<wbr>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hostname<wbr>Theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Manage<wbr>Berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Service<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Custom<wbr>Cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Opsworks<wbr>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpc<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Agent<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Berkshelf<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Color</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration<wbr>Manager<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration<wbr>Manager<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Cookbooks<wbr>Sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">[]Stack<wbr>Custom<wbr>Cookbooks<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Json</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Default<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Os</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Ssh<wbr>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hostname<wbr>Theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Manage<wbr>Berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Service<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Custom<wbr>Cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Opsworks<wbr>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpc<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>agent<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>berkshelf<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>color</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration<wbr>Manager<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration<wbr>Manager<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>custom<wbr>Cookbooks<wbr>Sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">Stack<wbr>Custom<wbr>Cookbooks<wbr>Source[]?</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>custom<wbr>Json</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>default<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Os</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Ssh<wbr>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hostname<wbr>Theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>manage<wbr>Berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>service<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use<wbr>Custom<wbr>Cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use<wbr>Opsworks<wbr>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpc<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>agent_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>berkshelf_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>color</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration_<wbr>manager_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration_<wbr>manager_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>custom_<wbr>cookbooks_<wbr>sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">List[Stack<wbr>Custom<wbr>Cookbooks<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>custom_<wbr>json</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>availability_<wbr>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>default_<wbr>instance_<wbr>profile_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>os</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>root_<wbr>device_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>ssh_<wbr>key_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>subnet_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hostname_<wbr>theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>manage_<wbr>berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>service_<wbr>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use_<wbr>custom_<wbr>cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use_<wbr>opsworks_<wbr>security_<wbr>groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpc_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## Stack Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Agent<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Berkshelf<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Color</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Configuration<wbr>Manager<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Configuration<wbr>Manager<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Custom<wbr>Cookbooks<wbr>Sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">List&lt;Pulumi.<wbr>Aws.<wbr>Ops<wbr>Works.<wbr>Outputs.<wbr>Stack<wbr>Custom<wbr>Cookbooks<wbr>Source&gt;</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Custom<wbr>Json</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Os</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Ssh<wbr>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hostname<wbr>Theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Manage<wbr>Berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Service<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Stack<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Use<wbr>Custom<wbr>Cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Use<wbr>Opsworks<wbr>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Vpc<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Agent<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Berkshelf<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Color</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Configuration<wbr>Manager<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Configuration<wbr>Manager<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Custom<wbr>Cookbooks<wbr>Sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">[]Stack<wbr>Custom<wbr>Cookbooks<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Custom<wbr>Json</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Os</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Ssh<wbr>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hostname<wbr>Theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Manage<wbr>Berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Service<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Stack<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Use<wbr>Custom<wbr>Cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Use<wbr>Opsworks<wbr>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Vpc<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>agent<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>berkshelf<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>color</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>configuration<wbr>Manager<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>configuration<wbr>Manager<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>custom<wbr>Cookbooks<wbr>Sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">Stack<wbr>Custom<wbr>Cookbooks<wbr>Source[]</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>custom<wbr>Json</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default<wbr>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default<wbr>Os</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default<wbr>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default<wbr>Ssh<wbr>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default<wbr>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hostname<wbr>Theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>manage<wbr>Berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>service<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>stack<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>use<wbr>Custom<wbr>Cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>use<wbr>Opsworks<wbr>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>vpc<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>agent_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>berkshelf_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>color</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>configuration_<wbr>manager_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>configuration_<wbr>manager_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>custom_<wbr>cookbooks_<wbr>sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">List[Stack<wbr>Custom<wbr>Cookbooks<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>custom_<wbr>json</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default_<wbr>availability_<wbr>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default_<wbr>instance_<wbr>profile_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default_<wbr>os</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default_<wbr>root_<wbr>device_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default_<wbr>ssh_<wbr>key_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default_<wbr>subnet_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hostname_<wbr>theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>manage_<wbr>berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>service_<wbr>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>stack_<wbr>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>use_<wbr>custom_<wbr>cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>use_<wbr>opsworks_<wbr>security_<wbr>groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>vpc_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing Stack Resource

Get an existing Stack resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/opsworks/#StackState">StackState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/opsworks/#Stack">Stack</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>agent_version=None<span class="p">, </span>arn=None<span class="p">, </span>berkshelf_version=None<span class="p">, </span>color=None<span class="p">, </span>configuration_manager_name=None<span class="p">, </span>configuration_manager_version=None<span class="p">, </span>custom_cookbooks_sources=None<span class="p">, </span>custom_json=None<span class="p">, </span>default_availability_zone=None<span class="p">, </span>default_instance_profile_arn=None<span class="p">, </span>default_os=None<span class="p">, </span>default_root_device_type=None<span class="p">, </span>default_ssh_key_name=None<span class="p">, </span>default_subnet_id=None<span class="p">, </span>hostname_theme=None<span class="p">, </span>manage_berkshelf=None<span class="p">, </span>name=None<span class="p">, </span>region=None<span class="p">, </span>service_role_arn=None<span class="p">, </span>stack_endpoint=None<span class="p">, </span>tags=None<span class="p">, </span>use_custom_cookbooks=None<span class="p">, </span>use_opsworks_security_groups=None<span class="p">, </span>vpc_id=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetStack<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/opsworks?tab=doc#StackState">StackState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/opsworks?tab=doc#Stack">Stack</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Opsworks.Stack.html">Stack</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Opsworks.StackState.html">StackState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Agent<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Berkshelf<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Color</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration<wbr>Manager<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration<wbr>Manager<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Cookbooks<wbr>Sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">List&lt;Pulumi.<wbr>Aws.<wbr>Ops<wbr>Works.<wbr>Inputs.<wbr>Stack<wbr>Custom<wbr>Cookbooks<wbr>Source<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Json</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Os</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Ssh<wbr>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hostname<wbr>Theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Manage<wbr>Berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Service<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Stack<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Custom<wbr>Cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Opsworks<wbr>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpc<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Agent<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Berkshelf<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Color</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration<wbr>Manager<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration<wbr>Manager<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Cookbooks<wbr>Sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">[]Stack<wbr>Custom<wbr>Cookbooks<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Json</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Os</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Ssh<wbr>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hostname<wbr>Theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Manage<wbr>Berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Service<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Stack<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Custom<wbr>Cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Use<wbr>Opsworks<wbr>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpc<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>agent<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>berkshelf<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>color</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration<wbr>Manager<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration<wbr>Manager<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>custom<wbr>Cookbooks<wbr>Sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">Stack<wbr>Custom<wbr>Cookbooks<wbr>Source[]?</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>custom<wbr>Json</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Os</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Ssh<wbr>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hostname<wbr>Theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>manage<wbr>Berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>service<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>stack<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use<wbr>Custom<wbr>Cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use<wbr>Opsworks<wbr>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpc<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>agent_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}If set to `"LATEST"`, OpsWorks will automatically install the latest version.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>berkshelf_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}If `manage_berkshelf` is enabled, the version of Berkshelf to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>color</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Color to paint next to the stack's resources in the OpsWorks console.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration_<wbr>manager_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the configuration manager to use. Defaults to "Chef".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration_<wbr>manager_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Version of the configuration manager to use. Defaults to "11.4".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>custom_<wbr>cookbooks_<wbr>sources</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#stackcustomcookbookssource">List[Stack<wbr>Custom<wbr>Cookbooks<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}When `use_custom_cookbooks` is set, provide this sub-object as
described below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>custom_<wbr>json</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Custom JSON attributes to apply to the entire stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>availability_<wbr>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the availability zone where instances will be created
by default. This is required unless you set `vpc_id`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>instance_<wbr>profile_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM Instance Profile that created instances
will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>os</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of OS that will be installed on instances by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>root_<wbr>device_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the type of root device instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>ssh_<wbr>key_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the SSH keypair that instances will have by default.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>subnet_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Id of the subnet in which instances will be created by default. Mandatory
if `vpc_id` is set, and forbidden if it isn't.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hostname_<wbr>theme</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Keyword representing the naming scheme that will be used for instance hostnames
within this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>manage_<wbr>berkshelf</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether Opsworks will run Berkshelf for this stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the stack.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the region where the stack will exist.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>service_<wbr>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that the OpsWorks service will act as.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>stack_<wbr>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use_<wbr>custom_<wbr>cookbooks</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the custom cookbook settings are
enabled.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>use_<wbr>opsworks_<wbr>security_<wbr>groups</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean value controlling whether the standard OpsWorks
security groups apply to created instances.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpc_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The id of the VPC that this stack belongs to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Stack<wbr>Custom<wbr>Cookbooks<wbr>Source</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#StackCustomCookbooksSource">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#StackCustomCookbooksSource">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/opsworks?tab=doc#StackCustomCookbooksSourceArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/opsworks?tab=doc#StackCustomCookbooksSourceOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Password to use when authenticating to the source. The provider cannot perform drift detection of this configuration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Revision</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}For sources that are version-aware, the revision to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ssh<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SSH key to use when authenticating to the source. The provider cannot perform drift detection of this configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of source to use. For example, "archive".
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URL where the cookbooks resource can be found.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Username to use when authenticating to the source.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Password to use when authenticating to the source. The provider cannot perform drift detection of this configuration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Revision</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}For sources that are version-aware, the revision to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ssh<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SSH key to use when authenticating to the source. The provider cannot perform drift detection of this configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of source to use. For example, "archive".
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URL where the cookbooks resource can be found.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Username to use when authenticating to the source.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Password to use when authenticating to the source. The provider cannot perform drift detection of this configuration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>revision</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}For sources that are version-aware, the revision to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ssh<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SSH key to use when authenticating to the source. The provider cannot perform drift detection of this configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of source to use. For example, "archive".
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URL where the cookbooks resource can be found.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Username to use when authenticating to the source.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Password to use when authenticating to the source. The provider cannot perform drift detection of this configuration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>revision</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}For sources that are version-aware, the revision to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ssh<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SSH key to use when authenticating to the source. The provider cannot perform drift detection of this configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of source to use. For example, "archive".
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>url</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The URL where the cookbooks resource can be found.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Username to use when authenticating to the source.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







