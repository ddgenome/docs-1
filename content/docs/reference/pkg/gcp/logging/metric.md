
---
title: "Metric"
block_external_search_index: true
---

Logs-based metric can also be used to extract values from logs and create a a distribution
of the values. The distribution records the statistics of the extracted values along with
an optional histogram of the values as specified by the bucket options.


To get more information about Metric, see:

* [API documentation](https://cloud.google.com/logging/docs/reference/v2/rest/v2/projects.metrics/create)
* How-to Guides
    * [Official Documentation](https://cloud.google.com/logging/docs/apis)

## Example Usage - Logging Metric Basic


```typescript
import * as pulumi from "@pulumi/pulumi";
import * as gcp from "@pulumi/gcp";

const loggingMetric = new gcp.logging.Metric("logging_metric", {
    bucketOptions: {
        linearBuckets: {
            numFiniteBuckets: 3,
            offset: 1,
            width: 1,
        },
    },
    filter: "resource.type=gae_app AND severity>=ERROR",
    labelExtractors: {
        mass: "EXTRACT(jsonPayload.request)",
        sku: "EXTRACT(jsonPayload.id)",
    },
    metricDescriptor: {
        displayName: "My metric",
        labels: [
            {
                description: "amount of matter",
                key: "mass",
                valueType: "STRING",
            },
            {
                description: "Identifying number for item",
                key: "sku",
                valueType: "INT64",
            },
        ],
        metricKind: "DELTA",
        unit: "1",
        valueType: "DISTRIBUTION",
    },
    valueExtractor: "EXTRACT(jsonPayload.request)",
});
```
## Example Usage - Logging Metric Counter Basic


```typescript
import * as pulumi from "@pulumi/pulumi";
import * as gcp from "@pulumi/gcp";

const loggingMetric = new gcp.logging.Metric("logging_metric", {
    filter: "resource.type=gae_app AND severity>=ERROR",
    metricDescriptor: {
        metricKind: "DELTA",
        valueType: "INT64",
    },
});
```
## Example Usage - Logging Metric Counter Labels


```typescript
import * as pulumi from "@pulumi/pulumi";
import * as gcp from "@pulumi/gcp";

const loggingMetric = new gcp.logging.Metric("logging_metric", {
    filter: "resource.type=gae_app AND severity>=ERROR",
    labelExtractors: {
        mass: "EXTRACT(jsonPayload.request)",
    },
    metricDescriptor: {
        labels: [{
            description: "amount of matter",
            key: "mass",
            valueType: "STRING",
        }],
        metricKind: "DELTA",
        valueType: "INT64",
    },
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-google/blob/master/website/docs/r/logging_metric.html.markdown.



## Create a Metric Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/logging/#Metric">Metric</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/logging/#MetricArgs">MetricArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">Metric</span><span class="p">(resource_name, opts=None, </span>bucket_options=None<span class="p">, </span>description=None<span class="p">, </span>filter=None<span class="p">, </span>label_extractors=None<span class="p">, </span>metric_descriptor=None<span class="p">, </span>name=None<span class="p">, </span>project=None<span class="p">, </span>value_extractor=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewMetric<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricArgs">MetricArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#Metric">Metric</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Logging.Metric.html">Metric</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Logging.Inputs.MetricArgs.html">MetricArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Bucket<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">Metric<wbr>Bucket<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Label<wbr>Extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Metric<wbr>Descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Metric<wbr>Metric<wbr>Descriptor<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>Value<wbr>Extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">*Metric<wbr>Bucket<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Label<wbr>Extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Metric<wbr>Descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Metric<wbr>Metric<wbr>Descriptor</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>Value<wbr>Extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>bucket<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">Metric<wbr>Bucket<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>label<wbr>Extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>metric<wbr>Descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Metric<wbr>Metric<wbr>Descriptor</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>value<wbr>Extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>bucket_<wbr>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">Dict[Metric<wbr>Bucket<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>label_<wbr>extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>metric_<wbr>descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Dict[Metric<wbr>Metric<wbr>Descriptor]</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>value_<wbr>extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## Metric Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Bucket<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">Metric<wbr>Bucket<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Label<wbr>Extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Metric<wbr>Descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Metric<wbr>Metric<wbr>Descriptor</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>Value<wbr>Extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Bucket<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">*Metric<wbr>Bucket<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Label<wbr>Extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Metric<wbr>Descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Metric<wbr>Metric<wbr>Descriptor</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>Value<wbr>Extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>bucket<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">Metric<wbr>Bucket<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>label<wbr>Extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>metric<wbr>Descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Metric<wbr>Metric<wbr>Descriptor</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>value<wbr>Extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>bucket_<wbr>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">Dict[Metric<wbr>Bucket<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>label_<wbr>extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>metric_<wbr>descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Dict[Metric<wbr>Metric<wbr>Descriptor]</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>value_<wbr>extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing Metric Resource

Get an existing Metric resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/logging/#MetricState">MetricState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/logging/#Metric">Metric</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>bucket_options=None<span class="p">, </span>description=None<span class="p">, </span>filter=None<span class="p">, </span>label_extractors=None<span class="p">, </span>metric_descriptor=None<span class="p">, </span>name=None<span class="p">, </span>project=None<span class="p">, </span>value_extractor=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetMetric<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricState">MetricState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#Metric">Metric</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Logging.Metric.html">Metric</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Logging.MetricState.html">MetricState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Bucket<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">Metric<wbr>Bucket<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Label<wbr>Extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Metric<wbr>Descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Metric<wbr>Metric<wbr>Descriptor<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>Value<wbr>Extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">*Metric<wbr>Bucket<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Label<wbr>Extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Metric<wbr>Descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">*Metric<wbr>Metric<wbr>Descriptor</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>Value<wbr>Extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>bucket<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">Metric<wbr>Bucket<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>label<wbr>Extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>metric<wbr>Descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Metric<wbr>Metric<wbr>Descriptor?</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>value<wbr>Extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>bucket_<wbr>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptions">Dict[Metric<wbr>Bucket<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}The bucketOptions are required when the logs-based metric is using a DISTRIBUTION value type and it describes the bucket
boundaries used to create a histogram of the extracted values.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A description of this metric, which is used in documentation. The maximum length of the description is 8000 characters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filter</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}An advanced logs filter (https://cloud.google.com/logging/docs/view/advanced-filters) which is used to match log
entries.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>label_<wbr>extractors</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A map from a label key string to an extractor expression which is used to extract data from a log entry field and assign
as the label value. Each label key specified in the LabelDescriptor must have an associated extractor expression in this
map. The syntax of the extractor expression is the same as for the valueExtractor field.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>metric_<wbr>descriptor</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptor">Dict[Metric<wbr>Metric<wbr>Descriptor]</a></span>
    </dt>
    <dd>{{% md %}}The metric descriptor associated with the logs-based metric.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The client-assigned metric identifier. Examples - "error_count", "nginx/requests". Metric identifiers are limited to 100
characters and can include only the following characters A-Z, a-z, 0-9, and the special characters _-.,+!*',()%/. The
forward-slash character (/) denotes a hierarchy of name pieces, and it cannot be the first character of the name.
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
        <span>value_<wbr>extractor</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A valueExtractor is required when using a distribution logs-based metric to extract the values to record from a log
entry. Two functions are supported for value extraction - EXTRACT(field) or REGEXP_EXTRACT(field, regex). The argument
are 1. field - The name of the log entry field from which the value is to be extracted. 2. regex - A regular expression
using the Google RE2 syntax (https://github.com/google/re2/wiki/Syntax) with a single capture group to extract data from
the specified log entry field. The value of the field is converted to a string before applying the regex. It is an error
to specify a regex that does not include exactly one capture group.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Metric<wbr>Bucket<wbr>Options</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#MetricBucketOptions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#MetricBucketOptions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricBucketOptionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricBucketOptionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Explicit<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionsexplicitbuckets">Metric<wbr>Bucket<wbr>Options<wbr>Explicit<wbr>Buckets<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Exponential<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionsexponentialbuckets">Metric<wbr>Bucket<wbr>Options<wbr>Exponential<wbr>Buckets<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Linear<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionslinearbuckets">Metric<wbr>Bucket<wbr>Options<wbr>Linear<wbr>Buckets<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Explicit<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionsexplicitbuckets">*Metric<wbr>Bucket<wbr>Options<wbr>Explicit<wbr>Buckets</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Exponential<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionsexponentialbuckets">*Metric<wbr>Bucket<wbr>Options<wbr>Exponential<wbr>Buckets</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Linear<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionslinearbuckets">*Metric<wbr>Bucket<wbr>Options<wbr>Linear<wbr>Buckets</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>explicit<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionsexplicitbuckets">Metric<wbr>Bucket<wbr>Options<wbr>Explicit<wbr>Buckets?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>exponential<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionsexponentialbuckets">Metric<wbr>Bucket<wbr>Options<wbr>Exponential<wbr>Buckets?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>linear<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionslinearbuckets">Metric<wbr>Bucket<wbr>Options<wbr>Linear<wbr>Buckets?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>explicit<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionsexplicitbuckets">Dict[Metric<wbr>Bucket<wbr>Options<wbr>Explicit<wbr>Buckets]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>exponential<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionsexponentialbuckets">Dict[Metric<wbr>Bucket<wbr>Options<wbr>Exponential<wbr>Buckets]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>linear<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricbucketoptionslinearbuckets">Dict[Metric<wbr>Bucket<wbr>Options<wbr>Linear<wbr>Buckets]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Metric<wbr>Bucket<wbr>Options<wbr>Explicit<wbr>Buckets</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#MetricBucketOptionsExplicitBuckets">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#MetricBucketOptionsExplicitBuckets">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricBucketOptionsExplicitBucketsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricBucketOptionsExplicitBucketsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bounds</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<double></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bounds</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]float64</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bounds</span>
        <span class="property-indicator"></span>
        <span class="property-type">number[]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bounds</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[Number]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Metric<wbr>Bucket<wbr>Options<wbr>Exponential<wbr>Buckets</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#MetricBucketOptionsExponentialBuckets">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#MetricBucketOptionsExponentialBuckets">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricBucketOptionsExponentialBucketsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricBucketOptionsExponentialBucketsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Growth<wbr>Factor</span>
        <span class="property-indicator"></span>
        <span class="property-type">double?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Num<wbr>Finite<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Scale</span>
        <span class="property-indicator"></span>
        <span class="property-type">double?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Growth<wbr>Factor</span>
        <span class="property-indicator"></span>
        <span class="property-type">*float64</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Num<wbr>Finite<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Scale</span>
        <span class="property-indicator"></span>
        <span class="property-type">*float64</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>growth<wbr>Factor</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>num<wbr>Finite<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>scale</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>growth<wbr>Factor</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>num<wbr>Finite<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>scale</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Metric<wbr>Bucket<wbr>Options<wbr>Linear<wbr>Buckets</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#MetricBucketOptionsLinearBuckets">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#MetricBucketOptionsLinearBuckets">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricBucketOptionsLinearBucketsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricBucketOptionsLinearBucketsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Num<wbr>Finite<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Offset</span>
        <span class="property-indicator"></span>
        <span class="property-type">double?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Width</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Num<wbr>Finite<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Offset</span>
        <span class="property-indicator"></span>
        <span class="property-type">*float64</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Width</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>num<wbr>Finite<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>offset</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>width</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>num<wbr>Finite<wbr>Buckets</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>offset</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>width</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Metric<wbr>Metric<wbr>Descriptor</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#MetricMetricDescriptor">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#MetricMetricDescriptor">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricMetricDescriptorArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricMetricDescriptorOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptorlabel">List&lt;Metric<wbr>Metric<wbr>Descriptor<wbr>Label<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Metric<wbr>Kind</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Value<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptorlabel">[]Metric<wbr>Metric<wbr>Descriptor<wbr>Label</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Metric<wbr>Kind</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Value<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptorlabel">Metric<wbr>Metric<wbr>Descriptor<wbr>Label[]?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>metric<wbr>Kind</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>value<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>display_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#metricmetricdescriptorlabel">List[Metric<wbr>Metric<wbr>Descriptor<wbr>Label]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>metric<wbr>Kind</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>value<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Metric<wbr>Metric<wbr>Descriptor<wbr>Label</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#MetricMetricDescriptorLabel">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#MetricMetricDescriptorLabel">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricMetricDescriptorLabelArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/logging?tab=doc#MetricMetricDescriptorLabelOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Value<wbr>Type</span>
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
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Value<wbr>Type</span>
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
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>value<wbr>Type</span>
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
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>value<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}







