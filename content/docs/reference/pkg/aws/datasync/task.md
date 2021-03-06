
---
title: "Task"
block_external_search_index: true
---

Manages an AWS DataSync Task, which represents a configuration for synchronization. Starting an execution of these DataSync Tasks (actually synchronizing files) is performed outside of this resource.

## Example Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const example = new aws.datasync.Task("example", {
    destinationLocationArn: aws_datasync_location_s3_destination.arn,
    options: {
        bytesPerSecond: -1,
    },
    sourceLocationArn: aws_datasync_location_nfs_source.arn,
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/datasync_task.html.markdown.



## Create a Task Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/datasync/#Task">Task</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/datasync/#TaskArgs">TaskArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">Task</span><span class="p">(resource_name, opts=None, </span>cloudwatch_log_group_arn=None<span class="p">, </span>destination_location_arn=None<span class="p">, </span>name=None<span class="p">, </span>options=None<span class="p">, </span>source_location_arn=None<span class="p">, </span>tags=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewTask<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/datasync?tab=doc#TaskArgs">TaskArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/datasync?tab=doc#Task">Task</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Datasync.Task.html">Task</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.DataSync.Inputs.TaskArgs.html">TaskArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Cloudwatch<wbr>Log<wbr>Group<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Destination<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">Pulumi.<wbr>Aws.<wbr>Data<wbr>Sync.<wbr>Inputs.<wbr>Task<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Source<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Log<wbr>Group<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Destination<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">*Task<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Source<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Log<wbr>Group<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">ARN?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>destination<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">ARN</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">Task<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>source<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">ARN</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch_<wbr>log_<wbr>group_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>destination_<wbr>location_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">Dict[Task<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>source_<wbr>location_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## Task Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Cloudwatch<wbr>Log<wbr>Group<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Destination<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">Pulumi.<wbr>Aws.<wbr>Data<wbr>Sync.<wbr>Outputs.<wbr>Task<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Cloudwatch<wbr>Log<wbr>Group<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Destination<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">*Task<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>cloudwatch<wbr>Log<wbr>Group<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">ARN?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>destination<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">ARN</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">Task<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">ARN</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>cloudwatch_<wbr>log_<wbr>group_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>destination_<wbr>location_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">Dict[Task<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source_<wbr>location_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing Task Resource

