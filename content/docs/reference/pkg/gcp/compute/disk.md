
---
title: "Disk"
block_external_search_index: true
---

Persistent disks are durable storage devices that function similarly to
the physical disks in a desktop or a server. Compute Engine manages the
hardware behind these devices to ensure data redundancy and optimize
performance for you. Persistent disks are available as either standard
hard disk drives (HDD) or solid-state drives (SSD).

Persistent disks are located independently from your virtual machine
instances, so you can detach or move persistent disks to keep your data
even after you delete your instances. Persistent disk performance scales
automatically with size, so you can resize your existing persistent disks
or add more persistent disks to an instance to meet your performance and
storage space requirements.

Add a persistent disk to your instance when you need reliable and
affordable storage with consistent performance characteristics.


To get more information about Disk, see:

* [API documentation](https://cloud.google.com/compute/docs/reference/v1/disks)
* How-to Guides
    * [Adding a persistent disk](https://cloud.google.com/compute/docs/disks/add-persistent-disk)

> **Warning:** All arguments including the disk encryption key will be stored in the raw
state as plain-text.
[Read more about sensitive data in state](https://www.terraform.io/docs/state/sensitive-data.html).

## Example Usage - Disk Basic


```typescript
import * as pulumi from "@pulumi/pulumi";
import * as gcp from "@pulumi/gcp";

const defaultDisk = new gcp.compute.Disk("default", {
    image: "debian-8-jessie-v20170523",
    labels: {
        environment: "dev",
    },
    physicalBlockSizeBytes: 4096,
    type: "pd-ssd",
    zone: "us-central1-a",
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-google/blob/master/website/docs/r/compute_disk.html.markdown.



## Create a Disk Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#Disk">Disk</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#DiskArgs">DiskArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">Disk</span><span class="p">(resource_name, opts=None, </span>description=None<span class="p">, </span>disk_encryption_key=None<span class="p">, </span>image=None<span class="p">, </span>labels=None<span class="p">, </span>name=None<span class="p">, </span>physical_block_size_bytes=None<span class="p">, </span>project=None<span class="p">, </span>resource_policies=None<span class="p">, </span>size=None<span class="p">, </span>snapshot=None<span class="p">, </span>source_image_encryption_key=None<span class="p">, </span>source_snapshot_encryption_key=None<span class="p">, </span>type=None<span class="p">, </span>zone=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewDisk<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#DiskArgs">DiskArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#Disk">Disk</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.Disk.html">Disk</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.Inputs.DiskArgs.html">DiskArgs</a></span>? <span class="nx">args = null<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disk<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">Disk<wbr>Disk<wbr>Encryption<wbr>Key<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Physical<wbr>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>Resource<wbr>Policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Image<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Snapshot<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
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
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disk<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">*Disk<wbr>Disk<wbr>Encryption<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Physical<wbr>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>Resource<wbr>Policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Image<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">*Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Snapshot<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">*Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
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
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disk<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">Disk<wbr>Disk<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>physical<wbr>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>resource<wbr>Policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source<wbr>Image<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source<wbr>Snapshot<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
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
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disk_<wbr>encryption_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">Dict[Disk<wbr>Disk<wbr>Encryption<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>image</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>physical_<wbr>block_<wbr>size_<wbr>bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>resource_<wbr>policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source_<wbr>image_<wbr>encryption_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">Dict[Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source_<wbr>snapshot_<wbr>encryption_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">Dict[Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## Disk Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Disk<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">Disk<wbr>Disk<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Last<wbr>Attach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Last attach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Last<wbr>Detach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Last detach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Physical<wbr>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>Resource<wbr>Policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Image<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Image<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID value of the image used to create this disk. This value identifies the exact image that was used to create this
persistent disk. For example, if you created the persistent disk from an image that was later deleted and recreated
under the same name, the source image ID would identify the exact version of the image that was used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Snapshot<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The unique ID of the snapshot used to create this disk. This value identifies the exact snapshot that was used to create
this persistent disk. For example, if you created the persistent disk from a snapshot that was later deleted and
recreated under the same name, the source snapshot ID would identify the exact version of the snapshot that was used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Users</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}Links to the users of the disk (attached instances) in form: project/zones/zone/instances/instance
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Disk<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">*Disk<wbr>Disk<wbr>Encryption<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Last<wbr>Attach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Last attach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Last<wbr>Detach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Last detach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Physical<wbr>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>Resource<wbr>Policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Image<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">*Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Image<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID value of the image used to create this disk. This value identifies the exact image that was used to create this
persistent disk. For example, if you created the persistent disk from an image that was later deleted and recreated
under the same name, the source image ID would identify the exact version of the image that was used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Snapshot<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">*Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The unique ID of the snapshot used to create this disk. This value identifies the exact snapshot that was used to create
this persistent disk. For example, if you created the persistent disk from a snapshot that was later deleted and
recreated under the same name, the source snapshot ID would identify the exact version of the snapshot that was used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Users</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Links to the users of the disk (attached instances) in form: project/zones/zone/instances/instance
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>disk<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">Disk<wbr>Disk<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>last<wbr>Attach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Last attach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>last<wbr>Detach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Last detach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>physical<wbr>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>resource<wbr>Policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source<wbr>Image<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source<wbr>Image<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID value of the image used to create this disk. This value identifies the exact image that was used to create this
persistent disk. For example, if you created the persistent disk from an image that was later deleted and recreated
under the same name, the source image ID would identify the exact version of the image that was used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source<wbr>Snapshot<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source<wbr>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The unique ID of the snapshot used to create this disk. This value identifies the exact snapshot that was used to create
this persistent disk. For example, if you created the persistent disk from a snapshot that was later deleted and
recreated under the same name, the source snapshot ID would identify the exact version of the snapshot that was used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>users</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}Links to the users of the disk (attached instances) in form: project/zones/zone/instances/instance
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>creation_<wbr>timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>disk_<wbr>encryption_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">Dict[Disk<wbr>Disk<wbr>Encryption<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>image</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>label_<wbr>fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>last_<wbr>attach_<wbr>timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Last attach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>last_<wbr>detach_<wbr>timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Last detach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>physical_<wbr>block_<wbr>size_<wbr>bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>resource_<wbr>policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>self_<wbr>link</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source_<wbr>image_<wbr>encryption_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">Dict[Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source_<wbr>image_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID value of the image used to create this disk. This value identifies the exact image that was used to create this
persistent disk. For example, if you created the persistent disk from an image that was later deleted and recreated
under the same name, the source image ID would identify the exact version of the image that was used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source_<wbr>snapshot_<wbr>encryption_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">Dict[Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source_<wbr>snapshot_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The unique ID of the snapshot used to create this disk. This value identifies the exact snapshot that was used to create
this persistent disk. For example, if you created the persistent disk from a snapshot that was later deleted and
recreated under the same name, the source snapshot ID would identify the exact version of the snapshot that was used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>users</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Links to the users of the disk (attached instances) in form: project/zones/zone/instances/instance
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing Disk Resource

Get an existing Disk resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#DiskState">DiskState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/compute/#Disk">Disk</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>creation_timestamp=None<span class="p">, </span>description=None<span class="p">, </span>disk_encryption_key=None<span class="p">, </span>image=None<span class="p">, </span>label_fingerprint=None<span class="p">, </span>labels=None<span class="p">, </span>last_attach_timestamp=None<span class="p">, </span>last_detach_timestamp=None<span class="p">, </span>name=None<span class="p">, </span>physical_block_size_bytes=None<span class="p">, </span>project=None<span class="p">, </span>resource_policies=None<span class="p">, </span>self_link=None<span class="p">, </span>size=None<span class="p">, </span>snapshot=None<span class="p">, </span>source_image_encryption_key=None<span class="p">, </span>source_image_id=None<span class="p">, </span>source_snapshot_encryption_key=None<span class="p">, </span>source_snapshot_id=None<span class="p">, </span>type=None<span class="p">, </span>users=None<span class="p">, </span>zone=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetDisk<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#DiskState">DiskState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#Disk">Disk</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.Disk.html">Disk</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Compute.DiskState.html">DiskState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disk<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">Disk<wbr>Disk<wbr>Encryption<wbr>Key<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Last<wbr>Attach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Last attach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Last<wbr>Detach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Last detach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Physical<wbr>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>Resource<wbr>Policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Image<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Image<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID value of the image used to create this disk. This value identifies the exact image that was used to create this
persistent disk. For example, if you created the persistent disk from an image that was later deleted and recreated
under the same name, the source image ID would identify the exact version of the image that was used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Snapshot<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The unique ID of the snapshot used to create this disk. This value identifies the exact snapshot that was used to create
this persistent disk. For example, if you created the persistent disk from a snapshot that was later deleted and
recreated under the same name, the source snapshot ID would identify the exact version of the snapshot that was used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Users</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Links to the users of the disk (attached instances) in form: project/zones/zone/instances/instance
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disk<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">*Disk<wbr>Disk<wbr>Encryption<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Last<wbr>Attach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Last attach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Last<wbr>Detach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Last detach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Physical<wbr>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>Resource<wbr>Policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Image<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">*Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Image<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID value of the image used to create this disk. This value identifies the exact image that was used to create this
persistent disk. For example, if you created the persistent disk from an image that was later deleted and recreated
under the same name, the source image ID would identify the exact version of the image that was used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Snapshot<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">*Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The unique ID of the snapshot used to create this disk. This value identifies the exact snapshot that was used to create
this persistent disk. For example, if you created the persistent disk from a snapshot that was later deleted and
recreated under the same name, the source snapshot ID would identify the exact version of the snapshot that was used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Users</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Links to the users of the disk (attached instances) in form: project/zones/zone/instances/instance
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>creation<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disk<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">Disk<wbr>Disk<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>label<wbr>Fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>last<wbr>Attach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Last attach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>last<wbr>Detach<wbr>Timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Last detach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>physical<wbr>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>resource<wbr>Policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source<wbr>Image<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source<wbr>Image<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID value of the image used to create this disk. This value identifies the exact image that was used to create this
persistent disk. For example, if you created the persistent disk from an image that was later deleted and recreated
under the same name, the source image ID would identify the exact version of the image that was used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source<wbr>Snapshot<wbr>Encryption<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key?</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source<wbr>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The unique ID of the snapshot used to create this disk. This value identifies the exact snapshot that was used to create
this persistent disk. For example, if you created the persistent disk from a snapshot that was later deleted and
recreated under the same name, the source snapshot ID would identify the exact version of the snapshot that was used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>users</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Links to the users of the disk (attached instances) in form: project/zones/zone/instances/instance
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>creation_<wbr>timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Creation timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}An optional description of this resource. Provide this property when you create the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disk_<wbr>encryption_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#diskdiskencryptionkey">Dict[Disk<wbr>Disk<wbr>Encryption<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}Encrypts the disk using a customer-supplied encryption key. After you encrypt a disk with a customer-supplied key, you
must provide the same key if you use the disk later (e.g. to create a disk snapshot or an image, or to attach the disk
to a virtual machine). Customer-supplied encryption keys do not protect access to metadata of the disk. If you do not
provide an encryption key when creating the disk, then the disk will be encrypted using an automatically generated key
and you do not need to provide a key to use the disk later.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>image</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The image from which to initialize this disk. This can be one of: the image's 'self_link',
'projects/{project}/global/images/{image}', 'projects/{project}/global/images/family/{family}', 'global/images/{image}',
'global/images/family/{family}', 'family/{family}', '{project}/{family}', '{project}/{image}', '{family}', or '{image}'.
If referred by family, the images names must include the family name. If they don't, use the [google_compute_image data
source](/docs/providers/google/d/datasource_compute_image.html). For instance, the image 'centos-6-v20180104' includes
its family name 'centos-6'. These images can be referred by family name here.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>label_<wbr>fingerprint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The fingerprint used for optimistic locking of this resource. Used internally during updates.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}Labels to apply to this disk. A list of key->value pairs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>last_<wbr>attach_<wbr>timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Last attach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>last_<wbr>detach_<wbr>timestamp</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Last detach timestamp in RFC3339 text format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the resource. Provided by the client when the resource is created. The name must be 1-63 characters long, and
comply with RFC1035. Specifically, the name must be 1-63 characters long and match the regular expression
'[a-z]([-a-z0-9]*[a-z0-9])?' which means the first character must be a lowercase letter, and all following characters
must be a dash, lowercase letter, or digit, except the last character, which cannot be a dash.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>physical_<wbr>block_<wbr>size_<wbr>bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Physical block size of the persistent disk, in bytes. If not present in a request, a default value is used. Currently
supported sizes are 4096 and 16384, other sizes may be added in the future. If an unsupported value is requested, the
error message will list the supported values for the caller's project.
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
        <span>resource_<wbr>policies</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Resource policies applied to this disk for automatic snapshot creations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>self_<wbr>link</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The URI of the created resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Size of the persistent disk, specified in GB. You can specify this field when creating a persistent disk using the
'image' or 'snapshot' parameter, or specify it alone to create an empty persistent disk. If you specify this field along
with 'image' or 'snapshot', the value must not be less than the size of the image or the size of the snapshot.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>snapshot</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The source snapshot used to create this disk. You can provide this as a partial or full URL to the resource. If the
snapshot is in another project than this disk, you must supply a full URL. For example, the following are valid values:
* 'https://www.googleapis.com/compute/v1/projects/project/global/snapshots/snapshot' *
'projects/project/global/snapshots/snapshot' * 'global/snapshots/snapshot' * 'snapshot'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source_<wbr>image_<wbr>encryption_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourceimageencryptionkey">Dict[Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source image. Required if the source image is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source_<wbr>image_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID value of the image used to create this disk. This value identifies the exact image that was used to create this
persistent disk. For example, if you created the persistent disk from an image that was later deleted and recreated
under the same name, the source image ID would identify the exact version of the image that was used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source_<wbr>snapshot_<wbr>encryption_<wbr>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#disksourcesnapshotencryptionkey">Dict[Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}The customer-supplied encryption key of the source snapshot. Required if the source snapshot is protected by a
customer-supplied encryption key.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source_<wbr>snapshot_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The unique ID of the snapshot used to create this disk. This value identifies the exact snapshot that was used to create
this persistent disk. For example, if you created the persistent disk from a snapshot that was later deleted and
recreated under the same name, the source snapshot ID would identify the exact version of the snapshot that was used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}URL of the disk type resource describing which disk type to use to create the disk. Provide this when creating the disk.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>users</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Links to the users of the disk (attached instances) in form: project/zones/zone/instances/instance
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A reference to the zone where the disk resides.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Disk<wbr>Disk<wbr>Encryption<wbr>Key</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#DiskDiskEncryptionKey">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#DiskDiskEncryptionKey">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#DiskDiskEncryptionKeyArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#DiskDiskEncryptionKeyOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Disk<wbr>Source<wbr>Image<wbr>Encryption<wbr>Key</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#DiskSourceImageEncryptionKey">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#DiskSourceImageEncryptionKey">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#DiskSourceImageEncryptionKeyArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#DiskSourceImageEncryptionKeyOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Disk<wbr>Source<wbr>Snapshot<wbr>Encryption<wbr>Key</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#DiskSourceSnapshotEncryptionKey">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#DiskSourceSnapshotEncryptionKey">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#DiskSourceSnapshotEncryptionKeyArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/compute?tab=doc#DiskSourceSnapshotEncryptionKeyOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>raw<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sha256</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}







