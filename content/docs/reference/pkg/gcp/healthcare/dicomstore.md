
---
title: "DicomStore"
block_external_search_index: true
---

A DicomStore is a datastore inside a Healthcare dataset that conforms to the DICOM
(https://www.dicomstandard.org/about/) standard for Healthcare information exchange

To get more information about DicomStore, see:

* [API documentation](https://cloud.google.com/healthcare/docs/reference/rest/v1beta1/projects.locations.datasets.dicomStores)
* How-to Guides
    * [Creating a DICOM store](https://cloud.google.com/healthcare/docs/how-tos/dicom)

> This content is derived from https://github.com/terraform-providers/terraform-provider-google/blob/master/website/docs/r/healthcare_dicom_store.html.markdown.



## Create a DicomStore Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/healthcare/#DicomStore">DicomStore</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/healthcare/#DicomStoreArgs">DicomStoreArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">DicomStore</span><span class="p">(resource_name, opts=None, </span>dataset=None<span class="p">, </span>labels=None<span class="p">, </span>name=None<span class="p">, </span>notification_config=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewDicomStore<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/healthcare?tab=doc#DicomStoreArgs">DicomStoreArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/healthcare?tab=doc#DicomStore">DicomStore</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Healthcare.DicomStore.html">DicomStore</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Healthcare.Inputs.DicomStoreArgs.html">DicomStoreArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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

    <dt class="property-required"
            title="Required">
        <span>Dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Notification<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">Dicom<wbr>Store<wbr>Notification<wbr>Config<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Notification<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">*Dicom<wbr>Store<wbr>Notification<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>notification<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">Dicom<wbr>Store<wbr>Notification<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>notification_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">Dict[Dicom<wbr>Store<wbr>Notification<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## DicomStore Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Notification<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">Dicom<wbr>Store<wbr>Notification<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The fully qualified name of this dataset
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Notification<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">*Dicom<wbr>Store<wbr>Notification<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The fully qualified name of this dataset
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>notification<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">Dicom<wbr>Store<wbr>Notification<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The fully qualified name of this dataset
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>notification_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">Dict[Dicom<wbr>Store<wbr>Notification<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>self_<wbr>link</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The fully qualified name of this dataset
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing DicomStore Resource

Get an existing DicomStore resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/healthcare/#DicomStoreState">DicomStoreState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/healthcare/#DicomStore">DicomStore</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>dataset=None<span class="p">, </span>labels=None<span class="p">, </span>name=None<span class="p">, </span>notification_config=None<span class="p">, </span>self_link=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetDicomStore<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/healthcare?tab=doc#DicomStoreState">DicomStoreState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/healthcare?tab=doc#DicomStore">DicomStore</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Healthcare.DicomStore.html">DicomStore</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Healthcare.DicomStoreState.html">DicomStoreState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Notification<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">Dicom<wbr>Store<wbr>Notification<wbr>Config<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The fully qualified name of this dataset
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Notification<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">*Dicom<wbr>Store<wbr>Notification<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The fully qualified name of this dataset
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>notification<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">Dicom<wbr>Store<wbr>Notification<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>self<wbr>Link</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The fully qualified name of this dataset
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>dataset</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Identifies the dataset addressed by this request. Must be in the format
'projects/{project}/locations/{location}/datasets/{dataset}'
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}User-supplied key-value pairs used to organize DICOM stores. Label keys must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}][\p{Ll}\p{Lo}\p{N}_-]{0,62} Label values are optional, must be between 1 and 63 characters long, have a
UTF-8 encoding of maximum 128 bytes, and must conform to the following PCRE regular expression:
[\p{Ll}\p{Lo}\p{N}_-]{0,63} No more than 64 labels can be associated with a given store. An object containing a list of
"key": value pairs. Example: { "name": "wrench", "mass": "1.3kg", "count": "3" }.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The resource name for the DicomStore. ** Changing this property may recreate the Dicom store (removing all data) **
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>notification_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#dicomstorenotificationconfig">Dict[Dicom<wbr>Store<wbr>Notification<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A nested object resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>self_<wbr>link</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The fully qualified name of this dataset
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Dicom<wbr>Store<wbr>Notification<wbr>Config</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#DicomStoreNotificationConfig">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#DicomStoreNotificationConfig">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/healthcare?tab=doc#DicomStoreNotificationConfigArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/healthcare?tab=doc#DicomStoreNotificationConfigOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Pubsub<wbr>Topic</span>
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
        <span>Pubsub<wbr>Topic</span>
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
        <span>pubsub<wbr>Topic</span>
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
        <span>pubsub<wbr>Topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}







