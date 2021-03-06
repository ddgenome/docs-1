
---
title: "VirtualMachine"
block_external_search_index: true
---

Manages a Microsoft SQL Virtual Machine

> This content is derived from https://github.com/terraform-providers/terraform-provider-azurerm/blob/master/website/docs/r/mssql_virtual_machine.html.markdown.



## Create a VirtualMachine Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/mssql/#VirtualMachine">VirtualMachine</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/mssql/#VirtualMachineArgs">VirtualMachineArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">VirtualMachine</span><span class="p">(resource_name, opts=None, </span>auto_patching=None<span class="p">, </span>key_vault_credential=None<span class="p">, </span>r_services_enabled=None<span class="p">, </span>sql_connectivity_port=None<span class="p">, </span>sql_connectivity_type=None<span class="p">, </span>sql_connectivity_update_password=None<span class="p">, </span>sql_connectivity_update_username=None<span class="p">, </span>sql_license_type=None<span class="p">, </span>tags=None<span class="p">, </span>virtual_machine_id=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewVirtualMachine<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/mssql?tab=doc#VirtualMachineArgs">VirtualMachineArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/mssql?tab=doc#VirtualMachine">VirtualMachine</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Mssql.VirtualMachine.html">VirtualMachine</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.MSSql.Inputs.VirtualMachineArgs.html">VirtualMachineArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Auto<wbr>Patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">Pulumi.<wbr>Azure.<wbr>MSSql.<wbr>Inputs.<wbr>Virtual<wbr>Machine<wbr>Auto<wbr>Patching<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Key<wbr>Vault<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">Pulumi.<wbr>Azure.<wbr>MSSql.<wbr>Inputs.<wbr>Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>RServices<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Port</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Sql<wbr>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Virtual<wbr>Machine<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Auto<wbr>Patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">*Virtual<wbr>Machine<wbr>Auto<wbr>Patching</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Key<wbr>Vault<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">*Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>RServices<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Port</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Sql<wbr>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Virtual<wbr>Machine<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>auto<wbr>Patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">Virtual<wbr>Machine<wbr>Auto<wbr>Patching?</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>key<wbr>Vault<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential?</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>r<wbr>Services<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql<wbr>Connectivity<wbr>Port</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql<wbr>Connectivity<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql<wbr>Connectivity<wbr>Update<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql<wbr>Connectivity<wbr>Update<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>sql<wbr>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>virtual<wbr>Machine<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>auto_<wbr>patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">Dict[Virtual<wbr>Machine<wbr>Auto<wbr>Patching]</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>key_<wbr>vault_<wbr>credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">Dict[Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential]</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>r_<wbr>services_<wbr>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql_<wbr>connectivity_<wbr>port</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql_<wbr>connectivity_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql_<wbr>connectivity_<wbr>update_<wbr>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql_<wbr>connectivity_<wbr>update_<wbr>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>sql_<wbr>license_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>virtual_<wbr>machine_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## VirtualMachine Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Auto<wbr>Patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">Pulumi.<wbr>Azure.<wbr>MSSql.<wbr>Outputs.<wbr>Virtual<wbr>Machine<wbr>Auto<wbr>Patching?</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Key<wbr>Vault<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">Pulumi.<wbr>Azure.<wbr>MSSql.<wbr>Outputs.<wbr>Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential?</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>RServices<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sql<wbr>Connectivity<wbr>Port</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sql<wbr>Connectivity<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sql<wbr>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Virtual<wbr>Machine<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Auto<wbr>Patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">*Virtual<wbr>Machine<wbr>Auto<wbr>Patching</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Key<wbr>Vault<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">*Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>RServices<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sql<wbr>Connectivity<wbr>Port</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sql<wbr>Connectivity<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sql<wbr>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Virtual<wbr>Machine<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>auto<wbr>Patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">Virtual<wbr>Machine<wbr>Auto<wbr>Patching?</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>key<wbr>Vault<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential?</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>r<wbr>Services<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sql<wbr>Connectivity<wbr>Port</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sql<wbr>Connectivity<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sql<wbr>Connectivity<wbr>Update<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sql<wbr>Connectivity<wbr>Update<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sql<wbr>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>virtual<wbr>Machine<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>auto_<wbr>patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">Dict[Virtual<wbr>Machine<wbr>Auto<wbr>Patching]</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>key_<wbr>vault_<wbr>credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">Dict[Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential]</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>r_<wbr>services_<wbr>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sql_<wbr>connectivity_<wbr>port</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sql_<wbr>connectivity_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sql_<wbr>connectivity_<wbr>update_<wbr>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sql_<wbr>connectivity_<wbr>update_<wbr>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sql_<wbr>license_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>virtual_<wbr>machine_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing VirtualMachine Resource

