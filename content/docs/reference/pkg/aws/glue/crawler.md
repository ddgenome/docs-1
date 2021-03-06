
---
title: "Crawler"
block_external_search_index: true
---

Manages a Glue Crawler. More information can be found in the [AWS Glue Developer Guide](https://docs.aws.amazon.com/glue/latest/dg/add-crawler.html)

## Example Usage

### DynamoDB Target

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const example = new aws.glue.Crawler("example", {
    databaseName: aws_glue_catalog_database_example.name,
    dynamodbTargets: [{
        path: "table-name",
    }],
    role: aws_iam_role_example.arn,
});
```

### JDBC Target

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const example = new aws.glue.Crawler("example", {
    databaseName: aws_glue_catalog_database_example.name,
    jdbcTargets: [{
        connectionName: aws_glue_connection_example.name,
        path: "database-name/%",
    }],
    role: aws_iam_role_example.arn,
});
```

### S3 Target

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const example = new aws.glue.Crawler("example", {
    databaseName: aws_glue_catalog_database_example.name,
    role: aws_iam_role_example.arn,
    s3Targets: [{
        path: pulumi.interpolate`s3://${aws_s3_bucket_example.bucket}`,
    }],
});
```


### Catalog Target

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const example = new aws.glue.Crawler("example", {
    catalogTargets: [{
        databaseName: aws_glue_catalog_database_example.name,
        tables: [aws_glue_catalog_table_example.name],
    }],
    configuration: `{
  "Version":1.0,
  "Grouping": {
    "TableGroupingPolicy": "CombineCompatibleSchemas"
  }
}
`,
    databaseName: aws_glue_catalog_database_example.name,
    role: aws_iam_role_example.arn,
    schemaChangePolicy: {
        deleteBehavior: "LOG",
    },
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/glue_crawler.html.markdown.



## Create a Crawler Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/glue/#Crawler">Crawler</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/glue/#CrawlerArgs">CrawlerArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">Crawler</span><span class="p">(resource_name, opts=None, </span>catalog_targets=None<span class="p">, </span>classifiers=None<span class="p">, </span>configuration=None<span class="p">, </span>database_name=None<span class="p">, </span>description=None<span class="p">, </span>dynamodb_targets=None<span class="p">, </span>jdbc_targets=None<span class="p">, </span>name=None<span class="p">, </span>role=None<span class="p">, </span>s3_targets=None<span class="p">, </span>schedule=None<span class="p">, </span>schema_change_policy=None<span class="p">, </span>security_configuration=None<span class="p">, </span>table_prefix=None<span class="p">, </span>tags=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewCrawler<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerArgs">CrawlerArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#Crawler">Crawler</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Glue.Crawler.html">Crawler</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Glue.Inputs.CrawlerArgs.html">CrawlerArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Catalog<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">List&lt;Crawler<wbr>Catalog<wbr>Target<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dynamodb<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">List&lt;Crawler<wbr>Dynamodb<wbr>Target<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Jdbc<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">List&lt;Crawler<wbr>Jdbc<wbr>Target<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">List&lt;Crawler<wbr>S3Target<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schema<wbr>Change<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">Crawler<wbr>Schema<wbr>Change<wbr>Policy<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Security<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Table<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Catalog<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">[]Crawler<wbr>Catalog<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dynamodb<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">[]Crawler<wbr>Dynamodb<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Jdbc<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">[]Crawler<wbr>Jdbc<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">[]Crawler<wbr>S3Target</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schema<wbr>Change<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">*Crawler<wbr>Schema<wbr>Change<wbr>Policy</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Security<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Table<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>catalog<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">Crawler<wbr>Catalog<wbr>Target[]?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dynamodb<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">Crawler<wbr>Dynamodb<wbr>Target[]?</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>jdbc<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">Crawler<wbr>Jdbc<wbr>Target[]?</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">Crawler<wbr>S3Target[]?</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schema<wbr>Change<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">Crawler<wbr>Schema<wbr>Change<wbr>Policy?</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>security<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>table<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>catalog_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">List[Crawler<wbr>Catalog<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>database_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dynamodb_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">List[Crawler<wbr>Dynamodb<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>jdbc_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">List[Crawler<wbr>Jdbc<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">List[Crawler<wbr>S3Target]</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schema_<wbr>change_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">Dict[Crawler<wbr>Schema<wbr>Change<wbr>Policy]</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>security_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>table_<wbr>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## Crawler Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the crawler 
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Catalog<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">List&lt;Crawler<wbr>Catalog<wbr>Target&gt;?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Dynamodb<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">List&lt;Crawler<wbr>Dynamodb<wbr>Target&gt;?</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Jdbc<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">List&lt;Crawler<wbr>Jdbc<wbr>Target&gt;?</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>S3Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">List&lt;Crawler<wbr>S3Target&gt;?</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Schema<wbr>Change<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">Crawler<wbr>Schema<wbr>Change<wbr>Policy?</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Security<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Table<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
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
    <dd>{{% md %}}The ARN of the crawler 
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Catalog<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">[]Crawler<wbr>Catalog<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Dynamodb<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">[]Crawler<wbr>Dynamodb<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Jdbc<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">[]Crawler<wbr>Jdbc<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>S3Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">[]Crawler<wbr>S3Target</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Schema<wbr>Change<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">*Crawler<wbr>Schema<wbr>Change<wbr>Policy</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Security<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Table<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
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
    <dd>{{% md %}}The ARN of the crawler 
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>catalog<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">Crawler<wbr>Catalog<wbr>Target[]?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>dynamodb<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">Crawler<wbr>Dynamodb<wbr>Target[]?</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>jdbc<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">Crawler<wbr>Jdbc<wbr>Target[]?</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>s3Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">Crawler<wbr>S3Target[]?</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>schema<wbr>Change<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">Crawler<wbr>Schema<wbr>Change<wbr>Policy?</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>security<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>table<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
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
    <dd>{{% md %}}The ARN of the crawler 
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>catalog_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">List[Crawler<wbr>Catalog<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>database_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>dynamodb_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">List[Crawler<wbr>Dynamodb<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>jdbc_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">List[Crawler<wbr>Jdbc<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>s3_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">List[Crawler<wbr>S3Target]</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>schema_<wbr>change_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">Dict[Crawler<wbr>Schema<wbr>Change<wbr>Policy]</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>security_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>table_<wbr>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing Crawler Resource

Get an existing Crawler resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/glue/#CrawlerState">CrawlerState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/glue/#Crawler">Crawler</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>arn=None<span class="p">, </span>catalog_targets=None<span class="p">, </span>classifiers=None<span class="p">, </span>configuration=None<span class="p">, </span>database_name=None<span class="p">, </span>description=None<span class="p">, </span>dynamodb_targets=None<span class="p">, </span>jdbc_targets=None<span class="p">, </span>name=None<span class="p">, </span>role=None<span class="p">, </span>s3_targets=None<span class="p">, </span>schedule=None<span class="p">, </span>schema_change_policy=None<span class="p">, </span>security_configuration=None<span class="p">, </span>table_prefix=None<span class="p">, </span>tags=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetCrawler<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerState">CrawlerState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#Crawler">Crawler</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Glue.Crawler.html">Crawler</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Glue.CrawlerState.html">CrawlerState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
    <dd>{{% md %}}The ARN of the crawler 
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Catalog<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">List&lt;Crawler<wbr>Catalog<wbr>Target<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dynamodb<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">List&lt;Crawler<wbr>Dynamodb<wbr>Target<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Jdbc<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">List&lt;Crawler<wbr>Jdbc<wbr>Target<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">List&lt;Crawler<wbr>S3Target<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schema<wbr>Change<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">Crawler<wbr>Schema<wbr>Change<wbr>Policy<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Security<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Table<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
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
    <dd>{{% md %}}The ARN of the crawler 
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Catalog<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">[]Crawler<wbr>Catalog<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dynamodb<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">[]Crawler<wbr>Dynamodb<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Jdbc<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">[]Crawler<wbr>Jdbc<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">[]Crawler<wbr>S3Target</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Schema<wbr>Change<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">*Crawler<wbr>Schema<wbr>Change<wbr>Policy</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Security<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Table<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
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
    <dd>{{% md %}}The ARN of the crawler 
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>catalog<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">Crawler<wbr>Catalog<wbr>Target[]?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dynamodb<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">Crawler<wbr>Dynamodb<wbr>Target[]?</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>jdbc<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">Crawler<wbr>Jdbc<wbr>Target[]?</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">Crawler<wbr>S3Target[]?</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schema<wbr>Change<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">Crawler<wbr>Schema<wbr>Change<wbr>Policy?</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>security<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>table<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
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
    <dd>{{% md %}}The ARN of the crawler 
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>catalog_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlercatalogtarget">List[Crawler<wbr>Catalog<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>classifiers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of custom classifiers. By default, all AWS classifiers are included in a crawl, but these custom classifiers always override the default classifiers for a given classification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}JSON string of configuration information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>database_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Glue database where results are written.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Description of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dynamodb_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerdynamodbtarget">List[Crawler<wbr>Dynamodb<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}List of nested DynamoDB target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>jdbc_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerjdbctarget">List[Crawler<wbr>Jdbc<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}List of nested JBDC target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the crawler.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IAM role friendly name (including path without leading slash), or ARN of an IAM role, used by the crawler to access other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlers3target">List[Crawler<wbr>S3Target]</a></span>
    </dt>
    <dd>{{% md %}}List nested Amazon S3 target arguments. See below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schedule</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A cron expression used to specify the schedule. For more information, see [Time-Based Schedules for Jobs and Crawlers](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html). For example, to run something every day at 12:15 UTC, you would specify: `cron(15 12 * * ? *)`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>schema_<wbr>change_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#crawlerschemachangepolicy">Dict[Crawler<wbr>Schema<wbr>Change<wbr>Policy]</a></span>
    </dt>
    <dd>{{% md %}}Policy for the crawler's update and deletion behavior.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>security_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of Security Configuration to be used by the crawler
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>table_<wbr>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The table prefix used for catalog tables that are created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Crawler<wbr>Catalog<wbr>Target</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#CrawlerCatalogTarget">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#CrawlerCatalogTarget">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerCatalogTargetArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerCatalogTargetOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Glue database to be synchronized.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Tables</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}A list of catalog tables to be synchronized.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Glue database to be synchronized.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Tables</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of catalog tables to be synchronized.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the Glue database to be synchronized.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>tables</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}A list of catalog tables to be synchronized.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>database_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the Glue database to be synchronized.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>tables</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of catalog tables to be synchronized.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Crawler<wbr>Dynamodb<wbr>Target</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#CrawlerDynamodbTarget">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#CrawlerDynamodbTarget">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerDynamodbTargetArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerDynamodbTargetOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the DynamoDB table to crawl.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the DynamoDB table to crawl.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the DynamoDB table to crawl.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>path</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the DynamoDB table to crawl.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Crawler<wbr>Jdbc<wbr>Target</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#CrawlerJdbcTarget">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#CrawlerJdbcTarget">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerJdbcTargetArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerJdbcTargetOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Connection<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the connection to use to connect to the JDBC target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Exclusions</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of glob patterns used to exclude from the crawl.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The path of the JDBC target.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Connection<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the connection to use to connect to the JDBC target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Exclusions</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of glob patterns used to exclude from the crawl.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The path of the JDBC target.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>connection<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the connection to use to connect to the JDBC target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>exclusions</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of glob patterns used to exclude from the crawl.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The path of the JDBC target.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>connection<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the connection to use to connect to the JDBC target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>exclusions</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of glob patterns used to exclude from the crawl.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>path</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The path of the JDBC target.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Crawler<wbr>S3Target</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#CrawlerS3Target">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#CrawlerS3Target">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerS3TargetArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerS3TargetOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Exclusions</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of glob patterns used to exclude from the crawl.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the DynamoDB table to crawl.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Exclusions</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of glob patterns used to exclude from the crawl.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the DynamoDB table to crawl.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>exclusions</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of glob patterns used to exclude from the crawl.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>path</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the DynamoDB table to crawl.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>exclusions</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of glob patterns used to exclude from the crawl.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>path</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the DynamoDB table to crawl.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Crawler<wbr>Schema<wbr>Change<wbr>Policy</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#CrawlerSchemaChangePolicy">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#CrawlerSchemaChangePolicy">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerSchemaChangePolicyArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/glue?tab=doc#CrawlerSchemaChangePolicyOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Behavior</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The deletion behavior when the crawler finds a deleted object. Valid values: `LOG`, `DELETE_FROM_DATABASE`, or `DEPRECATE_IN_DATABASE`. Defaults to `DEPRECATE_IN_DATABASE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Update<wbr>Behavior</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The update behavior when the crawler finds a changed schema. Valid values: `LOG` or `UPDATE_IN_DATABASE`. Defaults to `UPDATE_IN_DATABASE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>Behavior</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The deletion behavior when the crawler finds a deleted object. Valid values: `LOG`, `DELETE_FROM_DATABASE`, or `DEPRECATE_IN_DATABASE`. Defaults to `DEPRECATE_IN_DATABASE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Update<wbr>Behavior</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The update behavior when the crawler finds a changed schema. Valid values: `LOG` or `UPDATE_IN_DATABASE`. Defaults to `UPDATE_IN_DATABASE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>delete<wbr>Behavior</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The deletion behavior when the crawler finds a deleted object. Valid values: `LOG`, `DELETE_FROM_DATABASE`, or `DEPRECATE_IN_DATABASE`. Defaults to `DEPRECATE_IN_DATABASE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>update<wbr>Behavior</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The update behavior when the crawler finds a changed schema. Valid values: `LOG` or `UPDATE_IN_DATABASE`. Defaults to `UPDATE_IN_DATABASE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>delete<wbr>Behavior</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The deletion behavior when the crawler finds a deleted object. Valid values: `LOG`, `DELETE_FROM_DATABASE`, or `DEPRECATE_IN_DATABASE`. Defaults to `DEPRECATE_IN_DATABASE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>update<wbr>Behavior</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The update behavior when the crawler finds a changed schema. Valid values: `LOG` or `UPDATE_IN_DATABASE`. Defaults to `UPDATE_IN_DATABASE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







