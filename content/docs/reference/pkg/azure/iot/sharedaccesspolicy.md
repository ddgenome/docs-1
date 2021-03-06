
---
title: "SharedAccessPolicy"
block_external_search_index: true
---

Manages an IotHub Shared Access Policy

> This content is derived from https://github.com/terraform-providers/terraform-provider-azurerm/blob/master/website/docs/r/iothub_shared_access_policy.html.markdown.



## Create a SharedAccessPolicy Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/iot/#SharedAccessPolicy">SharedAccessPolicy</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/iot/#SharedAccessPolicyArgs">SharedAccessPolicyArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">SharedAccessPolicy</span><span class="p">(resource_name, opts=None, </span>device_connect=None<span class="p">, </span>iothub_name=None<span class="p">, </span>name=None<span class="p">, </span>registry_read=None<span class="p">, </span>registry_write=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>service_connect=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewSharedAccessPolicy<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/iot?tab=doc#SharedAccessPolicyArgs">SharedAccessPolicyArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/iot?tab=doc#SharedAccessPolicy">SharedAccessPolicy</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Iot.SharedAccessPolicy.html">SharedAccessPolicy</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Iot.Inputs.SharedAccessPolicyArgs.html">SharedAccessPolicyArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Device<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Iothub<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Registry<wbr>Read</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Registry<wbr>Write</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Service<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Device<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Iothub<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Registry<wbr>Read</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Registry<wbr>Write</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Service<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>device<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>iothub<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>registry<wbr>Read</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>registry<wbr>Write</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>service<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>device_<wbr>connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>iothub_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>registry_<wbr>read</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>registry_<wbr>write</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>service_<wbr>connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## SharedAccessPolicy Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Device<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Iothub<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Primary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The primary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Primary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The primary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Registry<wbr>Read</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Registry<wbr>Write</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Secondary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The secondary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Secondary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The secondary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Service<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Device<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Iothub<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Primary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The primary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Primary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The primary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Registry<wbr>Read</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Registry<wbr>Write</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Secondary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The secondary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Secondary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The secondary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Service<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>device<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>iothub<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>primary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The primary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>primary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The primary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>registry<wbr>Read</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>registry<wbr>Write</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>secondary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The secondary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>secondary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The secondary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>service<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>device_<wbr>connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>iothub_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>primary_<wbr>connection_<wbr>string</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The primary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>primary_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The primary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>registry_<wbr>read</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>registry_<wbr>write</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>secondary_<wbr>connection_<wbr>string</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The secondary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>secondary_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The secondary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>service_<wbr>connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing SharedAccessPolicy Resource

Get an existing SharedAccessPolicy resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/iot/#SharedAccessPolicyState">SharedAccessPolicyState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/iot/#SharedAccessPolicy">SharedAccessPolicy</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>device_connect=None<span class="p">, </span>iothub_name=None<span class="p">, </span>name=None<span class="p">, </span>primary_connection_string=None<span class="p">, </span>primary_key=None<span class="p">, </span>registry_read=None<span class="p">, </span>registry_write=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>secondary_connection_string=None<span class="p">, </span>secondary_key=None<span class="p">, </span>service_connect=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetSharedAccessPolicy<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/iot?tab=doc#SharedAccessPolicyState">SharedAccessPolicyState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/iot?tab=doc#SharedAccessPolicy">SharedAccessPolicy</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Iot.SharedAccessPolicy.html">SharedAccessPolicy</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Iot.SharedAccessPolicyState.html">SharedAccessPolicyState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Device<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iothub<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Primary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The primary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Primary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The primary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Registry<wbr>Read</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Registry<wbr>Write</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Secondary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The secondary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Secondary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The secondary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Service<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Device<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iothub<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Primary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The primary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Primary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The primary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Registry<wbr>Read</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Registry<wbr>Write</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Secondary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The secondary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Secondary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The secondary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Service<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>device<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iothub<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>primary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The primary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>primary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The primary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>registry<wbr>Read</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>registry<wbr>Write</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>secondary<wbr>Connection<wbr>String</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The secondary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>secondary<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The secondary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>service<wbr>Connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>device_<wbr>connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `DeviceConnect` permission to this Shared Access Account. It allows sending and receiving on the device-side endpoints.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iothub_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the IoTHub to which this Shared Access Policy belongs. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the IotHub Shared Access Policy resource. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>primary_<wbr>connection_<wbr>string</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The primary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>primary_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The primary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>registry_<wbr>read</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryRead` permission to this Shared Access Account. It allows read access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>registry_<wbr>write</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `RegistryWrite` permission to this Shared Access Account. It allows write access to the identity registry.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group under which the IotHub Shared Access Policy resource has to be created. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>secondary_<wbr>connection_<wbr>string</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The secondary connection string of the Shared Access Policy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>secondary_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The secondary key used to create the authentication token.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>service_<wbr>connect</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Adds `ServiceConnect` permission to this Shared Access Account. It allows sending and receiving on the cloud-side endpoints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}









