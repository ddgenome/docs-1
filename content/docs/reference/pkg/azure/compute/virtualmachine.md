
---
title: "VirtualMachine"
block_external_search_index: true
---

Manages a Virtual Machine.

## Disclaimers

> **Note:** The `azure.compute.VirtualMachine` resource has been superseded by the `azure.compute.LinuxVirtualMachine` and `azure.compute.WindowsVirtualMachine` resources. The existing `azure.compute.VirtualMachine` resource will continue to be available throughout the 2.x releases however is in a feature-frozen state to maintain compatibility - new functionality will instead be added to the `azure.compute.LinuxVirtualMachine` and `azure.compute.WindowsVirtualMachine` resources.

> **Note:** Data Disks can be attached either directly on the `azure.compute.VirtualMachine` resource, or using the `azure.compute.DataDiskAttachment` resource - but the two cannot be used together. If both are used against the same Virtual Machine, spurious changes will occur.

> This content is derived from https://github.com/terraform-providers/terraform-provider-azurerm/blob/master/website/docs/r/virtual_machine.html.markdown.



## Create a VirtualMachine Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/compute/#VirtualMachine">VirtualMachine</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/compute/#VirtualMachineArgs">VirtualMachineArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">VirtualMachine</span><span class="p">(resource_name, opts=None, </span>additional_capabilities=None<span class="p">, </span>availability_set_id=None<span class="p">, </span>boot_diagnostics=None<span class="p">, </span>delete_data_disks_on_termination=None<span class="p">, </span>delete_os_disk_on_termination=None<span class="p">, </span>identity=None<span class="p">, </span>license_type=None<span class="p">, </span>location=None<span class="p">, </span>name=None<span class="p">, </span>network_interface_ids=None<span class="p">, </span>os_profile=None<span class="p">, </span>os_profile_linux_config=None<span class="p">, </span>os_profile_secrets=None<span class="p">, </span>os_profile_windows_config=None<span class="p">, </span>plan=None<span class="p">, </span>primary_network_interface_id=None<span class="p">, </span>proximity_placement_group_id=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>storage_data_disks=None<span class="p">, </span>storage_image_reference=None<span class="p">, </span>storage_os_disk=None<span class="p">, </span>tags=None<span class="p">, </span>vm_size=None<span class="p">, </span>zones=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewVirtualMachine<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineArgs">VirtualMachineArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachine">VirtualMachine</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Compute.VirtualMachine.html">VirtualMachine</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Compute.Inputs.VirtualMachineArgs.html">VirtualMachineArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Additional<wbr>Capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Availability<wbr>Set<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Boot<wbr>Diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Data<wbr>Disks<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Os<wbr>Disk<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">Virtual<wbr>Machine<wbr>Identity<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Network<wbr>Interface<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Linux<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">List&lt;Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Windows<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">Virtual<wbr>Machine<wbr>Plan<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Primary<wbr>Network<wbr>Interface<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Proximity<wbr>Placement<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Data<wbr>Disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">List&lt;Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Image<wbr>Reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Storage<wbr>Os<wbr>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Vm<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Additional<wbr>Capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">*Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Availability<wbr>Set<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Boot<wbr>Diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">*Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Data<wbr>Disks<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Os<wbr>Disk<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">*Virtual<wbr>Machine<wbr>Identity</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Network<wbr>Interface<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">*Virtual<wbr>Machine<wbr>Os<wbr>Profile</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Linux<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">*Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">[]Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Windows<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">*Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">*Virtual<wbr>Machine<wbr>Plan</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Primary<wbr>Network<wbr>Interface<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Proximity<wbr>Placement<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Data<wbr>Disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">[]Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Image<wbr>Reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">*Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Storage<wbr>Os<wbr>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Vm<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>additional<wbr>Capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities?</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>availability<wbr>Set<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>boot<wbr>Diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics?</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delete<wbr>Data<wbr>Disks<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delete<wbr>Os<wbr>Disk<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">Virtual<wbr>Machine<wbr>Identity?</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>license<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>network<wbr>Interface<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">Virtual<wbr>Machine<wbr>Os<wbr>Profile?</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os<wbr>Profile<wbr>Linux<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os<wbr>Profile<wbr>Secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os<wbr>Profile<wbr>Windows<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">Virtual<wbr>Machine<wbr>Plan?</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>primary<wbr>Network<wbr>Interface<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>proximity<wbr>Placement<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage<wbr>Data<wbr>Disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage<wbr>Image<wbr>Reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference?</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>storage<wbr>Os<wbr>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>vm<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>additional_<wbr>capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">Dict[Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities]</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>availability_<wbr>set_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>boot_<wbr>diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">Dict[Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics]</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delete_<wbr>data_<wbr>disks_<wbr>on_<wbr>termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delete_<wbr>os_<wbr>disk_<wbr>on_<wbr>termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">Dict[Virtual<wbr>Machine<wbr>Identity]</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>license_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>network_<wbr>interface_<wbr>ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os_<wbr>profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">Dict[Virtual<wbr>Machine<wbr>Os<wbr>Profile]</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os_<wbr>profile_<wbr>linux_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">Dict[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os_<wbr>profile_<wbr>secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">List[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret]</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os_<wbr>profile_<wbr>windows_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">Dict[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">Dict[Virtual<wbr>Machine<wbr>Plan]</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>primary_<wbr>network_<wbr>interface_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>proximity_<wbr>placement_<wbr>group_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage_<wbr>data_<wbr>disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">List[Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk]</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage_<wbr>image_<wbr>reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">Dict[Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference]</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>storage_<wbr>os_<wbr>disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Dict[Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk]</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>vm_<wbr>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## VirtualMachine Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Additional<wbr>Capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities?</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Availability<wbr>Set<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Boot<wbr>Diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics?</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Delete<wbr>Data<wbr>Disks<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Delete<wbr>Os<wbr>Disk<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">Virtual<wbr>Machine<wbr>Identity</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Network<wbr>Interface<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Os<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">Virtual<wbr>Machine<wbr>Os<wbr>Profile?</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Os<wbr>Profile<wbr>Linux<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Os<wbr>Profile<wbr>Secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">List&lt;Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Os<wbr>Profile<wbr>Windows<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">Virtual<wbr>Machine<wbr>Plan?</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Primary<wbr>Network<wbr>Interface<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Proximity<wbr>Placement<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Storage<wbr>Data<wbr>Disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">List&lt;Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk&gt;</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Storage<wbr>Image<wbr>Reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Storage<wbr>Os<wbr>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Vm<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Additional<wbr>Capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">*Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Availability<wbr>Set<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Boot<wbr>Diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">*Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Delete<wbr>Data<wbr>Disks<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Delete<wbr>Os<wbr>Disk<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">Virtual<wbr>Machine<wbr>Identity</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Network<wbr>Interface<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Os<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">*Virtual<wbr>Machine<wbr>Os<wbr>Profile</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Os<wbr>Profile<wbr>Linux<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">*Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Os<wbr>Profile<wbr>Secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">[]Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Os<wbr>Profile<wbr>Windows<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">*Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">*Virtual<wbr>Machine<wbr>Plan</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Primary<wbr>Network<wbr>Interface<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Proximity<wbr>Placement<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Storage<wbr>Data<wbr>Disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">[]Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Storage<wbr>Image<wbr>Reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Storage<wbr>Os<wbr>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Vm<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>additional<wbr>Capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities?</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>availability<wbr>Set<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>boot<wbr>Diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics?</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>delete<wbr>Data<wbr>Disks<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>delete<wbr>Os<wbr>Disk<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">Virtual<wbr>Machine<wbr>Identity</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>license<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>network<wbr>Interface<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>os<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">Virtual<wbr>Machine<wbr>Os<wbr>Profile?</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>os<wbr>Profile<wbr>Linux<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>os<wbr>Profile<wbr>Secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>os<wbr>Profile<wbr>Windows<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">Virtual<wbr>Machine<wbr>Plan?</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>primary<wbr>Network<wbr>Interface<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>proximity<wbr>Placement<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>storage<wbr>Data<wbr>Disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk[]</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>storage<wbr>Image<wbr>Reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>storage<wbr>Os<wbr>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>vm<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>additional_<wbr>capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">Dict[Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities]</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>availability_<wbr>set_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>boot_<wbr>diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">Dict[Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics]</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>delete_<wbr>data_<wbr>disks_<wbr>on_<wbr>termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>delete_<wbr>os_<wbr>disk_<wbr>on_<wbr>termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">Dict[Virtual<wbr>Machine<wbr>Identity]</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>license_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>network_<wbr>interface_<wbr>ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>os_<wbr>profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">Dict[Virtual<wbr>Machine<wbr>Os<wbr>Profile]</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>os_<wbr>profile_<wbr>linux_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">Dict[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>os_<wbr>profile_<wbr>secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">List[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret]</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>os_<wbr>profile_<wbr>windows_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">Dict[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">Dict[Virtual<wbr>Machine<wbr>Plan]</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>primary_<wbr>network_<wbr>interface_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>proximity_<wbr>placement_<wbr>group_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>storage_<wbr>data_<wbr>disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">List[Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk]</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>storage_<wbr>image_<wbr>reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">Dict[Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference]</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>storage_<wbr>os_<wbr>disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Dict[Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk]</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>vm_<wbr>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing VirtualMachine Resource

