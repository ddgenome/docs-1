
---
title: "GetAmi"
block_external_search_index: true
---

Use this data source to get the ID of a registered AMI for use in other
resources.

## Example Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const example = aws.getAmi({
    executableUsers: ["self"],
    filters: [
        {
            name: "name",
            values: ["myami-*"],
        },
        {
            name: "root-device-type",
            values: ["ebs"],
        },
        {
            name: "virtualization-type",
            values: ["hvm"],
        },
    ],
    mostRecent: true,
    nameRegex: "^myami-\\d{3}",
    owners: ["self"],
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/d/ami.html.markdown.





## Using GetAmi

{{< chooser language "javascript,typescript,python,go,csharp" / >}}


{{% choosable language typescript %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">function </span>getAmi<span class="p">(</span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/#GetAmiArgs">GetAmiArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#InvokeOptions">pulumi.InvokeOptions</a></span><span class="p">): Promise&lt;<span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/#GetAmiResult">GetAmiResult</a></span>></span></code></pre></div>
{{% /choosable %}}


{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">function </span> get_ami(</span>executable_users=None<span class="p">, </span>filters=None<span class="p">, </span>most_recent=None<span class="p">, </span>name_regex=None<span class="p">, </span>owners=None<span class="p">, </span>tags=None<span class="p">, </span>opts=None<span class="p">)</span></code></pre></div>
{{% /choosable %}}


{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>LookupAmi<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/?tab=doc#GetAmiArgs">GetAmiArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#InvokeOption">pulumi.InvokeOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/?tab=doc#LookupAmiResult">LookupAmiResult</a></span>, error)</span></code></pre></div>
{{% /choosable %}}


{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static class </span><span class="nx">GetAmi </span><span class="p">{</span><span class="k">
    public static </span>Task&lt;<span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.GetAmiResult.html">GetAmiResult</a></span>> <span class="p">InvokeAsync(</span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Inputs.GetAmiArgs.html">GetAmiArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.InvokeOptions.html">Pulumi.InvokeOptions</a></span>? <span class="nx">opts = null<span class="p">)</span><span class="p">
}</span></code></pre></div>
{{% /choosable %}}



The following arguments are supported:



{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Executable<wbr>Users</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Limit search to users with *explicit* launch permission on
the image. Valid items are the numeric account ID or `self`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamifilter">List&lt;Pulumi.<wbr>Aws.<wbr>Inputs.<wbr>Get<wbr>Ami<wbr>Filter<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}One or more name/value pairs to filter off of. There are
several valid keys, for a full reference, check out
[describe-images in the AWS CLI reference][1].
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Most<wbr>Recent</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If more than one result is returned, use the most
recent AMI.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name<wbr>Regex</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A regex string to apply to the AMI list returned
by AWS. This allows more advanced filtering not supported from the AWS API. This
filtering is done locally on what AWS returns, and could have a performance
impact if the result is large. It is recommended to combine this with other
options to narrow down the list AWS returns.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Owners</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}List of AMI owners to limit search. At least 1 value must be specified. Valid values: an AWS account ID, `self` (the current account), or an AWS owner alias (e.g. `amazon`, `aws-marketplace`, `microsoft`).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}Any tags assigned to the image.
* `tags.#.key` - The key name of the tag.
* `tags.#.value` - The value of the tag.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Executable<wbr>Users</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Limit search to users with *explicit* launch permission on
the image. Valid items are the numeric account ID or `self`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamifilter">[]Get<wbr>Ami<wbr>Filter</a></span>
    </dt>
    <dd>{{% md %}}One or more name/value pairs to filter off of. There are
several valid keys, for a full reference, check out
[describe-images in the AWS CLI reference][1].
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Most<wbr>Recent</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If more than one result is returned, use the most
recent AMI.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name<wbr>Regex</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A regex string to apply to the AMI list returned
by AWS. This allows more advanced filtering not supported from the AWS API. This
filtering is done locally on what AWS returns, and could have a performance
impact if the result is large. It is recommended to combine this with other
options to narrow down the list AWS returns.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Owners</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of AMI owners to limit search. At least 1 value must be specified. Valid values: an AWS account ID, `self` (the current account), or an AWS owner alias (e.g. `amazon`, `aws-marketplace`, `microsoft`).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Any tags assigned to the image.
* `tags.#.key` - The key name of the tag.
* `tags.#.value` - The value of the tag.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>executable<wbr>Users</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Limit search to users with *explicit* launch permission on
the image. Valid items are the numeric account ID or `self`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamifilter">Get<wbr>Ami<wbr>Filter[]?</a></span>
    </dt>
    <dd>{{% md %}}One or more name/value pairs to filter off of. There are
several valid keys, for a full reference, check out
[describe-images in the AWS CLI reference][1].
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>most<wbr>Recent</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If more than one result is returned, use the most
recent AMI.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name<wbr>Regex</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A regex string to apply to the AMI list returned
by AWS. This allows more advanced filtering not supported from the AWS API. This
filtering is done locally on what AWS returns, and could have a performance
impact if the result is large. It is recommended to combine this with other
options to narrow down the list AWS returns.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>owners</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}List of AMI owners to limit search. At least 1 value must be specified. Valid values: an AWS account ID, `self` (the current account), or an AWS owner alias (e.g. `amazon`, `aws-marketplace`, `microsoft`).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}Any tags assigned to the image.
* `tags.#.key` - The key name of the tag.
* `tags.#.value` - The value of the tag.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>executable_<wbr>users</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Limit search to users with *explicit* launch permission on
the image. Valid items are the numeric account ID or `self`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamifilter">List[Get<wbr>Ami<wbr>Filter]</a></span>
    </dt>
    <dd>{{% md %}}One or more name/value pairs to filter off of. There are
several valid keys, for a full reference, check out
[describe-images in the AWS CLI reference][1].
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>most_<wbr>recent</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If more than one result is returned, use the most
recent AMI.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name_<wbr>regex</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A regex string to apply to the AMI list returned
by AWS. This allows more advanced filtering not supported from the AWS API. This
filtering is done locally on what AWS returns, and could have a performance
impact if the result is large. It is recommended to combine this with other
options to narrow down the list AWS returns.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>owners</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of AMI owners to limit search. At least 1 value must be specified. Valid values: an AWS account ID, `self` (the current account), or an AWS owner alias (e.g. `amazon`, `aws-marketplace`, `microsoft`).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Any tags assigned to the image.
* `tags.#.key` - The key name of the tag.
* `tags.#.value` - The value of the tag.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## GetAmi Result

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Architecture</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The OS architecture of the AMI (ie: `i386` or `x86_64`).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Block<wbr>Device<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamiblockdevicemapping">List&lt;Pulumi.<wbr>Aws.<wbr>Outputs.<wbr>Get<wbr>Ami<wbr>Block<wbr>Device<wbr>Mapping&gt;</a></span>
    </dt>
    <dd>{{% md %}}The block device mappings of the AMI.
* `block_device_mappings.#.device_name` - The physical name of the device.
* `block_device_mappings.#.ebs.delete_on_termination` - `true` if the EBS volume
will be deleted on termination.
* `block_device_mappings.#.ebs.encrypted` - `true` if the EBS volume
is encrypted.
* `block_device_mappings.#.ebs.iops` - `0` if the EBS volume is
not a provisioned IOPS image, otherwise the supported IOPS count.
* `block_device_mappings.#.ebs.snapshot_id` - The ID of the snapshot.
* `block_device_mappings.#.ebs.volume_size` - The size of the volume, in GiB.
* `block_device_mappings.#.ebs.volume_type` - The volume type.
* `block_device_mappings.#.no_device` - Suppresses the specified device
included in the block device mapping of the AMI.
* `block_device_mappings.#.virtual_name` - The virtual device name (for
instance stores).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Creation<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The date and time the image was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The description of the AMI that was provided during image
creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Executable<wbr>Users</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamifilter">List&lt;Pulumi.<wbr>Aws.<wbr>Outputs.<wbr>Get<wbr>Ami<wbr>Filter&gt;?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hypervisor</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The hypervisor type of the image.
{{% /md %}}</dd>

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
        <span>Image<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the AMI. Should be the same as the resource `id`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Image<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The location of the AMI.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Image<wbr>Owner<wbr>Alias</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The AWS account alias (for example, `amazon`, `self`) or
the AWS account ID of the AMI owner.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Image<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of image.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Kernel<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The kernel associated with the image, if any. Only applicable
for machine images.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Most<wbr>Recent</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the AMI that was provided during image creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name<wbr>Regex</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Owner<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The AWS account ID of the image owner.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Owners</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The value is Windows for `Windows` AMIs; otherwise blank.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Product<wbr>Codes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamiproductcode">List&lt;Pulumi.<wbr>Aws.<wbr>Outputs.<wbr>Get<wbr>Ami<wbr>Product<wbr>Code&gt;</a></span>
    </dt>
    <dd>{{% md %}}Any product codes associated with the AMI.
* `product_codes.#.product_code_id` - The product code.
* `product_codes.#.product_code_type` - The type of product code.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Public</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}`true` if the image has public launch permissions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ramdisk<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The RAM disk associated with the image, if any. Only applicable
for machine images.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Root<wbr>Device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The device name of the root device.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of root device (ie: `ebs` or `instance-store`).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Root<wbr>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The snapshot id associated with the root device, if any
(only applies to `ebs` root devices).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sriov<wbr>Net<wbr>Support</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies whether enhanced networking is enabled.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The current state of the AMI. If the state is `available`, the image
is successfully registered and can be used to launch an instance.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>State<wbr>Reason</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object></span>
    </dt>
    <dd>{{% md %}}Describes a state change. Fields are `UNSET` if not available.
* `state_reason.code` - The reason code for the state change.
* `state_reason.message` - The message for the state change.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object></span>
    </dt>
    <dd>{{% md %}}Any tags assigned to the image.
* `tags.#.key` - The key name of the tag.
* `tags.#.value` - The value of the tag.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Virtualization<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of virtualization of the AMI (ie: `hvm` or
`paravirtual`).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Architecture</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The OS architecture of the AMI (ie: `i386` or `x86_64`).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Block<wbr>Device<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamiblockdevicemapping">[]Get<wbr>Ami<wbr>Block<wbr>Device<wbr>Mapping</a></span>
    </dt>
    <dd>{{% md %}}The block device mappings of the AMI.
* `block_device_mappings.#.device_name` - The physical name of the device.
* `block_device_mappings.#.ebs.delete_on_termination` - `true` if the EBS volume
will be deleted on termination.
* `block_device_mappings.#.ebs.encrypted` - `true` if the EBS volume
is encrypted.
* `block_device_mappings.#.ebs.iops` - `0` if the EBS volume is
not a provisioned IOPS image, otherwise the supported IOPS count.
* `block_device_mappings.#.ebs.snapshot_id` - The ID of the snapshot.
* `block_device_mappings.#.ebs.volume_size` - The size of the volume, in GiB.
* `block_device_mappings.#.ebs.volume_type` - The volume type.
* `block_device_mappings.#.no_device` - Suppresses the specified device
included in the block device mapping of the AMI.
* `block_device_mappings.#.virtual_name` - The virtual device name (for
instance stores).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Creation<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The date and time the image was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The description of the AMI that was provided during image
creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Executable<wbr>Users</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamifilter">[]Get<wbr>Ami<wbr>Filter</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hypervisor</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The hypervisor type of the image.
{{% /md %}}</dd>

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
        <span>Image<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the AMI. Should be the same as the resource `id`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Image<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The location of the AMI.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Image<wbr>Owner<wbr>Alias</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The AWS account alias (for example, `amazon`, `self`) or
the AWS account ID of the AMI owner.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Image<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of image.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Kernel<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The kernel associated with the image, if any. Only applicable
for machine images.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Most<wbr>Recent</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the AMI that was provided during image creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name<wbr>Regex</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Owner<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The AWS account ID of the image owner.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Owners</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The value is Windows for `Windows` AMIs; otherwise blank.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Product<wbr>Codes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamiproductcode">[]Get<wbr>Ami<wbr>Product<wbr>Code</a></span>
    </dt>
    <dd>{{% md %}}Any product codes associated with the AMI.
* `product_codes.#.product_code_id` - The product code.
* `product_codes.#.product_code_type` - The type of product code.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Public</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}`true` if the image has public launch permissions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ramdisk<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The RAM disk associated with the image, if any. Only applicable
for machine images.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Root<wbr>Device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The device name of the root device.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of root device (ie: `ebs` or `instance-store`).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Root<wbr>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The snapshot id associated with the root device, if any
(only applies to `ebs` root devices).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sriov<wbr>Net<wbr>Support</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies whether enhanced networking is enabled.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The current state of the AMI. If the state is `available`, the image
is successfully registered and can be used to launch an instance.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>State<wbr>Reason</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Describes a state change. Fields are `UNSET` if not available.
* `state_reason.code` - The reason code for the state change.
* `state_reason.message` - The message for the state change.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Any tags assigned to the image.
* `tags.#.key` - The key name of the tag.
* `tags.#.value` - The value of the tag.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Virtualization<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of virtualization of the AMI (ie: `hvm` or
`paravirtual`).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>architecture</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The OS architecture of the AMI (ie: `i386` or `x86_64`).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>block<wbr>Device<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamiblockdevicemapping">Get<wbr>Ami<wbr>Block<wbr>Device<wbr>Mapping[]</a></span>
    </dt>
    <dd>{{% md %}}The block device mappings of the AMI.
