
---
title: "GetService"
block_external_search_index: true
---

Use this data source to access information about an existing Database Migration Service.


## Example Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure from "@pulumi/azure";

const example = azure.databasemigration.getService({
    name: "example-dms",
    resourceGroupName: "example-rg",
});

export const azurermDmsId = example.id;
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-azurerm/blob/master/website/docs/d/database_migration_service.html.markdown.





## Using GetService

{{< chooser language "javascript,typescript,python,go,csharp" / >}}


{{% choosable language typescript %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">function </span>getService<span class="p">(</span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/databasemigration/#GetServiceArgs">GetServiceArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#InvokeOptions">pulumi.InvokeOptions</a></span><span class="p">): Promise&lt;<span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/databasemigration/#GetServiceResult">GetServiceResult</a></span>></span></code></pre></div>
{{% /choosable %}}


{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">function </span> get_service(</span>name=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>opts=None<span class="p">)</span></code></pre></div>
{{% /choosable %}}


{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>LookupService<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/databasemigration?tab=doc#LookupServiceArgs">LookupServiceArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#InvokeOption">pulumi.InvokeOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/databasemigration?tab=doc#LookupServiceResult">LookupServiceResult</a></span>, error)</span></code></pre></div>
{{% /choosable %}}


{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static class </span><span class="nx">GetService </span><span class="p">{</span><span class="k">
    public static </span>Task&lt;<span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Databasemigration.GetServiceResult.html">GetServiceResult</a></span>> <span class="p">InvokeAsync(</span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.DatabaseMigration.Inputs.GetServiceArgs.html">GetServiceArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.InvokeOptions.html">Pulumi.InvokeOptions</a></span>? <span class="nx">opts = null<span class="p">)</span><span class="p">
}</span></code></pre></div>
{{% /choosable %}}



The following arguments are supported:



{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specify the name of the database migration service.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Name of the Resource Group within which the database migration service exists
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
    <dd>{{% md %}}Specify the name of the database migration service.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Name of the Resource Group within which the database migration service exists
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
    <dd>{{% md %}}Specify the name of the database migration service.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Name of the Resource Group within which the database migration service exists
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
    <dd>{{% md %}}Specify the name of the database migration service.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Name of the Resource Group within which the database migration service exists
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## GetService Result

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}id is the provider-assigned unique ID for this managed resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Azure location where the resource exists.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sku<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The sku name of database migration service.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the virtual subnet resource to which the database migration service exists.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string></span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assigned to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}id is the provider-assigned unique ID for this managed resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Azure location where the resource exists.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sku<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The sku name of database migration service.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the virtual subnet resource to which the database migration service exists.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assigned to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}id is the provider-assigned unique ID for this managed resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Azure location where the resource exists.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sku<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The sku name of database migration service.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the virtual subnet resource to which the database migration service exists.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assigned to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}id is the provider-assigned unique ID for this managed resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Azure location where the resource exists.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sku_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The sku name of database migration service.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>subnet_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the virtual subnet resource to which the database migration service exists.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assigned to the resource.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







