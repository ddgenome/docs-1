
---
title: "Definition"
block_external_search_index: true
---

Manages a policy rule definition on a management group or your provider subscription.

Policy definitions do not take effect until they are assigned to a scope using a Policy Assignment.

## Example Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure from "@pulumi/azure";

const policy = new azure.policy.Definition("policy", {
    displayName: "acceptance test policy definition",
    metadata: `    {
    "category": "General"
    }
  
`,
    mode: "Indexed",
    parameters: `	{
    "allowedLocations": {
      "type": "Array",
      "metadata": {
        "description": "The list of allowed locations for resources.",
        "displayName": "Allowed locations",
        "strongType": "location"
      }
    }
  }
`,
    policyRule: `	{
    "if": {
      "not": {
        "field": "location",
        "in": "[parameters('allowedLocations')]"
      }
    },
    "then": {
      "effect": "audit"
    }
  }
`,
    policyType: "Custom",
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-azurerm/blob/master/website/docs/r/policy_definition.html.markdown.



## Create a Definition Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/policy/#Definition">Definition</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/policy/#DefinitionArgs">DefinitionArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">Definition</span><span class="p">(resource_name, opts=None, </span>description=None<span class="p">, </span>display_name=None<span class="p">, </span>management_group_id=None<span class="p">, </span>metadata=None<span class="p">, </span>mode=None<span class="p">, </span>name=None<span class="p">, </span>parameters=None<span class="p">, </span>policy_rule=None<span class="p">, </span>policy_type=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewDefinition<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/policy?tab=doc#DefinitionArgs">DefinitionArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/policy?tab=doc#Definition">Definition</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Policy.Definition.html">Definition</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Policy.Inputs.DefinitionArgs.html">DefinitionArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Management<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Policy<wbr>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Policy<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
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
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Management<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Policy<wbr>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Policy<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
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
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>management<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>policy<wbr>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>policy<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
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
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>display_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>management_<wbr>group_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>policy_<wbr>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>policy_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## Definition Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Management<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Policy<wbr>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Policy<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Management<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Policy<wbr>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Policy<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>management<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>policy<wbr>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>policy<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>display_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>management_<wbr>group_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>policy_<wbr>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>policy_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing Definition Resource

Get an existing Definition resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/policy/#DefinitionState">DefinitionState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/policy/#Definition">Definition</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>description=None<span class="p">, </span>display_name=None<span class="p">, </span>management_group_id=None<span class="p">, </span>metadata=None<span class="p">, </span>mode=None<span class="p">, </span>name=None<span class="p">, </span>parameters=None<span class="p">, </span>policy_rule=None<span class="p">, </span>policy_type=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetDefinition<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/policy?tab=doc#DefinitionState">DefinitionState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/policy?tab=doc#Definition">Definition</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Policy.Definition.html">Definition</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Policy.DefinitionState.html">DefinitionState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Management<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Policy<wbr>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Policy<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
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
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Management<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Policy<wbr>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Policy<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
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
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>management<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>policy<wbr>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>policy<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
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
    <dd>{{% md %}}The description of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>display_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The display name of the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>management_<wbr>group_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Management Group where this policy should be defined. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>metadata</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The metadata for the policy definition. This
is a json object representing additional metadata that should be stored
with the policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The policy mode that allows you to specify which resource
types will be evaluated.  The value can be "All", "Indexed" or
"NotSpecified". Changing this resource forces a new resource to be
created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the policy definition. Changing this forces a
new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameters for the policy definition. This field
is a json object that allows you to parameterize your policy definition.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>policy_<wbr>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The policy rule for the policy definition. This
is a json object representing the rule that contains an if and
a then block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>policy_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The policy type.  The value can be "BuiltIn", "Custom"
or "NotSpecified". Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}