* `block_device_mappings.#.device_name` - The physical name of the device.
* `block_device_mappings.#.ebs.delete_on_termination` - `true` if the EBS volume
will be deleted on termination.
* `block_device_mappings.#.ebs.encrypted` - `true` if the EBS volume
is encrypted.
* `block_device_mappings.#.ebs.iops` - `0` if the EBS volume is
not a provisioned IOPS image, otherwise the supported IOPS count.
* `block_device_mappings.#.ebs.snapshot_id` - The ID of the snapshot.
* `block_device_mappings.#.ebs.volume_size` - The size of the volume, in GiB.
* `block_device_mappings.#.ebs.volume_type` - The volume type.
* `block_device_mappings.#.no_device` - Suppresses the specified device
included in the block device mapping of the AMI.
* `block_device_mappings.#.virtual_name` - The virtual device name (for
instance stores).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>creation<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The date and time the image was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The description of the AMI that was provided during image
creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>executable<wbr>Users</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamifilter">Get<wbr>Ami<wbr>Filter[]?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hypervisor</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The hypervisor type of the image.
{{% /md %}}</dd>

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
        <span>image<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the AMI. Should be the same as the resource `id`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>image<wbr>Location</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The location of the AMI.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>image<wbr>Owner<wbr>Alias</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The AWS account alias (for example, `amazon`, `self`) or