Get an existing Task resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/datasync/#TaskState">TaskState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/datasync/#Task">Task</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>arn=None<span class="p">, </span>cloudwatch_log_group_arn=None<span class="p">, </span>destination_location_arn=None<span class="p">, </span>name=None<span class="p">, </span>options=None<span class="p">, </span>source_location_arn=None<span class="p">, </span>tags=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetTask<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/datasync?tab=doc#TaskState">TaskState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/datasync?tab=doc#Task">Task</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Datasync.Task.html">Task</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Datasync.TaskState.html">TaskState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Log<wbr>Group<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Destination<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">Pulumi.<wbr>Aws.<wbr>Data<wbr>Sync.<wbr>Inputs.<wbr>Task<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Log<wbr>Group<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Destination<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">*Task<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Log<wbr>Group<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">ARN?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>destination<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">ARN?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">Task<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source<wbr>Location<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">ARN?</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch_<wbr>log_<wbr>group_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the CloudWatch Log Group that is used to monitor and log events in the sync task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>destination_<wbr>location_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of destination DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the DataSync Task.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#taskoptions">Dict[Task<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing option that controls the default behavior when you start an execution of this DataSync Task. For each individual task execution, you can override these options by specifying an overriding configuration in those executions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source_<wbr>location_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of source DataSync Location.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Key-value pairs of resource tags to assign to the DataSync Task.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Task<wbr>Options</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#TaskOptions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#TaskOptions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/datasync?tab=doc#TaskOptionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/datasync?tab=doc#TaskOptionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Atime</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A file metadata that shows the last time a file was accessed (that is when the file was read or written to). If set to `BEST_EFFORT`, the DataSync Task attempts to preserve the original (that is, the version before sync `PREPARING` phase) `atime` attribute on all source files. Valid values: `BEST_EFFORT`, `NONE`. Default: `BEST_EFFORT`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bytes<wbr>Per<wbr>Second</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Limits the bandwidth utilized. For example, to set a maximum of 1 MB, set this value to `1048576`. Value values: `-1` or greater. Default: `-1` (unlimited).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Gid</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Group identifier of the file's owners. Valid values: `BOTH`, `INT_VALUE`, `NAME`, `NONE`. Default: `INT_VALUE` (preserve integer value of the ID).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Mtime</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A file metadata that indicates the last time a file was modified (written to) before the sync `PREPARING` phase. Value values: `NONE`, `PRESERVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Posix<wbr>Permissions</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Determines which users or groups can access a file for a specific purpose such as reading, writing, or execution of the file. Valid values: `NONE`, `PRESERVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Preserve<wbr>Deleted<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Whether files deleted in the source should be removed or preserved in the destination file system. Valid values: `PRESERVE`, `REMOVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Preserve<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Whether the DataSync Task should preserve the metadata of block and character devices in the source files system, and recreate the files with that device name and metadata on the destination. The DataSync Task can’t sync the actual contents of such devices, because many of the devices are non-terminal and don’t return an end of file (EOF) marker. Valid values: `NONE`, `PRESERVE`. Default: `NONE` (ignore special devices).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Uid</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}User identifier of the file's owners. Valid values: `BOTH`, `INT_VALUE`, `NAME`, `NONE`. Default: `INT_VALUE` (preserve integer value of the ID).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Verify<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Whether a data integrity verification should be performed at the end of a task execution after all data and metadata have been transferred. Valid values: `NONE`, `POINT_IN_TIME_CONSISTENT`. Default: `POINT_IN_TIME_CONSISTENT`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Atime</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A file metadata that shows the last time a file was accessed (that is when the file was read or written to). If set to `BEST_EFFORT`, the DataSync Task attempts to preserve the original (that is, the version before sync `PREPARING` phase) `atime` attribute on all source files. Valid values: `BEST_EFFORT`, `NONE`. Default: `BEST_EFFORT`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bytes<wbr>Per<wbr>Second</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Limits the bandwidth utilized. For example, to set a maximum of 1 MB, set this value to `1048576`. Value values: `-1` or greater. Default: `-1` (unlimited).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Gid</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Group identifier of the file's owners. Valid values: `BOTH`, `INT_VALUE`, `NAME`, `NONE`. Default: `INT_VALUE` (preserve integer value of the ID).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Mtime</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A file metadata that indicates the last time a file was modified (written to) before the sync `PREPARING` phase. Value values: `NONE`, `PRESERVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Posix<wbr>Permissions</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Determines which users or groups can access a file for a specific purpose such as reading, writing, or execution of the file. Valid values: `NONE`, `PRESERVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Preserve<wbr>Deleted<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Whether files deleted in the source should be removed or preserved in the destination file system. Valid values: `PRESERVE`, `REMOVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Preserve<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Whether the DataSync Task should preserve the metadata of block and character devices in the source files system, and recreate the files with that device name and metadata on the destination. The DataSync Task can’t sync the actual contents of such devices, because many of the devices are non-terminal and don’t return an end of file (EOF) marker. Valid values: `NONE`, `PRESERVE`. Default: `NONE` (ignore special devices).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Uid</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}User identifier of the file's owners. Valid values: `BOTH`, `INT_VALUE`, `NAME`, `NONE`. Default: `INT_VALUE` (preserve integer value of the ID).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Verify<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Whether a data integrity verification should be performed at the end of a task execution after all data and metadata have been transferred. Valid values: `NONE`, `POINT_IN_TIME_CONSISTENT`. Default: `POINT_IN_TIME_CONSISTENT`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>atime</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A file metadata that shows the last time a file was accessed (that is when the file was read or written to). If set to `BEST_EFFORT`, the DataSync Task attempts to preserve the original (that is, the version before sync `PREPARING` phase) `atime` attribute on all source files. Valid values: `BEST_EFFORT`, `NONE`. Default: `BEST_EFFORT`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bytes<wbr>Per<wbr>Second</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Limits the bandwidth utilized. For example, to set a maximum of 1 MB, set this value to `1048576`. Value values: `-1` or greater. Default: `-1` (unlimited).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>gid</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Group identifier of the file's owners. Valid values: `BOTH`, `INT_VALUE`, `NAME`, `NONE`. Default: `INT_VALUE` (preserve integer value of the ID).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>mtime</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A file metadata that indicates the last time a file was modified (written to) before the sync `PREPARING` phase. Value values: `NONE`, `PRESERVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>posix<wbr>Permissions</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Determines which users or groups can access a file for a specific purpose such as reading, writing, or execution of the file. Valid values: `NONE`, `PRESERVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>preserve<wbr>Deleted<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Whether files deleted in the source should be removed or preserved in the destination file system. Valid values: `PRESERVE`, `REMOVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>preserve<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Whether the DataSync Task should preserve the metadata of block and character devices in the source files system, and recreate the files with that device name and metadata on the destination. The DataSync Task can’t sync the actual contents of such devices, because many of the devices are non-terminal and don’t return an end of file (EOF) marker. Valid values: `NONE`, `PRESERVE`. Default: `NONE` (ignore special devices).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>uid</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}User identifier of the file's owners. Valid values: `BOTH`, `INT_VALUE`, `NAME`, `NONE`. Default: `INT_VALUE` (preserve integer value of the ID).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>verify<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Whether a data integrity verification should be performed at the end of a task execution after all data and metadata have been transferred. Valid values: `NONE`, `POINT_IN_TIME_CONSISTENT`. Default: `POINT_IN_TIME_CONSISTENT`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>atime</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A file metadata that shows the last time a file was accessed (that is when the file was read or written to). If set to `BEST_EFFORT`, the DataSync Task attempts to preserve the original (that is, the version before sync `PREPARING` phase) `atime` attribute on all source files. Valid values: `BEST_EFFORT`, `NONE`. Default: `BEST_EFFORT`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bytes<wbr>Per<wbr>Second</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Limits the bandwidth utilized. For example, to set a maximum of 1 MB, set this value to `1048576`. Value values: `-1` or greater. Default: `-1` (unlimited).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>gid</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Group identifier of the file's owners. Valid values: `BOTH`, `INT_VALUE`, `NAME`, `NONE`. Default: `INT_VALUE` (preserve integer value of the ID).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>mtime</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A file metadata that indicates the last time a file was modified (written to) before the sync `PREPARING` phase. Value values: `NONE`, `PRESERVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>posix<wbr>Permissions</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Determines which users or groups can access a file for a specific purpose such as reading, writing, or execution of the file. Valid values: `NONE`, `PRESERVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>preserve<wbr>Deleted<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Whether files deleted in the source should be removed or preserved in the destination file system. Valid values: `PRESERVE`, `REMOVE`. Default: `PRESERVE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>preserve<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Whether the DataSync Task should preserve the metadata of block and character devices in the source files system, and recreate the files with that device name and metadata on the destination. The DataSync Task can’t sync the actual contents of such devices, because many of the devices are non-terminal and don’t return an end of file (EOF) marker. Valid values: `NONE`, `PRESERVE`. Default: `NONE` (ignore special devices).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>uid</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}User identifier of the file's owners. Valid values: `BOTH`, `INT_VALUE`, `NAME`, `NONE`. Default: `INT_VALUE` (preserve integer value of the ID).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>verify<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Whether a data integrity verification should be performed at the end of a task execution after all data and metadata have been transferred. Valid values: `NONE`, `POINT_IN_TIME_CONSISTENT`. Default: `POINT_IN_TIME_CONSISTENT`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







