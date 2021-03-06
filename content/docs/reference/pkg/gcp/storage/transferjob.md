
---
title: "TransferJob"
block_external_search_index: true
---

Creates a new Transfer Job in Google Cloud Storage Transfer.

To get more information about Google Cloud Storage Transfer, see:

* [Overview](https://cloud.google.com/storage-transfer/docs/overview)
* [API documentation](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/transferJobs#TransferJob)
* How-to Guides
    * [Configuring Access to Data Sources and Sinks](https://cloud.google.com/storage-transfer/docs/configure-access)

> This content is derived from https://github.com/terraform-providers/terraform-provider-google/blob/master/website/docs/r/storage_transfer_job.html.markdown.



## Create a TransferJob Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/storage/#TransferJob">TransferJob</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/storage/#TransferJobArgs">TransferJobArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">TransferJob</span><span class="p">(resource_name, opts=None, </span>description=None<span class="p">, </span>project=None<span class="p">, </span>schedule=None<span class="p">, </span>status=None<span class="p">, </span>transfer_spec=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewTransferJob<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobArgs">TransferJobArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJob">TransferJob</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Storage.TransferJob.html">TransferJob</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Storage.Inputs.TransferJobArgs.html">TransferJobArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Transfer<wbr>Job<wbr>Schedule<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Transfer<wbr>Spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Transfer<wbr>Job<wbr>Schedule</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Transfer<wbr>Spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Transfer<wbr>Job<wbr>Transfer<wbr>Spec</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Transfer<wbr>Job<wbr>Schedule</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>transfer<wbr>Spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Transfer<wbr>Job<wbr>Transfer<wbr>Spec</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Dict[Transfer<wbr>Job<wbr>Schedule]</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>transfer_<wbr>spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Dict[Transfer<wbr>Job<wbr>Transfer<wbr>Spec]</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## TransferJob Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Creation<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Deletion<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was deleted.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Last<wbr>Modification<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was last modified.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Transfer<wbr>Job<wbr>Schedule</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Transfer<wbr>Spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Transfer<wbr>Job<wbr>Transfer<wbr>Spec</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Creation<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Deletion<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was deleted.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Last<wbr>Modification<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was last modified.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Transfer<wbr>Job<wbr>Schedule</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Transfer<wbr>Spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Transfer<wbr>Job<wbr>Transfer<wbr>Spec</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>creation<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>deletion<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was deleted.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>last<wbr>Modification<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was last modified.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Transfer<wbr>Job<wbr>Schedule</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>transfer<wbr>Spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Transfer<wbr>Job<wbr>Transfer<wbr>Spec</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>creation_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>deletion_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was deleted.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>last_<wbr>modification_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was last modified.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Dict[Transfer<wbr>Job<wbr>Schedule]</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>transfer_<wbr>spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Dict[Transfer<wbr>Job<wbr>Transfer<wbr>Spec]</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing TransferJob Resource

Get an existing TransferJob resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/storage/#TransferJobState">TransferJobState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/storage/#TransferJob">TransferJob</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>creation_time=None<span class="p">, </span>deletion_time=None<span class="p">, </span>description=None<span class="p">, </span>last_modification_time=None<span class="p">, </span>name=None<span class="p">, </span>project=None<span class="p">, </span>schedule=None<span class="p">, </span>status=None<span class="p">, </span>transfer_spec=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetTransferJob<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobState">TransferJobState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJob">TransferJob</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Storage.TransferJob.html">TransferJob</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Storage.TransferJobState.html">TransferJobState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Creation<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Deletion<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was deleted.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Last<wbr>Modification<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was last modified.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Transfer<wbr>Job<wbr>Schedule<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Transfer<wbr>Spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Creation<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Deletion<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was deleted.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Last<wbr>Modification<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was last modified.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Project</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">*Transfer<wbr>Job<wbr>Schedule</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Transfer<wbr>Spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">*Transfer<wbr>Job<wbr>Transfer<wbr>Spec</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>creation<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>deletion<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was deleted.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>last<wbr>Modification<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was last modified.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Transfer<wbr>Job<wbr>Schedule?</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>transfer<wbr>Spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Transfer<wbr>Job<wbr>Transfer<wbr>Spec?</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>creation_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>deletion_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was deleted.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Unique description to identify the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>last_<wbr>modification_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}When the Transfer Job was last modified.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the Transfer Job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>project</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The project in which the resource belongs. If it
is not provided, the provider project is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedule">Dict[Transfer<wbr>Job<wbr>Schedule]</a></span>
    </dt>
    <dd>{{% md %}}Schedule specification defining when the Transfer Job should be scheduled to start, end and and what time to run. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Status of the job. Default: `ENABLED`. **NOTE: The effect of the new job status takes place during a subsequent job run. For example, if you change the job status from ENABLED to DISABLED, and an operation spawned by the transfer is running, the status change would not affect the current operation.**
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>transfer_<wbr>spec</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspec">Dict[Transfer<wbr>Job<wbr>Transfer<wbr>Spec]</a></span>
    </dt>
    <dd>{{% md %}}Transfer specification. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Transfer<wbr>Job<wbr>Schedule</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobSchedule">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobSchedule">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobScheduleArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobScheduleOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Schedule<wbr>End<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedulescheduleenddate">Transfer<wbr>Job<wbr>Schedule<wbr>Schedule<wbr>End<wbr>Date<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The last day the recurring transfer will be run. If `schedule_end_date` is the same as `schedule_start_date`, the transfer will be executed only once. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Schedule<wbr>Start<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobscheduleschedulestartdate">Transfer<wbr>Job<wbr>Schedule<wbr>Schedule<wbr>Start<wbr>Date<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}The first day the recurring transfer is scheduled to run. If `schedule_start_date` is in the past, the transfer will run for the first time on the following day. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Start<wbr>Time<wbr>Of<wbr>Day</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedulestarttimeofday">Transfer<wbr>Job<wbr>Schedule<wbr>Start<wbr>Time<wbr>Of<wbr>Day<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The time in UTC at which the transfer will be scheduled to start in a day. Transfers may start later than this time. If not specified, recurring and one-time transfers that are scheduled to run today will run immediately; recurring transfers that are scheduled to run on a future date will start at approximately midnight UTC on that date. Note that when configuring a transfer with the Cloud Platform Console, the transfer's start time in a day is specified in your local timezone. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Schedule<wbr>End<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedulescheduleenddate">*Transfer<wbr>Job<wbr>Schedule<wbr>Schedule<wbr>End<wbr>Date</a></span>
    </dt>
    <dd>{{% md %}}The last day the recurring transfer will be run. If `schedule_end_date` is the same as `schedule_start_date`, the transfer will be executed only once. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Schedule<wbr>Start<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobscheduleschedulestartdate">Transfer<wbr>Job<wbr>Schedule<wbr>Schedule<wbr>Start<wbr>Date</a></span>
    </dt>
    <dd>{{% md %}}The first day the recurring transfer is scheduled to run. If `schedule_start_date` is in the past, the transfer will run for the first time on the following day. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Start<wbr>Time<wbr>Of<wbr>Day</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedulestarttimeofday">*Transfer<wbr>Job<wbr>Schedule<wbr>Start<wbr>Time<wbr>Of<wbr>Day</a></span>
    </dt>
    <dd>{{% md %}}The time in UTC at which the transfer will be scheduled to start in a day. Transfers may start later than this time. If not specified, recurring and one-time transfers that are scheduled to run today will run immediately; recurring transfers that are scheduled to run on a future date will start at approximately midnight UTC on that date. Note that when configuring a transfer with the Cloud Platform Console, the transfer's start time in a day is specified in your local timezone. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>schedule<wbr>End<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedulescheduleenddate">Transfer<wbr>Job<wbr>Schedule<wbr>Schedule<wbr>End<wbr>Date?</a></span>
    </dt>
    <dd>{{% md %}}The last day the recurring transfer will be run. If `schedule_end_date` is the same as `schedule_start_date`, the transfer will be executed only once. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>schedule<wbr>Start<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobscheduleschedulestartdate">Transfer<wbr>Job<wbr>Schedule<wbr>Schedule<wbr>Start<wbr>Date</a></span>
    </dt>
    <dd>{{% md %}}The first day the recurring transfer is scheduled to run. If `schedule_start_date` is in the past, the transfer will run for the first time on the following day. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>start<wbr>Time<wbr>Of<wbr>Day</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedulestarttimeofday">Transfer<wbr>Job<wbr>Schedule<wbr>Start<wbr>Time<wbr>Of<wbr>Day?</a></span>
    </dt>
    <dd>{{% md %}}The time in UTC at which the transfer will be scheduled to start in a day. Transfers may start later than this time. If not specified, recurring and one-time transfers that are scheduled to run today will run immediately; recurring transfers that are scheduled to run on a future date will start at approximately midnight UTC on that date. Note that when configuring a transfer with the Cloud Platform Console, the transfer's start time in a day is specified in your local timezone. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>schedule<wbr>End<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedulescheduleenddate">Dict[Transfer<wbr>Job<wbr>Schedule<wbr>Schedule<wbr>End<wbr>Date]</a></span>
    </dt>
    <dd>{{% md %}}The last day the recurring transfer will be run. If `schedule_end_date` is the same as `schedule_start_date`, the transfer will be executed only once. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>schedule<wbr>Start<wbr>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobscheduleschedulestartdate">Dict[Transfer<wbr>Job<wbr>Schedule<wbr>Schedule<wbr>Start<wbr>Date]</a></span>
    </dt>
    <dd>{{% md %}}The first day the recurring transfer is scheduled to run. If `schedule_start_date` is in the past, the transfer will run for the first time on the following day. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>start<wbr>Time<wbr>Of<wbr>Day</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobschedulestarttimeofday">Dict[Transfer<wbr>Job<wbr>Schedule<wbr>Start<wbr>Time<wbr>Of<wbr>Day]</a></span>
    </dt>
    <dd>{{% md %}}The time in UTC at which the transfer will be scheduled to start in a day. Transfers may start later than this time. If not specified, recurring and one-time transfers that are scheduled to run today will run immediately; recurring transfers that are scheduled to run on a future date will start at approximately midnight UTC on that date. Note that when configuring a transfer with the Cloud Platform Console, the transfer's start time in a day is specified in your local timezone. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Schedule<wbr>Schedule<wbr>End<wbr>Date</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobScheduleScheduleEndDate">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobScheduleScheduleEndDate">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobScheduleScheduleEndDateArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobScheduleScheduleEndDateOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Day</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Day of month. Must be from 1 to 31 and valid for the year and month.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Month</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Month of year. Must be from 1 to 12.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Year</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Year of date. Must be from 1 to 9999.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Day</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Day of month. Must be from 1 to 31 and valid for the year and month.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Month</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Month of year. Must be from 1 to 12.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Year</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Year of date. Must be from 1 to 9999.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>day</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Day of month. Must be from 1 to 31 and valid for the year and month.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>month</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Month of year. Must be from 1 to 12.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>year</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Year of date. Must be from 1 to 9999.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>day</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Day of month. Must be from 1 to 31 and valid for the year and month.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>month</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Month of year. Must be from 1 to 12.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>year</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Year of date. Must be from 1 to 9999.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Schedule<wbr>Schedule<wbr>Start<wbr>Date</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobScheduleScheduleStartDate">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobScheduleScheduleStartDate">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobScheduleScheduleStartDateArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobScheduleScheduleStartDateOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Day</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Day of month. Must be from 1 to 31 and valid for the year and month.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Month</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Month of year. Must be from 1 to 12.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Year</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Year of date. Must be from 1 to 9999.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Day</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Day of month. Must be from 1 to 31 and valid for the year and month.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Month</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Month of year. Must be from 1 to 12.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Year</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Year of date. Must be from 1 to 9999.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>day</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Day of month. Must be from 1 to 31 and valid for the year and month.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>month</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Month of year. Must be from 1 to 12.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>year</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Year of date. Must be from 1 to 9999.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>day</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Day of month. Must be from 1 to 31 and valid for the year and month.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>month</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Month of year. Must be from 1 to 12.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>year</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Year of date. Must be from 1 to 9999.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Schedule<wbr>Start<wbr>Time<wbr>Of<wbr>Day</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobScheduleStartTimeOfDay">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobScheduleStartTimeOfDay">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobScheduleStartTimeOfDayArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobScheduleStartTimeOfDayOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Hours of day in 24 hour format. Should be from 0 to 23
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Minutes of hour of day. Must be from 0 to 59.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Nanos</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Fractions of seconds in nanoseconds. Must be from 0 to 999,999,999.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Seconds</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Seconds of minutes of the time. Must normally be from 0 to 59.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Hours of day in 24 hour format. Should be from 0 to 23
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Minutes of hour of day. Must be from 0 to 59.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Nanos</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Fractions of seconds in nanoseconds. Must be from 0 to 999,999,999.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Seconds</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}Seconds of minutes of the time. Must normally be from 0 to 59.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Hours of day in 24 hour format. Should be from 0 to 23
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Minutes of hour of day. Must be from 0 to 59.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>nanos</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Fractions of seconds in nanoseconds. Must be from 0 to 999,999,999.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>seconds</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}Seconds of minutes of the time. Must normally be from 0 to 59.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Hours of day in 24 hour format. Should be from 0 to 23
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Minutes of hour of day. Must be from 0 to 59.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>nanos</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Fractions of seconds in nanoseconds. Must be from 0 to 999,999,999.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>seconds</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Seconds of minutes of the time. Must normally be from 0 to 59.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Transfer<wbr>Spec</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobTransferSpec">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobTransferSpec">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Aws<wbr>S3Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecawss3datasource">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Aws<wbr>S3Data<wbr>Source<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}An AWS S3 data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Gcs<wbr>Data<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecgcsdatasink">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Gcs<wbr>Data<wbr>Sink<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A Google Cloud Storage data sink. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Gcs<wbr>Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecgcsdatasource">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Gcs<wbr>Data<wbr>Source<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A Google Cloud Storage data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Http<wbr>Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspechttpdatasource">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Http<wbr>Data<wbr>Source<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}An HTTP URL data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Object<wbr>Conditions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecobjectconditions">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Object<wbr>Conditions<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Only objects that satisfy these object conditions are included in the set of data source and data sink objects. Object conditions based on objects' `last_modification_time` do not exclude objects in a data sink. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Transfer<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspectransferoptions">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Transfer<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Characteristics of how to treat files from datasource and sink during job. If the option `delete_objects_unique_in_sink` is true, object conditions based on objects' `last_modification_time` are ignored and do not exclude objects in a data source or a data sink. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Aws<wbr>S3Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecawss3datasource">*Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Aws<wbr>S3Data<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}An AWS S3 data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Gcs<wbr>Data<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecgcsdatasink">*Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Gcs<wbr>Data<wbr>Sink</a></span>
    </dt>
    <dd>{{% md %}}A Google Cloud Storage data sink. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Gcs<wbr>Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecgcsdatasource">*Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Gcs<wbr>Data<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}A Google Cloud Storage data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Http<wbr>Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspechttpdatasource">*Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Http<wbr>Data<wbr>Source</a></span>
    </dt>
    <dd>{{% md %}}An HTTP URL data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Object<wbr>Conditions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecobjectconditions">*Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Object<wbr>Conditions</a></span>
    </dt>
    <dd>{{% md %}}Only objects that satisfy these object conditions are included in the set of data source and data sink objects. Object conditions based on objects' `last_modification_time` do not exclude objects in a data sink. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Transfer<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspectransferoptions">*Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Transfer<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}Characteristics of how to treat files from datasource and sink during job. If the option `delete_objects_unique_in_sink` is true, object conditions based on objects' `last_modification_time` are ignored and do not exclude objects in a data source or a data sink. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>aws<wbr>S3Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecawss3datasource">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Aws<wbr>S3Data<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}An AWS S3 data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>gcs<wbr>Data<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecgcsdatasink">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Gcs<wbr>Data<wbr>Sink?</a></span>
    </dt>
    <dd>{{% md %}}A Google Cloud Storage data sink. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>gcs<wbr>Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecgcsdatasource">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Gcs<wbr>Data<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}A Google Cloud Storage data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>http<wbr>Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspechttpdatasource">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Http<wbr>Data<wbr>Source?</a></span>
    </dt>
    <dd>{{% md %}}An HTTP URL data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>object<wbr>Conditions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecobjectconditions">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Object<wbr>Conditions?</a></span>
    </dt>
    <dd>{{% md %}}Only objects that satisfy these object conditions are included in the set of data source and data sink objects. Object conditions based on objects' `last_modification_time` do not exclude objects in a data sink. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>transfer<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspectransferoptions">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Transfer<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}Characteristics of how to treat files from datasource and sink during job. If the option `delete_objects_unique_in_sink` is true, object conditions based on objects' `last_modification_time` are ignored and do not exclude objects in a data source or a data sink. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>aws<wbr>S3Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecawss3datasource">Dict[Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Aws<wbr>S3Data<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}An AWS S3 data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>gcs<wbr>Data<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecgcsdatasink">Dict[Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Gcs<wbr>Data<wbr>Sink]</a></span>
    </dt>
    <dd>{{% md %}}A Google Cloud Storage data sink. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>gcs<wbr>Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecgcsdatasource">Dict[Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Gcs<wbr>Data<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}A Google Cloud Storage data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>http<wbr>Data<wbr>Source</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspechttpdatasource">Dict[Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Http<wbr>Data<wbr>Source]</a></span>
    </dt>
    <dd>{{% md %}}An HTTP URL data source. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>object<wbr>Conditions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecobjectconditions">Dict[Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Object<wbr>Conditions]</a></span>
    </dt>
    <dd>{{% md %}}Only objects that satisfy these object conditions are included in the set of data source and data sink objects. Object conditions based on objects' `last_modification_time` do not exclude objects in a data sink. Structure documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>transfer<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspectransferoptions">Dict[Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Transfer<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}Characteristics of how to treat files from datasource and sink during job. If the option `delete_objects_unique_in_sink` is true, object conditions based on objects' `last_modification_time` are ignored and do not exclude objects in a data source or a data sink. Structure documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Aws<wbr>S3Data<wbr>Source</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobTransferSpecAwsS3DataSource">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobTransferSpecAwsS3DataSource">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecAwsS3DataSourceArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecAwsS3DataSourceOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Aws<wbr>Access<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecawss3datasourceawsaccesskey">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Aws<wbr>S3Data<wbr>Source<wbr>Aws<wbr>Access<wbr>Key<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}AWS credentials block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Aws<wbr>Access<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecawss3datasourceawsaccesskey">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Aws<wbr>S3Data<wbr>Source<wbr>Aws<wbr>Access<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}AWS credentials block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>aws<wbr>Access<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecawss3datasourceawsaccesskey">Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Aws<wbr>S3Data<wbr>Source<wbr>Aws<wbr>Access<wbr>Key</a></span>
    </dt>
    <dd>{{% md %}}AWS credentials block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>aws<wbr>Access<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#transferjobtransferspecawss3datasourceawsaccesskey">Dict[Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Aws<wbr>S3Data<wbr>Source<wbr>Aws<wbr>Access<wbr>Key]</a></span>
    </dt>
    <dd>{{% md %}}AWS credentials block.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>bucket_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Aws<wbr>S3Data<wbr>Source<wbr>Aws<wbr>Access<wbr>Key</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobTransferSpecAwsS3DataSourceAwsAccessKey">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobTransferSpecAwsS3DataSourceAwsAccessKey">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecAwsS3DataSourceAwsAccessKeyArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecAwsS3DataSourceAwsAccessKeyOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Access<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}AWS Key ID.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Secret<wbr>Access<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}AWS Secret Access Key.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Access<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}AWS Key ID.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Secret<wbr>Access<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}AWS Secret Access Key.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>access<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}AWS Key ID.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>secret<wbr>Access<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}AWS Secret Access Key.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>access<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}AWS Key ID.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>secret<wbr>Access<wbr>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}AWS Secret Access Key.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Gcs<wbr>Data<wbr>Sink</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobTransferSpecGcsDataSink">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobTransferSpecGcsDataSink">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecGcsDataSinkArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecGcsDataSinkOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Gcs<wbr>Data<wbr>Source</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobTransferSpecGcsDataSource">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobTransferSpecGcsDataSource">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecGcsDataSourceArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecGcsDataSourceOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}S3 Bucket name.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Http<wbr>Data<wbr>Source</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobTransferSpecHttpDataSource">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobTransferSpecHttpDataSource">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecHttpDataSourceArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecHttpDataSourceOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>List<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URL that points to the file that stores the object list entries. This file must allow public access. Currently, only URLs with HTTP and HTTPS schemes are supported.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>List<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URL that points to the file that stores the object list entries. This file must allow public access. Currently, only URLs with HTTP and HTTPS schemes are supported.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>list<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The URL that points to the file that stores the object list entries. This file must allow public access. Currently, only URLs with HTTP and HTTPS schemes are supported.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>list<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The URL that points to the file that stores the object list entries. This file must allow public access. Currently, only URLs with HTTP and HTTPS schemes are supported.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Object<wbr>Conditions</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobTransferSpecObjectConditions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobTransferSpecObjectConditions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecObjectConditionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecObjectConditionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Exclude<wbr>Prefixes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}`exclude_prefixes` must follow the requirements described for `include_prefixes`. See [Requirements](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#ObjectConditions).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Include<wbr>Prefixes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}If `include_refixes` is specified, objects that satisfy the object conditions must have names that start with one of the `include_prefixes` and that do not start with any of the `exclude_prefixes`. If `include_prefixes` is not specified, all objects except those that have names starting with one of the `exclude_prefixes` must satisfy the object conditions. See [Requirements](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#ObjectConditions).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Max<wbr>Time<wbr>Elapsed<wbr>Since<wbr>Last<wbr>Modification</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A duration in seconds with up to nine fractional digits, terminated by 's'. Example: "3.5s".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Min<wbr>Time<wbr>Elapsed<wbr>Since<wbr>Last<wbr>Modification</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}
A duration in seconds with up to nine fractional digits, terminated by 's'. Example: "3.5s".
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Exclude<wbr>Prefixes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}`exclude_prefixes` must follow the requirements described for `include_prefixes`. See [Requirements](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#ObjectConditions).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Include<wbr>Prefixes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}If `include_refixes` is specified, objects that satisfy the object conditions must have names that start with one of the `include_prefixes` and that do not start with any of the `exclude_prefixes`. If `include_prefixes` is not specified, all objects except those that have names starting with one of the `exclude_prefixes` must satisfy the object conditions. See [Requirements](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#ObjectConditions).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Max<wbr>Time<wbr>Elapsed<wbr>Since<wbr>Last<wbr>Modification</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A duration in seconds with up to nine fractional digits, terminated by 's'. Example: "3.5s".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Min<wbr>Time<wbr>Elapsed<wbr>Since<wbr>Last<wbr>Modification</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}
A duration in seconds with up to nine fractional digits, terminated by 's'. Example: "3.5s".
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>exclude<wbr>Prefixes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}`exclude_prefixes` must follow the requirements described for `include_prefixes`. See [Requirements](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#ObjectConditions).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>include<wbr>Prefixes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}If `include_refixes` is specified, objects that satisfy the object conditions must have names that start with one of the `include_prefixes` and that do not start with any of the `exclude_prefixes`. If `include_prefixes` is not specified, all objects except those that have names starting with one of the `exclude_prefixes` must satisfy the object conditions. See [Requirements](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#ObjectConditions).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>max<wbr>Time<wbr>Elapsed<wbr>Since<wbr>Last<wbr>Modification</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A duration in seconds with up to nine fractional digits, terminated by 's'. Example: "3.5s".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>min<wbr>Time<wbr>Elapsed<wbr>Since<wbr>Last<wbr>Modification</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}
A duration in seconds with up to nine fractional digits, terminated by 's'. Example: "3.5s".
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>exclude<wbr>Prefixes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}`exclude_prefixes` must follow the requirements described for `include_prefixes`. See [Requirements](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#ObjectConditions).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>include<wbr>Prefixes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}If `include_refixes` is specified, objects that satisfy the object conditions must have names that start with one of the `include_prefixes` and that do not start with any of the `exclude_prefixes`. If `include_prefixes` is not specified, all objects except those that have names starting with one of the `exclude_prefixes` must satisfy the object conditions. See [Requirements](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/TransferSpec#ObjectConditions).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>max<wbr>Time<wbr>Elapsed<wbr>Since<wbr>Last<wbr>Modification</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A duration in seconds with up to nine fractional digits, terminated by 's'. Example: "3.5s".
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>min<wbr>Time<wbr>Elapsed<wbr>Since<wbr>Last<wbr>Modification</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}
A duration in seconds with up to nine fractional digits, terminated by 's'. Example: "3.5s".
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Transfer<wbr>Job<wbr>Transfer<wbr>Spec<wbr>Transfer<wbr>Options</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TransferJobTransferSpecTransferOptions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TransferJobTransferSpecTransferOptions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecTransferOptionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/storage?tab=doc#TransferJobTransferSpecTransferOptionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Objects<wbr>From<wbr>Source<wbr>After<wbr>Transfer</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Whether objects should be deleted from the source after they are transferred to the sink. Note that this option and `delete_objects_unique_in_sink` are mutually exclusive.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Objects<wbr>Unique<wbr>In<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Whether objects that exist only in the sink should be deleted. Note that this option and
`delete_objects_from_source_after_transfer` are mutually exclusive.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Overwrite<wbr>Objects<wbr>Already<wbr>Existing<wbr>In<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Whether overwriting objects that already exist in the sink is allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Objects<wbr>From<wbr>Source<wbr>After<wbr>Transfer</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Whether objects should be deleted from the source after they are transferred to the sink. Note that this option and `delete_objects_unique_in_sink` are mutually exclusive.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Objects<wbr>Unique<wbr>In<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Whether objects that exist only in the sink should be deleted. Note that this option and
`delete_objects_from_source_after_transfer` are mutually exclusive.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Overwrite<wbr>Objects<wbr>Already<wbr>Existing<wbr>In<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Whether overwriting objects that already exist in the sink is allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>delete<wbr>Objects<wbr>From<wbr>Source<wbr>After<wbr>Transfer</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Whether objects should be deleted from the source after they are transferred to the sink. Note that this option and `delete_objects_unique_in_sink` are mutually exclusive.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delete<wbr>Objects<wbr>Unique<wbr>In<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Whether objects that exist only in the sink should be deleted. Note that this option and
`delete_objects_from_source_after_transfer` are mutually exclusive.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>overwrite<wbr>Objects<wbr>Already<wbr>Existing<wbr>In<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Whether overwriting objects that already exist in the sink is allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>delete<wbr>Objects<wbr>From<wbr>Source<wbr>After<wbr>Transfer</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Whether objects should be deleted from the source after they are transferred to the sink. Note that this option and `delete_objects_unique_in_sink` are mutually exclusive.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delete<wbr>Objects<wbr>Unique<wbr>In<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Whether objects that exist only in the sink should be deleted. Note that this option and
`delete_objects_from_source_after_transfer` are mutually exclusive.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>overwrite<wbr>Objects<wbr>Already<wbr>Existing<wbr>In<wbr>Sink</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Whether overwriting objects that already exist in the sink is allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