the AWS account ID of the AMI owner.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>image<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of image.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>kernel<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The kernel associated with the image, if any. Only applicable
for machine images.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>most<wbr>Recent</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the AMI that was provided during image creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name<wbr>Regex</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>owner<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The AWS account ID of the image owner.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>owners</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The value is Windows for `Windows` AMIs; otherwise blank.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>product<wbr>Codes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamiproductcode">Get<wbr>Ami<wbr>Product<wbr>Code[]</a></span>
    </dt>
    <dd>{{% md %}}Any product codes associated with the AMI.
* `product_codes.#.product_code_id` - The product code.
* `product_codes.#.product_code_type` - The type of product code.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>public</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}`true` if the image has public launch permissions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ramdisk<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The RAM disk associated with the image, if any. Only applicable
for machine images.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>root<wbr>Device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The device name of the root device.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>root<wbr>Device<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of root device (ie: `ebs` or `instance-store`).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>root<wbr>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The snapshot id associated with the root device, if any
(only applies to `ebs` root devices).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sriov<wbr>Net<wbr>Support</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies whether enhanced networking is enabled.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>state</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The current state of the AMI. If the state is `available`, the image
is successfully registered and can be used to launch an instance.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>state<wbr>Reason</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}</span>
    </dt>
    <dd>{{% md %}}Describes a state change. Fields are `UNSET` if not available.