Get an existing VirtualMachine resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/compute/#VirtualMachineState">VirtualMachineState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/compute/#VirtualMachine">VirtualMachine</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>additional_capabilities=None<span class="p">, </span>availability_set_id=None<span class="p">, </span>boot_diagnostics=None<span class="p">, </span>delete_data_disks_on_termination=None<span class="p">, </span>delete_os_disk_on_termination=None<span class="p">, </span>identity=None<span class="p">, </span>license_type=None<span class="p">, </span>location=None<span class="p">, </span>name=None<span class="p">, </span>network_interface_ids=None<span class="p">, </span>os_profile=None<span class="p">, </span>os_profile_linux_config=None<span class="p">, </span>os_profile_secrets=None<span class="p">, </span>os_profile_windows_config=None<span class="p">, </span>plan=None<span class="p">, </span>primary_network_interface_id=None<span class="p">, </span>proximity_placement_group_id=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>storage_data_disks=None<span class="p">, </span>storage_image_reference=None<span class="p">, </span>storage_os_disk=None<span class="p">, </span>tags=None<span class="p">, </span>vm_size=None<span class="p">, </span>zones=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetVirtualMachine<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineState">VirtualMachineState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachine">VirtualMachine</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Compute.VirtualMachine.html">VirtualMachine</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Compute.VirtualMachineState.html">VirtualMachineState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Additional<wbr>Capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Availability<wbr>Set<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Boot<wbr>Diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Data<wbr>Disks<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Os<wbr>Disk<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">Virtual<wbr>Machine<wbr>Identity<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Network<wbr>Interface<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Linux<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">List&lt;Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Windows<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">Virtual<wbr>Machine<wbr>Plan<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Primary<wbr>Network<wbr>Interface<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Proximity<wbr>Placement<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Data<wbr>Disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">List&lt;Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Image<wbr>Reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Os<wbr>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vm<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Additional<wbr>Capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">*Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Availability<wbr>Set<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Boot<wbr>Diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">*Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Data<wbr>Disks<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Os<wbr>Disk<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">*Virtual<wbr>Machine<wbr>Identity</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>License<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Network<wbr>Interface<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">*Virtual<wbr>Machine<wbr>Os<wbr>Profile</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Linux<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">*Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">[]Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Profile<wbr>Windows<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">*Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">*Virtual<wbr>Machine<wbr>Plan</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Primary<wbr>Network<wbr>Interface<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Proximity<wbr>Placement<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Data<wbr>Disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">[]Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Image<wbr>Reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">*Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Os<wbr>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">*Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vm<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>additional<wbr>Capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities?</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>availability<wbr>Set<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>boot<wbr>Diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics?</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delete<wbr>Data<wbr>Disks<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delete<wbr>Os<wbr>Disk<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">Virtual<wbr>Machine<wbr>Identity?</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>license<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>network<wbr>Interface<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">Virtual<wbr>Machine<wbr>Os<wbr>Profile?</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os<wbr>Profile<wbr>Linux<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os<wbr>Profile<wbr>Secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os<wbr>Profile<wbr>Windows<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">Virtual<wbr>Machine<wbr>Plan?</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>primary<wbr>Network<wbr>Interface<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>proximity<wbr>Placement<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage<wbr>Data<wbr>Disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage<wbr>Image<wbr>Reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference?</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage<wbr>Os<wbr>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk?</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vm<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>additional_<wbr>capabilities</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineadditionalcapabilities">Dict[Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities]</a></span>
    </dt>
    <dd>{{% md %}}A `additional_capabilities` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>availability_<wbr>set_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Availability Set in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>boot_<wbr>diagnostics</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinebootdiagnostics">Dict[Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics]</a></span>
    </dt>
    <dd>{{% md %}}A `boot_diagnostics` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delete_<wbr>data_<wbr>disks_<wbr>on_<wbr>termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should the Data Disks (either the Managed Disks / VHD Blobs) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delete_<wbr>os_<wbr>disk_<wbr>on_<wbr>termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should the OS Disk (either the Managed Disk / VHD Blob) be deleted when the Virtual Machine is destroyed? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>identity</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineidentity">Dict[Virtual<wbr>Machine<wbr>Identity]</a></span>
    </dt>
    <dd>{{% md %}}A `identity` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>license_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the BYOL Type for this Virtual Machine. This is only applicable to Windows Virtual Machines. Possible values are `Windows_Client` and `Windows_Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Azure Region where the Virtual Machine exists. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>network_<wbr>interface_<wbr>ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of Network Interface ID's which should be associated with the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os_<wbr>profile</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofile">Dict[Virtual<wbr>Machine<wbr>Os<wbr>Profile]</a></span>
    </dt>
    <dd>{{% md %}}An `os_profile` block. Required when `create_option` in the `storage_os_disk` block is set to `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os_<wbr>profile_<wbr>linux_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfig">Dict[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_linux_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os_<wbr>profile_<wbr>secrets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecret">List[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret]</a></span>
    </dt>
    <dd>{{% md %}}One or more `os_profile_secrets` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os_<wbr>profile_<wbr>windows_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfig">Dict[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A `os_profile_windows_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>plan</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineplan">Dict[Virtual<wbr>Machine<wbr>Plan]</a></span>
    </dt>
    <dd>{{% md %}}A `plan` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>primary_<wbr>network_<wbr>interface_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Network Interface (which must be attached to the Virtual Machine) which should be the Primary Network Interface for this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>proximity_<wbr>placement_<wbr>group_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Proximity Placement Group to which this Virtual Machine should be assigned. Changing this forces a new resource to be created
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Resource Group in which the Virtual Machine should exist. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage_<wbr>data_<wbr>disks</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestoragedatadisk">List[Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk]</a></span>
    </dt>
    <dd>{{% md %}}One or more `storage_data_disk` blocks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage_<wbr>image_<wbr>reference</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageimagereference">Dict[Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference]</a></span>
    </dt>
    <dd>{{% md %}}A `storage_image_reference` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage_<wbr>os_<wbr>disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachinestorageosdisk">Dict[Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk]</a></span>
    </dt>
    <dd>{{% md %}}A `storage_os_disk` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vm_<wbr>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the [size of the Virtual Machine](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-size-specs/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>zones</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A list of a single item of the Availability Zone which the Virtual Machine should be allocated in.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Virtual<wbr>Machine<wbr>Additional<wbr>Capabilities</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineAdditionalCapabilities">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineAdditionalCapabilities">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineAdditionalCapabilitiesArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineAdditionalCapabilitiesOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Ultra<wbr>Ssd<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should Ultra SSD disk be enabled for this Virtual Machine?
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Ultra<wbr>Ssd<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should Ultra SSD disk be enabled for this Virtual Machine?
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>ultra<wbr>Ssd<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}Should Ultra SSD disk be enabled for this Virtual Machine?
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>ultra<wbr>Ssd<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should Ultra SSD disk be enabled for this Virtual Machine?
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Boot<wbr>Diagnostics</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineBootDiagnostics">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineBootDiagnostics">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineBootDiagnosticsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineBootDiagnosticsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should Boot Diagnostics be enabled for this Virtual Machine?
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Storage<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Storage Account's Blob Endpoint which should hold the virtual machine's diagnostic files.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should Boot Diagnostics be enabled for this Virtual Machine?
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Storage<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Storage Account's Blob Endpoint which should hold the virtual machine's diagnostic files.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}Should Boot Diagnostics be enabled for this Virtual Machine?
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>storage<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Storage Account's Blob Endpoint which should hold the virtual machine's diagnostic files.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should Boot Diagnostics be enabled for this Virtual Machine?
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>storage<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Storage Account's Blob Endpoint which should hold the virtual machine's diagnostic files.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Identity</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineIdentity">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineIdentity">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineIdentityArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineIdentityOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Identity<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Specifies a list of user managed identity ids to be assigned to the VM. Required if `type` is `UserAssigned`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Principal<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Principal ID for the Service Principal associated with the Managed Service Identity of this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Managed Service Identity Type of this Virtual Machine. Possible values are `SystemAssigned` (where Azure will generate a Service Principal for you), `UserAssigned` (where you can specify the Service Principal ID's) to be used by this Virtual Machine using the `identity_ids` field, and `SystemAssigned, UserAssigned` which assigns both a system managed identity as well as the specified user assigned identities.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Identity<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Specifies a list of user managed identity ids to be assigned to the VM. Required if `type` is `UserAssigned`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Principal<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Principal ID for the Service Principal associated with the Managed Service Identity of this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Managed Service Identity Type of this Virtual Machine. Possible values are `SystemAssigned` (where Azure will generate a Service Principal for you), `UserAssigned` (where you can specify the Service Principal ID's) to be used by this Virtual Machine using the `identity_ids` field, and `SystemAssigned, UserAssigned` which assigns both a system managed identity as well as the specified user assigned identities.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>identity<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Specifies a list of user managed identity ids to be assigned to the VM. Required if `type` is `UserAssigned`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>principal<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Principal ID for the Service Principal associated with the Managed Service Identity of this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Managed Service Identity Type of this Virtual Machine. Possible values are `SystemAssigned` (where Azure will generate a Service Principal for you), `UserAssigned` (where you can specify the Service Principal ID's) to be used by this Virtual Machine using the `identity_ids` field, and `SystemAssigned, UserAssigned` which assigns both a system managed identity as well as the specified user assigned identities.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>identity<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Specifies a list of user managed identity ids to be assigned to the VM. Required if `type` is `UserAssigned`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>principal_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Principal ID for the Service Principal associated with the Managed Service Identity of this Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Managed Service Identity Type of this Virtual Machine. Possible values are `SystemAssigned` (where Azure will generate a Service Principal for you), `UserAssigned` (where you can specify the Service Principal ID's) to be used by this Virtual Machine using the `identity_ids` field, and `SystemAssigned, UserAssigned` which assigns both a system managed identity as well as the specified user assigned identities.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Os<wbr>Profile</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineOsProfile">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineOsProfile">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Admin<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The password associated with the local administrator account.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Admin<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the local administrator account.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Computer<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies custom data to supply to the machine. On Linux-based systems, this can be used as a cloud-init script. On other systems, this will be copied as a file on disk. Internally, this provider will base64 encode this value before sending it to the API. The maximum length of the binary array is 65535 bytes.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Admin<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The password associated with the local administrator account.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Admin<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the local administrator account.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Computer<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Custom<wbr>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies custom data to supply to the machine. On Linux-based systems, this can be used as a cloud-init script. On other systems, this will be copied as a file on disk. Internally, this provider will base64 encode this value before sending it to the API. The maximum length of the binary array is 65535 bytes.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>admin<wbr>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The password associated with the local administrator account.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>admin<wbr>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the local administrator account.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>computer<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>custom<wbr>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies custom data to supply to the machine. On Linux-based systems, this can be used as a cloud-init script. On other systems, this will be copied as a file on disk. Internally, this provider will base64 encode this value before sending it to the API. The maximum length of the binary array is 65535 bytes.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>admin_<wbr>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The password associated with the local administrator account.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>admin_<wbr>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the local administrator account.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>computer_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>custom_<wbr>data</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies custom data to supply to the machine. On Linux-based systems, this can be used as a cloud-init script. On other systems, this will be copied as a file on disk. Internally, this provider will base64 encode this value before sending it to the API. The maximum length of the binary array is 65535 bytes.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineOsProfileLinuxConfig">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineOsProfileLinuxConfig">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileLinuxConfigArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileLinuxConfigOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Disable<wbr>Password<wbr>Authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Specifies whether password authentication should be disabled. If set to `false`, an `admin_password` must be specified.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ssh<wbr>Keys</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfigsshkey">List&lt;Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config<wbr>Ssh<wbr>Key<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `ssh_keys` blocks. This field is required if `disable_password_authentication` is set to `true`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Disable<wbr>Password<wbr>Authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Specifies whether password authentication should be disabled. If set to `false`, an `admin_password` must be specified.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ssh<wbr>Keys</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfigsshkey">[]Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config<wbr>Ssh<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}One or more `ssh_keys` blocks. This field is required if `disable_password_authentication` is set to `true`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>disable<wbr>Password<wbr>Authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}Specifies whether password authentication should be disabled. If set to `false`, an `admin_password` must be specified.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ssh<wbr>Keys</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfigsshkey">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config<wbr>Ssh<wbr>Key[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `ssh_keys` blocks. This field is required if `disable_password_authentication` is set to `true`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>disable_<wbr>password_<wbr>authentication</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Specifies whether password authentication should be disabled. If set to `false`, an `admin_password` must be specified.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ssh<wbr>Keys</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilelinuxconfigsshkey">List[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config<wbr>Ssh<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}One or more `ssh_keys` blocks. This field is required if `disable_password_authentication` is set to `true`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Linux<wbr>Config<wbr>Ssh<wbr>Key</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineOsProfileLinuxConfigSshKey">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineOsProfileLinuxConfigSshKey">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileLinuxConfigSshKeyArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileLinuxConfigSshKeyOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key<wbr>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Public SSH Key which should be written to the `path` defined above.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The path of the destination file on the virtual machine
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key<wbr>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Public SSH Key which should be written to the `path` defined above.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The path of the destination file on the virtual machine
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>key<wbr>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Public SSH Key which should be written to the `path` defined above.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The path of the destination file on the virtual machine
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>key<wbr>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Public SSH Key which should be written to the `path` defined above.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>path</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The path of the destination file on the virtual machine
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineOsProfileSecret">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineOsProfileSecret">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileSecretArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileSecretOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Source<wbr>Vault<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of the Key Vault to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vault<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecretvaultcertificate">List&lt;Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret<wbr>Vault<wbr>Certificate<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `vault_certificates` blocks.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Source<wbr>Vault<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of the Key Vault to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vault<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecretvaultcertificate">[]Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret<wbr>Vault<wbr>Certificate</a></span>
    </dt>
    <dd>{{% md %}}One or more `vault_certificates` blocks.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>source<wbr>Vault<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of the Key Vault to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vault<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecretvaultcertificate">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret<wbr>Vault<wbr>Certificate[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `vault_certificates` blocks.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>source<wbr>Vault<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of the Key Vault to use.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vault<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilesecretvaultcertificate">List[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret<wbr>Vault<wbr>Certificate]</a></span>
    </dt>
    <dd>{{% md %}}One or more `vault_certificates` blocks.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Secret<wbr>Vault<wbr>Certificate</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineOsProfileSecretVaultCertificate">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineOsProfileSecretVaultCertificate">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileSecretVaultCertificateArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileSecretVaultCertificateOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Certificate<wbr>Store</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the certificate store on the Virtual Machine where the certificate should be added to, such as `My`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Certificate<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Key Vault Secret. Stored secret is the Base64 encoding of a JSON Object that which is encoded in UTF-8 of which the contents need to be:
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Certificate<wbr>Store</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the certificate store on the Virtual Machine where the certificate should be added to, such as `My`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Certificate<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Key Vault Secret. Stored secret is the Base64 encoding of a JSON Object that which is encoded in UTF-8 of which the contents need to be:
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>certificate<wbr>Store</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the certificate store on the Virtual Machine where the certificate should be added to, such as `My`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>certificate<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the Key Vault Secret. Stored secret is the Base64 encoding of a JSON Object that which is encoded in UTF-8 of which the contents need to be:
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>certificate<wbr>Store</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the certificate store on the Virtual Machine where the certificate should be added to, such as `My`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>certificate<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Key Vault Secret. Stored secret is the Base64 encoding of a JSON Object that which is encoded in UTF-8 of which the contents need to be:
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineOsProfileWindowsConfig">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineOsProfileWindowsConfig">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileWindowsConfigArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileWindowsConfigOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Additional<wbr>Unattend<wbr>Configs</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfigadditionalunattendconfig">List&lt;Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Additional<wbr>Unattend<wbr>Config<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A `additional_unattend_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enable<wbr>Automatic<wbr>Upgrades</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Are automatic updates enabled on this Virtual Machine? Defaults to `false.`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Provision<wbr>Vm<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should the Azure Virtual Machine Guest Agent be installed on this Virtual Machine? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Timezone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the time zone of the virtual machine, [the possible values are defined here](http://jackstromberg.com/2017/01/list-of-time-zones-consumed-by-azure/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Winrms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfigwinrm">List&lt;Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Winrm<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more `winrm` block.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Additional<wbr>Unattend<wbr>Configs</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfigadditionalunattendconfig">[]Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Additional<wbr>Unattend<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A `additional_unattend_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enable<wbr>Automatic<wbr>Upgrades</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Are automatic updates enabled on this Virtual Machine? Defaults to `false.`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Provision<wbr>Vm<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should the Azure Virtual Machine Guest Agent be installed on this Virtual Machine? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Timezone</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the time zone of the virtual machine, [the possible values are defined here](http://jackstromberg.com/2017/01/list-of-time-zones-consumed-by-azure/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Winrms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfigwinrm">[]Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Winrm</a></span>
    </dt>
    <dd>{{% md %}}One or more `winrm` block.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>additional<wbr>Unattend<wbr>Configs</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfigadditionalunattendconfig">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Additional<wbr>Unattend<wbr>Config[]?</a></span>
    </dt>
    <dd>{{% md %}}A `additional_unattend_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enable<wbr>Automatic<wbr>Upgrades</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Are automatic updates enabled on this Virtual Machine? Defaults to `false.`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>provision<wbr>Vm<wbr>Agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should the Azure Virtual Machine Guest Agent be installed on this Virtual Machine? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>timezone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the time zone of the virtual machine, [the possible values are defined here](http://jackstromberg.com/2017/01/list-of-time-zones-consumed-by-azure/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>winrms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfigwinrm">Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Winrm[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more `winrm` block.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>additional<wbr>Unattend<wbr>Configs</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfigadditionalunattendconfig">List[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Additional<wbr>Unattend<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A `additional_unattend_config` block.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enable<wbr>Automatic<wbr>Upgrades</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Are automatic updates enabled on this Virtual Machine? Defaults to `false.`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>provision_<wbr>vm_<wbr>agent</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should the Azure Virtual Machine Guest Agent be installed on this Virtual Machine? Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>timezone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the time zone of the virtual machine, [the possible values are defined here](http://jackstromberg.com/2017/01/list-of-time-zones-consumed-by-azure/).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>winrms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#virtualmachineosprofilewindowsconfigwinrm">List[Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Winrm]</a></span>
    </dt>
    <dd>{{% md %}}One or more `winrm` block.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Additional<wbr>Unattend<wbr>Config</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineOsProfileWindowsConfigAdditionalUnattendConfig">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineOsProfileWindowsConfigAdditionalUnattendConfig">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileWindowsConfigAdditionalUnattendConfigArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileWindowsConfigAdditionalUnattendConfigOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Component</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the component to configure with the added content. The only allowable value is `Microsoft-Windows-Shell-Setup`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Content</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the base-64 encoded XML formatted content that is added to the unattend.xml file for the specified path and component.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Pass</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the pass that the content applies to. The only allowable value is `oobeSystem`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Setting<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the setting to which the content applies. Possible values are: `FirstLogonCommands` and `AutoLogon`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Component</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the component to configure with the added content. The only allowable value is `Microsoft-Windows-Shell-Setup`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Content</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the base-64 encoded XML formatted content that is added to the unattend.xml file for the specified path and component.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Pass</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the pass that the content applies to. The only allowable value is `oobeSystem`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Setting<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the setting to which the content applies. Possible values are: `FirstLogonCommands` and `AutoLogon`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>component</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the component to configure with the added content. The only allowable value is `Microsoft-Windows-Shell-Setup`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>content</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the base-64 encoded XML formatted content that is added to the unattend.xml file for the specified path and component.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>pass</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the pass that the content applies to. The only allowable value is `oobeSystem`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>setting<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the setting to which the content applies. Possible values are: `FirstLogonCommands` and `AutoLogon`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>component</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the component to configure with the added content. The only allowable value is `Microsoft-Windows-Shell-Setup`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>content</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the base-64 encoded XML formatted content that is added to the unattend.xml file for the specified path and component.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>pass</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the pass that the content applies to. The only allowable value is `oobeSystem`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>setting<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the setting to which the content applies. Possible values are: `FirstLogonCommands` and `AutoLogon`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Os<wbr>Profile<wbr>Windows<wbr>Config<wbr>Winrm</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineOsProfileWindowsConfigWinrm">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineOsProfileWindowsConfigWinrm">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileWindowsConfigWinrmArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineOsProfileWindowsConfigWinrmOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Certificate<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Key Vault Secret which contains the encrypted Certificate which should be installed on the Virtual Machine. This certificate must also be specified in the `vault_certificates` block within the `os_profile_secrets` block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the protocol of listener. Possible values are `HTTP` or `HTTPS`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Certificate<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the Key Vault Secret which contains the encrypted Certificate which should be installed on the Virtual Machine. This certificate must also be specified in the `vault_certificates` block within the `os_profile_secrets` block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the protocol of listener. Possible values are `HTTP` or `HTTPS`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>certificate<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the Key Vault Secret which contains the encrypted Certificate which should be installed on the Virtual Machine. This certificate must also be specified in the `vault_certificates` block within the `os_profile_secrets` block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the protocol of listener. Possible values are `HTTP` or `HTTPS`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>certificate<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the Key Vault Secret which contains the encrypted Certificate which should be installed on the Virtual Machine. This certificate must also be specified in the `vault_certificates` block within the `os_profile_secrets` block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the protocol of listener. Possible values are `HTTP` or `HTTPS`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Plan</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachinePlan">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachinePlan">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachinePlanArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachinePlanOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the image from the marketplace.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Product</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the product of the image from the marketplace.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Publisher</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the publisher of the image.
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
    <dd>{{% md %}}Specifies the name of the image from the marketplace.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Product</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the product of the image from the marketplace.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Publisher</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the publisher of the image.
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
    <dd>{{% md %}}Specifies the name of the image from the marketplace.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>product</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the product of the image from the marketplace.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>publisher</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the publisher of the image.
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
    <dd>{{% md %}}Specifies the name of the image from the marketplace.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>product</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the product of the image from the marketplace.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>publisher</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the publisher of the image.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Storage<wbr>Data<wbr>Disk</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineStorageDataDisk">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineStorageDataDisk">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineStorageDataDiskArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineStorageDataDiskOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Caching</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the caching requirements for the Data Disk. Possible values include `None`, `ReadOnly` and `ReadWrite`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Create<wbr>Option</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies how the data disk should be created. Possible values are `Attach`, `FromImage` and `Empty`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disk<wbr>Size<wbr>Gb</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies the size of the data disk in gigabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Lun</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Specifies the logical unit number of the data disk. This needs to be unique within all the Data Disks on the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Managed<wbr>Disk<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of an Existing Managed Disk which should be attached to this Virtual Machine. When this field is set `create_option` must be set to `Attach`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Managed<wbr>Disk<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the type of managed disk to create. Possible values are either `Standard_LRS`, `StandardSSD_LRS`, `Premium_LRS` or `UltraSSD_LRS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Data Disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vhd<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the URI of the VHD file backing this Unmanaged Data Disk. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Write<wbr>Accelerator<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Specifies if Write Accelerator is enabled on the disk. This can only be enabled on `Premium_LRS` managed disks with no caching and [M-Series VMs](https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/how-to-enable-write-accelerator). Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Caching</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the caching requirements for the Data Disk. Possible values include `None`, `ReadOnly` and `ReadWrite`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Create<wbr>Option</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies how the data disk should be created. Possible values are `Attach`, `FromImage` and `Empty`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disk<wbr>Size<wbr>Gb</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies the size of the data disk in gigabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Lun</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Specifies the logical unit number of the data disk. This needs to be unique within all the Data Disks on the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Managed<wbr>Disk<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of an Existing Managed Disk which should be attached to this Virtual Machine. When this field is set `create_option` must be set to `Attach`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Managed<wbr>Disk<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the type of managed disk to create. Possible values are either `Standard_LRS`, `StandardSSD_LRS`, `Premium_LRS` or `UltraSSD_LRS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Data Disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vhd<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the URI of the VHD file backing this Unmanaged Data Disk. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Write<wbr>Accelerator<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Specifies if Write Accelerator is enabled on the disk. This can only be enabled on `Premium_LRS` managed disks with no caching and [M-Series VMs](https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/how-to-enable-write-accelerator). Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>caching</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the caching requirements for the Data Disk. Possible values include `None`, `ReadOnly` and `ReadWrite`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>create<wbr>Option</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies how the data disk should be created. Possible values are `Attach`, `FromImage` and `Empty`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disk<wbr>Size<wbr>Gb</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies the size of the data disk in gigabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>lun</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Specifies the logical unit number of the data disk. This needs to be unique within all the Data Disks on the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>managed<wbr>Disk<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of an Existing Managed Disk which should be attached to this Virtual Machine. When this field is set `create_option` must be set to `Attach`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>managed<wbr>Disk<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the type of managed disk to create. Possible values are either `Standard_LRS`, `StandardSSD_LRS`, `Premium_LRS` or `UltraSSD_LRS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Data Disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vhd<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the URI of the VHD file backing this Unmanaged Data Disk. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>write<wbr>Accelerator<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Specifies if Write Accelerator is enabled on the disk. This can only be enabled on `Premium_LRS` managed disks with no caching and [M-Series VMs](https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/how-to-enable-write-accelerator). Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>caching</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the caching requirements for the Data Disk. Possible values include `None`, `ReadOnly` and `ReadWrite`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>create_<wbr>option</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies how the data disk should be created. Possible values are `Attach`, `FromImage` and `Empty`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disk_<wbr>size_<wbr>gb</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the size of the data disk in gigabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>lun</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the logical unit number of the data disk. This needs to be unique within all the Data Disks on the Virtual Machine.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>managed_<wbr>disk_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of an Existing Managed Disk which should be attached to this Virtual Machine. When this field is set `create_option` must be set to `Attach`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>managed<wbr>Disk<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the type of managed disk to create. Possible values are either `Standard_LRS`, `StandardSSD_LRS`, `Premium_LRS` or `UltraSSD_LRS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the Data Disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vhd<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the URI of the VHD file backing this Unmanaged Data Disk. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>write_<wbr>accelerator_<wbr>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Specifies if Write Accelerator is enabled on the disk. This can only be enabled on `Premium_LRS` managed disks with no caching and [M-Series VMs](https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/how-to-enable-write-accelerator). Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Storage<wbr>Image<wbr>Reference</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineStorageImageReference">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineStorageImageReference">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineStorageImageReferenceArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineStorageImageReferenceOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of the Custom Image which the Virtual Machine should be created from. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Offer</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the offer of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Publisher</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the publisher of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sku</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the SKU of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the version of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of the Custom Image which the Virtual Machine should be created from. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Offer</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the offer of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Publisher</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the publisher of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sku</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the SKU of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the version of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of the Custom Image which the Virtual Machine should be created from. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>offer</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the offer of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>publisher</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the publisher of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sku</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the SKU of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the version of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of the Custom Image which the Virtual Machine should be created from. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>offer</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the offer of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>publisher</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the publisher of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sku</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the SKU of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the version of the image used to create the virtual machine. Changing this forces a new resource to be created.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Virtual<wbr>Machine<wbr>Storage<wbr>Os<wbr>Disk</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/input/#VirtualMachineStorageOsDisk">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/azure/types/output/#VirtualMachineStorageOsDisk">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineStorageOsDiskArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/compute?tab=doc#VirtualMachineStorageOsDiskOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Caching</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the caching requirements for the OS Disk. Possible values include `None`, `ReadOnly` and `ReadWrite`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Create<wbr>Option</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies how the OS Disk should be created. Possible values are `Attach` (managed disks only) and `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disk<wbr>Size<wbr>Gb</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies the size of the OS Disk in gigabytes.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Image<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Image URI in the format `publisherName:offer:skus:version`. This field can also specify the [VHD uri](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-cli-deploy-templates/#create-a-custom-vm-image) of a custom VM image to clone. When cloning a Custom (Unmanaged) Disk Image the `os_type` field must be set.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Managed<wbr>Disk<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of an existing Managed Disk which should be attached as the OS Disk of this Virtual Machine. If this is set then the `create_option` must be set to `Attach`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Managed<wbr>Disk<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the type of Managed Disk which should be created. Possible values are `Standard_LRS`, `StandardSSD_LRS` or `Premium_LRS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the OS Disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Operating System on the OS Disk. Possible values are `Linux` and `Windows`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vhd<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the URI of the VHD file backing this Unmanaged OS Disk. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Write<wbr>Accelerator<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Specifies if Write Accelerator is enabled on the disk. This can only be enabled on `Premium_LRS` managed disks with no caching and [M-Series VMs](https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/how-to-enable-write-accelerator). Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Caching</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the caching requirements for the OS Disk. Possible values include `None`, `ReadOnly` and `ReadWrite`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Create<wbr>Option</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies how the OS Disk should be created. Possible values are `Attach` (managed disks only) and `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disk<wbr>Size<wbr>Gb</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies the size of the OS Disk in gigabytes.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Image<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the Image URI in the format `publisherName:offer:skus:version`. This field can also specify the [VHD uri](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-cli-deploy-templates/#create-a-custom-vm-image) of a custom VM image to clone. When cloning a Custom (Unmanaged) Disk Image the `os_type` field must be set.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Managed<wbr>Disk<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of an existing Managed Disk which should be attached as the OS Disk of this Virtual Machine. If this is set then the `create_option` must be set to `Attach`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Managed<wbr>Disk<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the type of Managed Disk which should be created. Possible values are `Standard_LRS`, `StandardSSD_LRS` or `Premium_LRS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the OS Disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Os<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the Operating System on the OS Disk. Possible values are `Linux` and `Windows`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vhd<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the URI of the VHD file backing this Unmanaged OS Disk. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Write<wbr>Accelerator<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Specifies if Write Accelerator is enabled on the disk. This can only be enabled on `Premium_LRS` managed disks with no caching and [M-Series VMs](https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/how-to-enable-write-accelerator). Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>caching</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the caching requirements for the OS Disk. Possible values include `None`, `ReadOnly` and `ReadWrite`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>create<wbr>Option</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies how the OS Disk should be created. Possible values are `Attach` (managed disks only) and `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disk<wbr>Size<wbr>Gb</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies the size of the OS Disk in gigabytes.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>image<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Image URI in the format `publisherName:offer:skus:version`. This field can also specify the [VHD uri](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-cli-deploy-templates/#create-a-custom-vm-image) of a custom VM image to clone. When cloning a Custom (Unmanaged) Disk Image the `os_type` field must be set.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>managed<wbr>Disk<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of an existing Managed Disk which should be attached as the OS Disk of this Virtual Machine. If this is set then the `create_option` must be set to `Attach`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>managed<wbr>Disk<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the type of Managed Disk which should be created. Possible values are `Standard_LRS`, `StandardSSD_LRS` or `Premium_LRS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the OS Disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the Operating System on the OS Disk. Possible values are `Linux` and `Windows`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vhd<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the URI of the VHD file backing this Unmanaged OS Disk. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>write<wbr>Accelerator<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Specifies if Write Accelerator is enabled on the disk. This can only be enabled on `Premium_LRS` managed disks with no caching and [M-Series VMs](https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/how-to-enable-write-accelerator). Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>caching</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the caching requirements for the OS Disk. Possible values include `None`, `ReadOnly` and `ReadWrite`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>create_<wbr>option</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies how the OS Disk should be created. Possible values are `Attach` (managed disks only) and `FromImage`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disk_<wbr>size_<wbr>gb</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the size of the OS Disk in gigabytes.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>image<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Image URI in the format `publisherName:offer:skus:version`. This field can also specify the [VHD uri](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-cli-deploy-templates/#create-a-custom-vm-image) of a custom VM image to clone. When cloning a Custom (Unmanaged) Disk Image the `os_type` field must be set.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>managed_<wbr>disk_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the ID of an existing Managed Disk which should be attached as the OS Disk of this Virtual Machine. If this is set then the `create_option` must be set to `Attach`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>managed<wbr>Disk<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the type of Managed Disk which should be created. Possible values are `Standard_LRS`, `StandardSSD_LRS` or `Premium_LRS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the OS Disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>os_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Operating System on the OS Disk. Possible values are `Linux` and `Windows`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vhd<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the URI of the VHD file backing this Unmanaged OS Disk. Changing this forces a new resource to be created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>write_<wbr>accelerator_<wbr>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Specifies if Write Accelerator is enabled on the disk. This can only be enabled on `Premium_LRS` managed disks with no caching and [M-Series VMs](https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/how-to-enable-write-accelerator). Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







