
---
title: "TriggerSchedule"
block_external_search_index: true
---

Manages a Trigger Schedule inside a Azure Data Factory.

> This content is derived from https://github.com/terraform-providers/terraform-provider-azurerm/blob/master/website/docs/r/data_factory_trigger_schedule.html.markdown.



## Create a TriggerSchedule Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/datafactory/#TriggerSchedule">TriggerSchedule</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/datafactory/#TriggerScheduleArgs">TriggerScheduleArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">TriggerSchedule</span><span class="p">(resource_name, opts=None, </span>annotations=None<span class="p">, </span>data_factory_name=None<span class="p">, </span>end_time=None<span class="p">, </span>frequency=None<span class="p">, </span>interval=None<span class="p">, </span>name=None<span class="p">, </span>pipeline_name=None<span class="p">, </span>pipeline_parameters=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>start_time=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewTriggerSchedule<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/datafactory?tab=doc#TriggerScheduleArgs">TriggerScheduleArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/datafactory?tab=doc#TriggerSchedule">TriggerSchedule</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Datafactory.TriggerSchedule.html">TriggerSchedule</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.DataFactory.Inputs.TriggerScheduleArgs.html">TriggerScheduleArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Data<wbr>Factory<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Pipeline<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Pipeline<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Data<wbr>Factory<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Pipeline<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Pipeline<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>data<wbr>Factory<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>end<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>pipeline<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>pipeline<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>data_<wbr>factory_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>end_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>pipeline_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>pipeline_<wbr>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>start_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## TriggerSchedule Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Data<wbr>Factory<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Pipeline<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Pipeline<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Data<wbr>Factory<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Pipeline<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Pipeline<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>data<wbr>Factory<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>end<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>pipeline<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>pipeline<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>data_<wbr>factory_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>end_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>pipeline_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>pipeline_<wbr>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>start_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing TriggerSchedule Resource

Get an existing TriggerSchedule resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/datafactory/#TriggerScheduleState">TriggerScheduleState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/azure/datafactory/#TriggerSchedule">TriggerSchedule</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>annotations=None<span class="p">, </span>data_factory_name=None<span class="p">, </span>end_time=None<span class="p">, </span>frequency=None<span class="p">, </span>interval=None<span class="p">, </span>name=None<span class="p">, </span>pipeline_name=None<span class="p">, </span>pipeline_parameters=None<span class="p">, </span>resource_group_name=None<span class="p">, </span>start_time=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetTriggerSchedule<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/datafactory?tab=doc#TriggerScheduleState">TriggerScheduleState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-azure/sdk/go/azure/datafactory?tab=doc#TriggerSchedule">TriggerSchedule</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Datafactory.TriggerSchedule.html">TriggerSchedule</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Azure/Pulumi.Azure.Datafactory.TriggerScheduleState.html">TriggerScheduleState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Data<wbr>Factory<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Pipeline<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Pipeline<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Data<wbr>Factory<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Pipeline<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Pipeline<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>data<wbr>Factory<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>end<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>pipeline<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>pipeline<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>annotations</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of tags that can be used for describing the Data Factory Schedule Trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>data_<wbr>factory_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Data Factory name in which to associate the Schedule Trigger with. Changing this forces a new resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>end_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger should end. The time will be represented in UTC.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>frequency</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The trigger freqency. Valid values include `Minute`, `Hour`, `Day`, `Week`, `Month`. Defaults to `Minute`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The interval for how often the trigger occurs. This defaults to 1.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the Data Factory Schedule Trigger. Changing this forces a new resource to be created. Must be globally unique. See the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/data-factory/naming-rules) for all restrictions.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>pipeline_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Data Factory Pipeline name that the trigger will act on.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>pipeline_<wbr>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}The pipeline parameters that the trigger will act upon.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the resource group in which to create the Data Factory Schedule Trigger. Changing this forces a new resource
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>start_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The time the Schedule Trigger will start. This defaults to the current time. The time will be represented in UTC.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}