* `state_reason.code` - The reason code for the state change.
* `state_reason.message` - The message for the state change.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}</span>
    </dt>
    <dd>{{% md %}}Any tags assigned to the image.
* `tags.#.key` - The key name of the tag.
* `tags.#.value` - The value of the tag.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>virtualization<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of virtualization of the AMI (ie: `hvm` or
`paravirtual`).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>architecture</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The OS architecture of the AMI (ie: `i386` or `x86_64`).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>block_<wbr>device_<wbr>mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamiblockdevicemapping">List[Get<wbr>Ami<wbr>Block<wbr>Device<wbr>Mapping]</a></span>
    </dt>
    <dd>{{% md %}}The block device mappings of the AMI.
* `block_device_mappings.#.device_name` - The physical name of the device.
* `block_device_mappings.#.ebs.delete_on_termination` - `true` if the EBS volume
will be deleted on termination.
* `block_device_mappings.#.ebs.encrypted` - `true` if the EBS volume
is encrypted.
* `block_device_mappings.#.ebs.iops` - `0` if the EBS volume is
not a provisioned IOPS image, otherwise the supported IOPS count.
* `block_device_mappings.#.ebs.snapshot_id` - The ID of the snapshot.
* `block_device_mappings.#.ebs.volume_size` - The size of the volume, in GiB.
* `block_device_mappings.#.ebs.volume_type` - The volume type.
* `block_device_mappings.#.no_device` - Suppresses the specified device
included in the block device mapping of the AMI.
* `block_device_mappings.#.virtual_name` - The virtual device name (for
instance stores).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>creation_<wbr>date</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The date and time the image was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The description of the AMI that was provided during image
creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>executable_<wbr>users</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamifilter">List[Get<wbr>Ami<wbr>Filter]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hypervisor</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The hypervisor type of the image.
{{% /md %}}</dd>

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
        <span>image_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the AMI. Should be the same as the resource `id`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>image_<wbr>location</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The location of the AMI.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>image_<wbr>owner_<wbr>alias</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The AWS account alias (for example, `amazon`, `self`) or