Get an existing VirtualMachine resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/mssql/#VirtualMachineState">VirtualMachineState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/mssql/#VirtualMachine">VirtualMachine</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>auto_patching=None<span class="p">, </span>key_vault_credential=None<span class="p">, </span>r_services_enabled=None<span class="p">, </span>sql_connectivity_port=None<span class="p">, </span>sql_connectivity_type=None<span class="p">, </span>sql_connectivity_update_password=None<span class="p">, </span>sql_connectivity_update_username=None<span class="p">, </span>sql_license_type=None<span class="p">, </span>tags=None<span class="p">, </span>virtual_machine_id=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetVirtualMachine<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/mssql?tab=doc#VirtualMachineState">VirtualMachineState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/mssql?tab=doc#VirtualMachine">VirtualMachine</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Mssql.VirtualMachine.html">VirtualMachine</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Mssql.VirtualMachineState.html">VirtualMachineState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Auto<wbr>Patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">Pulumi.<wbr>Azure.<wbr>MSSql.<wbr>Inputs.<wbr>Virtual<wbr>Machine<wbr>Auto<wbr>Patching<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Key<wbr>Vault<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">Pulumi.<wbr>Azure.<wbr>MSSql.<wbr>Inputs.<wbr>Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>RServices<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Port</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Virtual<wbr>Machine<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Auto<wbr>Patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">*Virtual<wbr>Machine<wbr>Auto<wbr>Patching</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Key<wbr>Vault<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">*Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>RServices<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Port</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>Connectivity<wbr>Update<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sql<wbr>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Virtual<wbr>Machine<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>auto<wbr>Patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">Virtual<wbr>Machine<wbr>Auto<wbr>Patching?</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>key<wbr>Vault<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential?</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>r<wbr>Services<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql<wbr>Connectivity<wbr>Port</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql<wbr>Connectivity<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql<wbr>Connectivity<wbr>Update<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql<wbr>Connectivity<wbr>Update<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql<wbr>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>virtual<wbr>Machine<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>auto_<wbr>patching</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineautopatching">Dict[Virtual<wbr>Machine<wbr>Auto<wbr>Patching]</a></span>
    </dt>
    <dd>{{% md %}}An `auto_patching` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>key_<wbr>vault_<wbr>credential</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinekeyvaultcredential">Dict[Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential]</a></span>
    </dt>
    <dd>{{% md %}}(Optional) An `key_vault_credential` block as defined below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>r_<wbr>services_<wbr>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should R Services be enabled?
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql_<wbr>connectivity_<wbr>port</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The SQL Server port. Defaults to `1433`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql_<wbr>connectivity_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The connectivity type used for this SQL Server. Defaults to `PRIVATE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql_<wbr>connectivity_<wbr>update_<wbr>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login password.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql_<wbr>connectivity_<wbr>update_<wbr>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The SQL Server sysadmin login to create.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sql_<wbr>license_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The SQL Server license type. Possible values are `AHUB` (Azure Hybrid Benefit) and `PAYG` (Pay-As-You-Go). Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>virtual_<wbr>machine_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Virtual<wbr>Machine<wbr>Auto<wbr>Patching</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineAutoPatching">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineAutoPatching">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/mssql?tab=doc#VirtualMachineAutoPatchingArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/mssql?tab=doc#VirtualMachineAutoPatchingOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Day<wbr>Of<wbr>Week</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The day of week to apply the patch on.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Maintenance<wbr>Window<wbr>Duration<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The size of the Maintenance Window in minutes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Maintenance<wbr>Window<wbr>Starting<wbr>Hour</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The Hour, in the Virtual Machine Time-Zone when the patching maintenance window should begin.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Day<wbr>Of<wbr>Week</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The day of week to apply the patch on.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Maintenance<wbr>Window<wbr>Duration<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The size of the Maintenance Window in minutes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Maintenance<wbr>Window<wbr>Starting<wbr>Hour</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The Hour, in the Virtual Machine Time-Zone when the patching maintenance window should begin.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>day<wbr>Of<wbr>Week</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The day of week to apply the patch on.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>maintenance<wbr>Window<wbr>Duration<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The size of the Maintenance Window in minutes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>maintenance<wbr>Window<wbr>Starting<wbr>Hour</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The Hour, in the Virtual Machine Time-Zone when the patching maintenance window should begin.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>day<wbr>Of<wbr>Week</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The day of week to apply the patch on.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>maintenance<wbr>Window<wbr>Duration<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The size of the Maintenance Window in minutes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>maintenance<wbr>Window<wbr>Starting<wbr>Hour</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The Hour, in the Virtual Machine Time-Zone when the patching maintenance window should begin.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Key<wbr>Vault<wbr>Credential</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineKeyVaultCredential">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineKeyVaultCredential">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/mssql?tab=doc#VirtualMachineKeyVaultCredentialArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/mssql?tab=doc#VirtualMachineKeyVaultCredentialOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key<wbr>Vault<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The azure Key Vault url. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The credential name.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Service<wbr>Principal<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The service principal name to access key vault. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Service<wbr>Principal<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The service principal name secret to access key vault. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key<wbr>Vault<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The azure Key Vault url. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The credential name.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Service<wbr>Principal<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The service principal name to access key vault. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Service<wbr>Principal<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The service principal name secret to access key vault. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>key<wbr>Vault<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The azure Key Vault url. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The credential name.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>service<wbr>Principal<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The service principal name to access key vault. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>service<wbr>Principal<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The service principal name secret to access key vault. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>key<wbr>Vault<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The azure Key Vault url. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The credential name.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>service<wbr>Principal<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The service principal name to access key vault. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>service<wbr>Principal<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The service principal name secret to access key vault. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