the AWS account ID of the AMI owner.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>image_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of image.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>kernel_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The kernel associated with the image, if any. Only applicable
for machine images.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>most_<wbr>recent</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the AMI that was provided during image creation.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name_<wbr>regex</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>owner_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The AWS account ID of the image owner.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>owners</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The value is Windows for `Windows` AMIs; otherwise blank.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>product_<wbr>codes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getamiproductcode">List[Get<wbr>Ami<wbr>Product<wbr>Code]</a></span>
    </dt>
    <dd>{{% md %}}Any product codes associated with the AMI.
* `product_codes.#.product_code_id` - The product code.
* `product_codes.#.product_code_type` - The type of product code.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>public</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}`true` if the image has public launch permissions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ramdisk_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The RAM disk associated with the image, if any. Only applicable
for machine images.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>root_<wbr>device_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The device name of the root device.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>root_<wbr>device_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of root device (ie: `ebs` or `instance-store`).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>root_<wbr>snapshot_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The snapshot id associated with the root device, if any
(only applies to `ebs` root devices).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sriov_<wbr>net_<wbr>support</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies whether enhanced networking is enabled.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>state</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The current state of the AMI. If the state is `available`, the image
is successfully registered and can be used to launch an instance.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>state_<wbr>reason</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Describes a state change. Fields are `UNSET` if not available.
* `state_reason.code` - The reason code for the state change.
* `state_reason.message` - The message for the state change.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Any tags assigned to the image.
* `tags.#.key` - The key name of the tag.
* `tags.#.value` - The value of the tag.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>virtualization_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of virtualization of the AMI (ie: `hvm` or
`paravirtual`).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Supporting Types

<h4>Get<wbr>Ami<wbr>Block<wbr>Device<wbr>Mapping</h4>
{{% choosable language nodejs %}}
> See the   <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#GetAmiBlockDeviceMapping">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the   <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/?tab=doc#GetAmiBlockDeviceMapping">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Ebs</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>No<wbr>Device</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Virtual<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Ebs</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>No<wbr>Device</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Virtual<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>ebs</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>no<wbr>Device</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>virtual<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>device_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>ebs</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>no<wbr>Device</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>virtual<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Get<wbr>Ami<wbr>Filter</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#GetAmiFilter">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#GetAmiFilter">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/?tab=doc#GetAmiFilterArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/?tab=doc#GetAmiFilter">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the AMI that was provided during image creation.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Values</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

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
    <dd>{{% md %}}The name of the AMI that was provided during image creation.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Values</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

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
    <dd>{{% md %}}The name of the AMI that was provided during image creation.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>values</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

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
    <dd>{{% md %}}The name of the AMI that was provided during image creation.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>values</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Get<wbr>Ami<wbr>Product<wbr>Code</h4>
{{% choosable language nodejs %}}
> See the   <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#GetAmiProductCode">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the   <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/?tab=doc#GetAmiProductCode">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Product<wbr>Code<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Product<wbr>Code<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Product<wbr>Code<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Product<wbr>Code<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>product<wbr>Code<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>product<wbr>Code<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>product<wbr>Code<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>product<wbr>Code<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}







