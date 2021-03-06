
---
title: "FirehoseDeliveryStream"
block_external_search_index: true
---

Provides a Kinesis Firehose Delivery Stream resource. Amazon Kinesis Firehose is a fully managed, elastic service to easily deliver real-time data streams to destinations such as Amazon S3 and Amazon Redshift.

For more details, see the [Amazon Kinesis Firehose Documentation][1].

## Example Usage

### Extended S3 Destination

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const bucket = new aws.s3.Bucket("bucket", {
    acl: "private",
});
const firehoseRole = new aws.iam.Role("firehose_role", {
    assumeRolePolicy: `{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": "sts:AssumeRole",
      "Principal": {
        "Service": "firehose.amazonaws.com"
      },
      "Effect": "Allow",
      "Sid": ""
    }
  ]
}
`,
});
const lambdaIam = new aws.iam.Role("lambda_iam", {
    assumeRolePolicy: `{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": "sts:AssumeRole",
      "Principal": {
        "Service": "lambda.amazonaws.com"
      },
      "Effect": "Allow",
      "Sid": ""
    }
  ]
}
`,
});
const lambdaProcessor = new aws.lambda.Function("lambda_processor", {
    code: new pulumi.asset.FileArchive("lambda.zip"),
    handler: "exports.handler",
    role: lambdaIam.arn,
    runtime: "nodejs8.10",
});
const extendedS3Stream = new aws.kinesis.FirehoseDeliveryStream("extended_s3_stream", {
    destination: "extended_s3",
    extendedS3Configuration: {
        bucketArn: bucket.arn,
        processingConfiguration: {
            enabled: true,
            processors: [{
                parameters: [{
                    parameterName: "LambdaArn",
                    parameterValue: pulumi.interpolate`${lambdaProcessor.arn}:$LATEST`,
                }],
                type: "Lambda",
            }],
        },
        roleArn: firehoseRole.arn,
    },
});
```

### S3 Destination

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const bucket = new aws.s3.Bucket("bucket", {
    acl: "private",
});
const firehoseRole = new aws.iam.Role("firehose_role", {
    assumeRolePolicy: `{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": "sts:AssumeRole",
      "Principal": {
        "Service": "firehose.amazonaws.com"
      },
      "Effect": "Allow",
      "Sid": ""
    }
  ]
}
`,
});
const testStream = new aws.kinesis.FirehoseDeliveryStream("test_stream", {
    destination: "s3",
    s3Configuration: {
        bucketArn: bucket.arn,
        roleArn: firehoseRole.arn,
    },
});
```

### Redshift Destination

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const testCluster = new aws.redshift.Cluster("test_cluster", {
    clusterIdentifier: "tf-redshift-cluster-%d",
    clusterType: "single-node",
    databaseName: "test",
    masterPassword: "T3stPass",
    masterUsername: "testuser",
    nodeType: "dc1.large",
});
const testStream = new aws.kinesis.FirehoseDeliveryStream("test_stream", {
    destination: "redshift",
    redshiftConfiguration: {
        clusterJdbcurl: pulumi.interpolate`jdbc:redshift://${testCluster.endpoint}/${testCluster.databaseName}`,
        copyOptions: "delimiter '|'", // the default delimiter
        dataTableColumns: "test-col",
        dataTableName: "test-table",
        password: "T3stPass",
        roleArn: aws_iam_role_firehose_role.arn,
        s3BackupConfiguration: {
            bucketArn: aws_s3_bucket_bucket.arn,
            bufferInterval: 300,
            bufferSize: 15,
            compressionFormat: "GZIP",
            roleArn: aws_iam_role_firehose_role.arn,
        },
        s3BackupMode: "Enabled",
        username: "testuser",
    },
    s3Configuration: {
        bucketArn: aws_s3_bucket_bucket.arn,
        bufferInterval: 400,
        bufferSize: 10,
        compressionFormat: "GZIP",
        roleArn: aws_iam_role_firehose_role.arn,
    },
});
```

### Elasticsearch Destination

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const testCluster = new aws.elasticsearch.Domain("test_cluster", {});
const testStream = new aws.kinesis.FirehoseDeliveryStream("test_stream", {
    destination: "elasticsearch",
    elasticsearchConfiguration: {
        domainArn: testCluster.arn,
        indexName: "test",
        processingConfiguration: {
            enabled: true,
            processors: [{
                parameters: [{
                    parameterName: "LambdaArn",
                    parameterValue: pulumi.interpolate`${aws_lambda_function_lambda_processor.arn}:$LATEST`,
                }],
                type: "Lambda",
            }],
        },
        roleArn: aws_iam_role_firehose_role.arn,
        typeName: "test",
    },
    s3Configuration: {
        bucketArn: aws_s3_bucket_bucket.arn,
        bufferInterval: 400,
        bufferSize: 10,
        compressionFormat: "GZIP",
        roleArn: aws_iam_role_firehose_role.arn,
    },
});
```


### Splunk Destination

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const testStream = new aws.kinesis.FirehoseDeliveryStream("test_stream", {
    destination: "splunk",
    s3Configuration: {
        bucketArn: aws_s3_bucket_bucket.arn,
        bufferInterval: 400,
        bufferSize: 10,
        compressionFormat: "GZIP",
        roleArn: aws_iam_role_firehose.arn,
    },
    splunkConfiguration: {
        hecAcknowledgmentTimeout: 600,
        hecEndpoint: "https://http-inputs-mydomain.splunkcloud.com:443",
        hecEndpointType: "Event",
        hecToken: "51D4DA16-C61B-4F5F-8EC7-ED4301342A4A",
        s3BackupMode: "FailedEventsOnly",
    },
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/kinesis_firehose_delivery_stream.html.markdown.



## Create a FirehoseDeliveryStream Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/kinesis/#FirehoseDeliveryStream">FirehoseDeliveryStream</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/kinesis/#FirehoseDeliveryStreamArgs">FirehoseDeliveryStreamArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">FirehoseDeliveryStream</span><span class="p">(resource_name, opts=None, </span>arn=None<span class="p">, </span>destination=None<span class="p">, </span>destination_id=None<span class="p">, </span>elasticsearch_configuration=None<span class="p">, </span>extended_s3_configuration=None<span class="p">, </span>kinesis_source_configuration=None<span class="p">, </span>name=None<span class="p">, </span>redshift_configuration=None<span class="p">, </span>s3_configuration=None<span class="p">, </span>server_side_encryption=None<span class="p">, </span>splunk_configuration=None<span class="p">, </span>tags=None<span class="p">, </span>version_id=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewFirehoseDeliveryStream<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamArgs">FirehoseDeliveryStreamArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStream">FirehoseDeliveryStream</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Kinesis.FirehoseDeliveryStream.html">FirehoseDeliveryStream</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Kinesis.Inputs.FirehoseDeliveryStreamArgs.html">FirehoseDeliveryStreamArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Destination<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Elasticsearch<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Extended<wbr>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kinesis<wbr>Source<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Redshift<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Server<wbr>Side<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Splunk<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
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
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Destination<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Elasticsearch<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Extended<wbr>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kinesis<wbr>Source<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Redshift<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">*Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Server<wbr>Side<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">*Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Splunk<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
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
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>destination<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>elasticsearch<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>extended<wbr>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kinesis<wbr>Source<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>redshift<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>server<wbr>Side<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption?</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>splunk<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
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
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>destination_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>elasticsearch_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>extended_<wbr>s3_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kinesis_<wbr>source_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>redshift_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>server_<wbr>side_<wbr>encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption]</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>splunk_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>version_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## FirehoseDeliveryStream Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Destination<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Elasticsearch<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Extended<wbr>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Kinesis<wbr>Source<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Redshift<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Server<wbr>Side<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption?</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Splunk<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
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
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Destination<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Elasticsearch<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Extended<wbr>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Kinesis<wbr>Source<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Redshift<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">*Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Server<wbr>Side<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">*Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Splunk<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
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
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>destination<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>elasticsearch<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>extended<wbr>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>kinesis<wbr>Source<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>redshift<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>s3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>server<wbr>Side<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption?</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>splunk<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
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
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>destination_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>elasticsearch_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>extended_<wbr>s3_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>kinesis_<wbr>source_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>redshift_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>s3_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>server_<wbr>side_<wbr>encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption]</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>splunk_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>version_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing FirehoseDeliveryStream Resource

Get an existing FirehoseDeliveryStream resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/kinesis/#FirehoseDeliveryStreamState">FirehoseDeliveryStreamState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/kinesis/#FirehoseDeliveryStream">FirehoseDeliveryStream</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>arn=None<span class="p">, </span>destination=None<span class="p">, </span>destination_id=None<span class="p">, </span>elasticsearch_configuration=None<span class="p">, </span>extended_s3_configuration=None<span class="p">, </span>kinesis_source_configuration=None<span class="p">, </span>name=None<span class="p">, </span>redshift_configuration=None<span class="p">, </span>s3_configuration=None<span class="p">, </span>server_side_encryption=None<span class="p">, </span>splunk_configuration=None<span class="p">, </span>tags=None<span class="p">, </span>version_id=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetFirehoseDeliveryStream<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamState">FirehoseDeliveryStreamState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStream">FirehoseDeliveryStream</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Kinesis.FirehoseDeliveryStream.html">FirehoseDeliveryStream</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Kinesis.FirehoseDeliveryStreamState.html">FirehoseDeliveryStreamState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Destination<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Elasticsearch<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Extended<wbr>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kinesis<wbr>Source<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Redshift<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Server<wbr>Side<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Splunk<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
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
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Destination<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Elasticsearch<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Extended<wbr>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kinesis<wbr>Source<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Redshift<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">*Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Server<wbr>Side<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">*Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Splunk<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
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
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>destination<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>elasticsearch<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>extended<wbr>S3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kinesis<wbr>Source<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>redshift<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>server<wbr>Side<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption?</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>splunk<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
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
    <dd>{{% md %}}The Amazon Resource Name (ARN) specifying the Stream
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>destination</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}This is the destination to where the data is delivered. The only options are `s3` (Deprecated, use `extended_s3` instead), `extended_s3`, `redshift`, `elasticsearch`, and `splunk`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>destination_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>elasticsearch_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if elasticsearch is the destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>extended_<wbr>s3_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configuration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Enhanced configuration options for the s3 destination. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kinesis_<wbr>source_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamkinesissourceconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Allows the ability to specify the kinesis stream that is used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A name to identify the stream. This is unique to the
AWS account and region the Stream is created in.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>redshift_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Configuration options if redshift is the destination.
Using `redshift_configuration` requires the user to also specify a
`s3_configuration` block. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configuration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Required for non-S3 destinations. For S3 destination, use `extended_s3_configuration` instead. Configuration options for the s3 destination (or the intermediate bucket if the destination
is redshift). More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>server_<wbr>side_<wbr>encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamserversideencryption">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption]</a></span>
    </dt>
    <dd>{{% md %}}Encrypt at rest options.
Server-side encryption should not be enabled when a kinesis stream is configured as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>splunk_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>version_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamElasticsearchConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamElasticsearchConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamElasticsearchConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamElasticsearchConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Buffering<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds between 60 to 900, before delivering it to the destination.  The default value is 300s.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffering<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs between 1 to 100, before delivering it to the destination.  The default value is 5MB.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Domain<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the Amazon ES domain.  The IAM role must have permission for `DescribeElasticsearchDomain`, `DescribeElasticsearchDomains`, and `DescribeElasticsearchDomainConfig` after assuming `RoleARN`.  The pattern needs to be `arn:.*`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Index<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch index name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Index<wbr>Rotation<wbr>Period</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch index rotation period.  Index rotation appends a timestamp to the IndexName to facilitate expiration of old data.  Valid values are `NoRotation`, `OneHour`, `OneDay`, `OneWeek`, and `OneMonth`.  The default value is `OneDay`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}After an initial failure to deliver to Amazon Elasticsearch, the total amount of time, in seconds between 0 to 7200, during which Firehose re-attempts delivery (including the first attempt).  After this time has elapsed, the failed documents are written to Amazon S3.  The default value is 300s.  There will be no retry if the value is 0.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the IAM role to be assumed by Firehose for calling the Amazon ES Configuration API and for indexing documents.  The pattern needs to be `arn:.*`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Defines how documents should be delivered to Amazon S3.  Valid values are `FailedDocumentsOnly` and `AllDocuments`.  Default value is `FailedDocumentsOnly`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch type name with maximum length of 100 characters.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Buffering<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds between 60 to 900, before delivering it to the destination.  The default value is 300s.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffering<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs between 1 to 100, before delivering it to the destination.  The default value is 5MB.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationcloudwatchloggingoptions">*Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Domain<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the Amazon ES domain.  The IAM role must have permission for `DescribeElasticsearchDomain`, `DescribeElasticsearchDomains`, and `DescribeElasticsearchDomainConfig` after assuming `RoleARN`.  The pattern needs to be `arn:.*`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Index<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch index name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Index<wbr>Rotation<wbr>Period</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch index rotation period.  Index rotation appends a timestamp to the IndexName to facilitate expiration of old data.  Valid values are `NoRotation`, `OneHour`, `OneDay`, `OneWeek`, and `OneMonth`.  The default value is `OneDay`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}After an initial failure to deliver to Amazon Elasticsearch, the total amount of time, in seconds between 0 to 7200, during which Firehose re-attempts delivery (including the first attempt).  After this time has elapsed, the failed documents are written to Amazon S3.  The default value is 300s.  There will be no retry if the value is 0.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the IAM role to be assumed by Firehose for calling the Amazon ES Configuration API and for indexing documents.  The pattern needs to be `arn:.*`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Defines how documents should be delivered to Amazon S3.  Valid values are `FailedDocumentsOnly` and `AllDocuments`.  Default value is `FailedDocumentsOnly`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch type name with maximum length of 100 characters.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>buffering<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds between 60 to 900, before delivering it to the destination.  The default value is 300s.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffering<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs between 1 to 100, before delivering it to the destination.  The default value is 5MB.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>domain<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the Amazon ES domain.  The IAM role must have permission for `DescribeElasticsearchDomain`, `DescribeElasticsearchDomains`, and `DescribeElasticsearchDomainConfig` after assuming `RoleARN`.  The pattern needs to be `arn:.*`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>index<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch index name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>index<wbr>Rotation<wbr>Period</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch index rotation period.  Index rotation appends a timestamp to the IndexName to facilitate expiration of old data.  Valid values are `NoRotation`, `OneHour`, `OneDay`, `OneWeek`, and `OneMonth`.  The default value is `OneDay`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}After an initial failure to deliver to Amazon Elasticsearch, the total amount of time, in seconds between 0 to 7200, during which Firehose re-attempts delivery (including the first attempt).  After this time has elapsed, the failed documents are written to Amazon S3.  The default value is 300s.  There will be no retry if the value is 0.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the IAM role to be assumed by Firehose for calling the Amazon ES Configuration API and for indexing documents.  The pattern needs to be `arn:.*`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Defines how documents should be delivered to Amazon S3.  Valid values are `FailedDocumentsOnly` and `AllDocuments`.  Default value is `FailedDocumentsOnly`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch type name with maximum length of 100 characters.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>buffering<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds between 60 to 900, before delivering it to the destination.  The default value is 300s.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffering<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs between 1 to 100, before delivering it to the destination.  The default value is 5MB.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch_<wbr>logging_<wbr>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationcloudwatchloggingoptions">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>domain<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the Amazon ES domain.  The IAM role must have permission for `DescribeElasticsearchDomain`, `DescribeElasticsearchDomains`, and `DescribeElasticsearchDomainConfig` after assuming `RoleARN`.  The pattern needs to be `arn:.*`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>index<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch index name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>index<wbr>Rotation<wbr>Period</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch index rotation period.  Index rotation appends a timestamp to the IndexName to facilitate expiration of old data.  Valid values are `NoRotation`, `OneHour`, `OneDay`, `OneWeek`, and `OneMonth`.  The default value is `OneDay`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}After an initial failure to deliver to Amazon Elasticsearch, the total amount of time, in seconds between 0 to 7200, during which Firehose re-attempts delivery (including the first attempt).  After this time has elapsed, the failed documents are written to Amazon S3.  The default value is 300s.  There will be no retry if the value is 0.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the IAM role to be assumed by Firehose for calling the Amazon ES Configuration API and for indexing documents.  The pattern needs to be `arn:.*`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Defines how documents should be delivered to Amazon S3.  Valid values are `FailedDocumentsOnly` and `AllDocuments`.  Default value is `FailedDocumentsOnly`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Elasticsearch type name with maximum length of 100 characters.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamElasticsearchConfigurationCloudwatchLoggingOptions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamElasticsearchConfigurationCloudwatchLoggingOptions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamElasticsearchConfigurationCloudwatchLoggingOptionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamElasticsearchConfigurationCloudwatchLoggingOptionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfigurationprocessor">List&lt;Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfigurationprocessor">[]Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfigurationprocessor">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor[]?</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfigurationprocessor">List[Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor]</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfigurationProcessor">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfigurationProcessor">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfigurationProcessorArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfigurationProcessorOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfigurationprocessorparameter">List&lt;Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfigurationprocessorparameter">[]Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfigurationprocessorparameter">Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter[]?</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamelasticsearchconfigurationprocessingconfigurationprocessorparameter">List[Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter]</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Elasticsearch<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfigurationProcessorParameter">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfigurationProcessorParameter">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfigurationProcessorParameterArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamElasticsearchConfigurationProcessingConfigurationProcessorParameterOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3Configuration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3Configuration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Data<wbr>Format<wbr>Conversion<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Nested argument for the serializer, deserializer, and schema for converting data from the JSON format to the Parquet or ORC format before writing it to Amazon S3. More details given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Error<wbr>Output<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Prefix added to failed records before writing them to S3. This prefix appears immediately following the bucket name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurations3backupconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>S3Backup<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The configuration for backup in Amazon S3. Required if `s3_backup_mode` is `Enabled`. Supports the same fields as `s3_configuration` object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Amazon S3 backup mode.  Valid values are `Disabled` and `Enabled`.  Default value is `Disabled`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationcloudwatchloggingoptions">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Data<wbr>Format<wbr>Conversion<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Nested argument for the serializer, deserializer, and schema for converting data from the JSON format to the Parquet or ORC format before writing it to Amazon S3. More details given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Error<wbr>Output<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Prefix added to failed records before writing them to S3. This prefix appears immediately following the bucket name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurations3backupconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>S3Backup<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}The configuration for backup in Amazon S3. Required if `s3_backup_mode` is `Enabled`. Supports the same fields as `s3_configuration` object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Amazon S3 backup mode.  Valid values are `Disabled` and `Enabled`.  Default value is `Disabled`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>data<wbr>Format<wbr>Conversion<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}Nested argument for the serializer, deserializer, and schema for converting data from the JSON format to the Parquet or ORC format before writing it to Amazon S3. More details given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>error<wbr>Output<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Prefix added to failed records before writing them to S3. This prefix appears immediately following the bucket name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurations3backupconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>S3Backup<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}The configuration for backup in Amazon S3. Required if `s3_backup_mode` is `Enabled`. Supports the same fields as `s3_configuration` object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Amazon S3 backup mode.  Valid values are `Disabled` and `Enabled`.  Default value is `Disabled`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch_<wbr>logging_<wbr>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationcloudwatchloggingoptions">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>data<wbr>Format<wbr>Conversion<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Nested argument for the serializer, deserializer, and schema for converting data from the JSON format to the Parquet or ORC format before writing it to Amazon S3. More details given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>error<wbr>Output<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Prefix added to failed records before writing them to S3. This prefix appears immediately following the bucket name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>key_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurations3backupconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>S3Backup<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}The configuration for backup in Amazon S3. Required if `s3_backup_mode` is `Enabled`. Supports the same fields as `s3_configuration` object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Amazon S3 backup mode.  Valid values are `Disabled` and `Enabled`.  Default value is `Disabled`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationCloudwatchLoggingOptions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationCloudwatchLoggingOptions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationCloudwatchLoggingOptionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationCloudwatchLoggingOptionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Defaults to `true`. Set it to `false` if you want to disable format conversion while preserving the configuration details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Input<wbr>Format<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the deserializer that you want Kinesis Data Firehose to use to convert the format of your data from JSON. More details below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Output<wbr>Format<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the serializer that you want Kinesis Data Firehose to use to convert the format of your data to the Parquet or ORC format. More details below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Schema<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationschemaconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Schema<wbr>Configuration<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the AWS Glue Data Catalog table that contains the column information. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Defaults to `true`. Set it to `false` if you want to disable format conversion while preserving the configuration details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Input<wbr>Format<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the deserializer that you want Kinesis Data Firehose to use to convert the format of your data from JSON. More details below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Output<wbr>Format<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the serializer that you want Kinesis Data Firehose to use to convert the format of your data to the Parquet or ORC format. More details below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Schema<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationschemaconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Schema<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the AWS Glue Data Catalog table that contains the column information. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Defaults to `true`. Set it to `false` if you want to disable format conversion while preserving the configuration details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>input<wbr>Format<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the deserializer that you want Kinesis Data Firehose to use to convert the format of your data from JSON. More details below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>output<wbr>Format<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the serializer that you want Kinesis Data Firehose to use to convert the format of your data to the Parquet or ORC format. More details below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>schema<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationschemaconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Schema<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the AWS Glue Data Catalog table that contains the column information. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Defaults to `true`. Set it to `false` if you want to disable format conversion while preserving the configuration details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>input<wbr>Format<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the deserializer that you want Kinesis Data Firehose to use to convert the format of your data from JSON. More details below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>output<wbr>Format<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the serializer that you want Kinesis Data Firehose to use to convert the format of your data to the Parquet or ORC format. More details below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>schema<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationschemaconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Schema<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the AWS Glue Data Catalog table that contains the column information. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Deserializer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializer">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies which deserializer to use. You can choose either the Apache Hive JSON SerDe or the OpenX JSON SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Deserializer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializer">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies which deserializer to use. You can choose either the Apache Hive JSON SerDe or the OpenX JSON SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>deserializer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializer">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies which deserializer to use. You can choose either the Apache Hive JSON SerDe or the OpenX JSON SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>deserializer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializer">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer]</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies which deserializer to use. You can choose either the Apache Hive JSON SerDe or the OpenX JSON SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializer">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializer">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializerArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializerOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Hive<wbr>Json<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializerhivejsonserde">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Hive<wbr>Json<wbr>Ser<wbr>De<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the native Hive / HCatalog JsonSerDe. More details below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Open<wbr>XJson<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializeropenxjsonserde">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Open<wbr>XJson<wbr>Ser<wbr>De<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the OpenX SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Hive<wbr>Json<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializerhivejsonserde">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Hive<wbr>Json<wbr>Ser<wbr>De</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the native Hive / HCatalog JsonSerDe. More details below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Open<wbr>XJson<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializeropenxjsonserde">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Open<wbr>XJson<wbr>Ser<wbr>De</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the OpenX SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>hive<wbr>Json<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializerhivejsonserde">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Hive<wbr>Json<wbr>Ser<wbr>De?</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the native Hive / HCatalog JsonSerDe. More details below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>open<wbr>XJson<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializeropenxjsonserde">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Open<wbr>XJson<wbr>Ser<wbr>De?</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the OpenX SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>hive<wbr>Json<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializerhivejsonserde">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Hive<wbr>Json<wbr>Ser<wbr>De]</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the native Hive / HCatalog JsonSerDe. More details below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>open<wbr>XJson<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationinputformatconfigurationdeserializeropenxjsonserde">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Open<wbr>XJson<wbr>Ser<wbr>De]</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies the OpenX SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Hive<wbr>Json<wbr>Ser<wbr>De</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializerHiveJsonSerDe">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializerHiveJsonSerDe">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializerHiveJsonSerDeArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializerHiveJsonSerDeOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Timestamp<wbr>Formats</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of how you want Kinesis Data Firehose to parse the date and time stamps that may be present in your input data JSON. To specify these format strings, follow the pattern syntax of JodaTime's DateTimeFormat format strings. For more information, see [Class DateTimeFormat](https://www.joda.org/joda-time/apidocs/org/joda/time/format/DateTimeFormat.html). You can also use the special value millis to parse time stamps in epoch milliseconds. If you don't specify a format, Kinesis Data Firehose uses java.sql.Timestamp::valueOf by default.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Timestamp<wbr>Formats</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of how you want Kinesis Data Firehose to parse the date and time stamps that may be present in your input data JSON. To specify these format strings, follow the pattern syntax of JodaTime's DateTimeFormat format strings. For more information, see [Class DateTimeFormat](https://www.joda.org/joda-time/apidocs/org/joda/time/format/DateTimeFormat.html). You can also use the special value millis to parse time stamps in epoch milliseconds. If you don't specify a format, Kinesis Data Firehose uses java.sql.Timestamp::valueOf by default.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>timestamp<wbr>Formats</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of how you want Kinesis Data Firehose to parse the date and time stamps that may be present in your input data JSON. To specify these format strings, follow the pattern syntax of JodaTime's DateTimeFormat format strings. For more information, see [Class DateTimeFormat](https://www.joda.org/joda-time/apidocs/org/joda/time/format/DateTimeFormat.html). You can also use the special value millis to parse time stamps in epoch milliseconds. If you don't specify a format, Kinesis Data Firehose uses java.sql.Timestamp::valueOf by default.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>timestamp<wbr>Formats</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of how you want Kinesis Data Firehose to parse the date and time stamps that may be present in your input data JSON. To specify these format strings, follow the pattern syntax of JodaTime's DateTimeFormat format strings. For more information, see [Class DateTimeFormat](https://www.joda.org/joda-time/apidocs/org/joda/time/format/DateTimeFormat.html). You can also use the special value millis to parse time stamps in epoch milliseconds. If you don't specify a format, Kinesis Data Firehose uses java.sql.Timestamp::valueOf by default.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Input<wbr>Format<wbr>Configuration<wbr>Deserializer<wbr>Open<wbr>XJson<wbr>Ser<wbr>De</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializerOpenXJsonSerDe">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializerOpenXJsonSerDe">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializerOpenXJsonSerDeArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationInputFormatConfigurationDeserializerOpenXJsonSerDeOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Case<wbr>Insensitive</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}When set to true, which is the default, Kinesis Data Firehose converts JSON keys to lowercase before deserializing them.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Column<wbr>To<wbr>Json<wbr>Key<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A map of column names to JSON keys that aren't identical to the column names. This is useful when the JSON contains keys that are Hive keywords. For example, timestamp is a Hive keyword. If you have a JSON key named timestamp, set this parameter to `{ ts = "timestamp" }` to map this key to a column named ts.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Convert<wbr>Dots<wbr>In<wbr>Json<wbr>Keys<wbr>To<wbr>Underscores</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}When set to `true`, specifies that the names of the keys include dots and that you want Kinesis Data Firehose to replace them with underscores. This is useful because Apache Hive does not allow dots in column names. For example, if the JSON contains a key whose name is "a.b", you can define the column name to be "a_b" when using this option. Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Case<wbr>Insensitive</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}When set to true, which is the default, Kinesis Data Firehose converts JSON keys to lowercase before deserializing them.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Column<wbr>To<wbr>Json<wbr>Key<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A map of column names to JSON keys that aren't identical to the column names. This is useful when the JSON contains keys that are Hive keywords. For example, timestamp is a Hive keyword. If you have a JSON key named timestamp, set this parameter to `{ ts = "timestamp" }` to map this key to a column named ts.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Convert<wbr>Dots<wbr>In<wbr>Json<wbr>Keys<wbr>To<wbr>Underscores</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}When set to `true`, specifies that the names of the keys include dots and that you want Kinesis Data Firehose to replace them with underscores. This is useful because Apache Hive does not allow dots in column names. For example, if the JSON contains a key whose name is "a.b", you can define the column name to be "a_b" when using this option. Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>case<wbr>Insensitive</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}When set to true, which is the default, Kinesis Data Firehose converts JSON keys to lowercase before deserializing them.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>column<wbr>To<wbr>Json<wbr>Key<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A map of column names to JSON keys that aren't identical to the column names. This is useful when the JSON contains keys that are Hive keywords. For example, timestamp is a Hive keyword. If you have a JSON key named timestamp, set this parameter to `{ ts = "timestamp" }` to map this key to a column named ts.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>convert<wbr>Dots<wbr>In<wbr>Json<wbr>Keys<wbr>To<wbr>Underscores</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}When set to `true`, specifies that the names of the keys include dots and that you want Kinesis Data Firehose to replace them with underscores. This is useful because Apache Hive does not allow dots in column names. For example, if the JSON contains a key whose name is "a.b", you can define the column name to be "a_b" when using this option. Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>case<wbr>Insensitive</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}When set to true, which is the default, Kinesis Data Firehose converts JSON keys to lowercase before deserializing them.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>column<wbr>To<wbr>Json<wbr>Key<wbr>Mappings</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A map of column names to JSON keys that aren't identical to the column names. This is useful when the JSON contains keys that are Hive keywords. For example, timestamp is a Hive keyword. If you have a JSON key named timestamp, set this parameter to `{ ts = "timestamp" }` to map this key to a column named ts.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>convert<wbr>Dots<wbr>In<wbr>Json<wbr>Keys<wbr>To<wbr>Underscores</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}When set to `true`, specifies that the names of the keys include dots and that you want Kinesis Data Firehose to replace them with underscores. This is useful because Apache Hive does not allow dots in column names. For example, if the JSON contains a key whose name is "a.b", you can define the column name to be "a_b" when using this option. Defaults to `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Serializer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializer">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies which serializer to use. You can choose either the ORC SerDe or the Parquet SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Serializer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializer">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies which serializer to use. You can choose either the ORC SerDe or the Parquet SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>serializer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializer">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies which serializer to use. You can choose either the ORC SerDe or the Parquet SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>serializer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializer">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer]</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies which serializer to use. You can choose either the ORC SerDe or the Parquet SerDe. More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializer">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializer">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializerArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializerOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Orc<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializerorcserde">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Orc<wbr>Ser<wbr>De<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies converting data to the ORC format before storing it in Amazon S3. For more information, see [Apache ORC](https://orc.apache.org/docs/). More details below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Parquet<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializerparquetserde">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Parquet<wbr>Ser<wbr>De<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies converting data to the Parquet format before storing it in Amazon S3. For more information, see [Apache Parquet](https://parquet.apache.org/documentation/latest/). More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Orc<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializerorcserde">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Orc<wbr>Ser<wbr>De</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies converting data to the ORC format before storing it in Amazon S3. For more information, see [Apache ORC](https://orc.apache.org/docs/). More details below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Parquet<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializerparquetserde">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Parquet<wbr>Ser<wbr>De</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies converting data to the Parquet format before storing it in Amazon S3. For more information, see [Apache Parquet](https://parquet.apache.org/documentation/latest/). More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>orc<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializerorcserde">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Orc<wbr>Ser<wbr>De?</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies converting data to the ORC format before storing it in Amazon S3. For more information, see [Apache ORC](https://orc.apache.org/docs/). More details below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>parquet<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializerparquetserde">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Parquet<wbr>Ser<wbr>De?</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies converting data to the Parquet format before storing it in Amazon S3. For more information, see [Apache Parquet](https://parquet.apache.org/documentation/latest/). More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>orc<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializerorcserde">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Orc<wbr>Ser<wbr>De]</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies converting data to the ORC format before storing it in Amazon S3. For more information, see [Apache ORC](https://orc.apache.org/docs/). More details below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>parquet<wbr>Ser<wbr>De</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationdataformatconversionconfigurationoutputformatconfigurationserializerparquetserde">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Parquet<wbr>Ser<wbr>De]</a></span>
    </dt>
    <dd>{{% md %}}Nested argument that specifies converting data to the Parquet format before storing it in Amazon S3. For more information, see [Apache Parquet](https://parquet.apache.org/documentation/latest/). More details below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Orc<wbr>Ser<wbr>De</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializerOrcSerDe">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializerOrcSerDe">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializerOrcSerDeArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializerOrcSerDeOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The Hadoop Distributed File System (HDFS) block size. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is 256 MiB and the minimum is 64 MiB. Kinesis Data Firehose uses this value for padding calculations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bloom<wbr>Filter<wbr>Columns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of column names for which you want Kinesis Data Firehose to create bloom filters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bloom<wbr>Filter<wbr>False<wbr>Positive<wbr>Probability</span>
        <span class="property-indicator"></span>
        <span class="property-type">double?</span>
    </dt>
    <dd>{{% md %}}The Bloom filter false positive probability (FPP). The lower the FPP, the bigger the Bloom filter. The default value is `0.05`, the minimum is `0`, and the maximum is `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression code to use over data blocks. The possible values are `UNCOMPRESSED`, `SNAPPY`, and `GZIP`, with the default being `SNAPPY`. Use `SNAPPY` for higher decompression speed. Use `GZIP` if the compression ratio is more important than speed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dictionary<wbr>Key<wbr>Threshold</span>
        <span class="property-indicator"></span>
        <span class="property-type">double?</span>
    </dt>
    <dd>{{% md %}}A float that represents the fraction of the total number of non-null rows. To turn off dictionary encoding, set this fraction to a number that is less than the number of distinct keys in a dictionary. To always use dictionary encoding, set this threshold to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enable<wbr>Padding</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Set this to `true` to indicate that you want stripes to be padded to the HDFS block boundaries. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Format<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The version of the file to write. The possible values are `V0_11` and `V0_12`. The default is `V0_12`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Padding<wbr>Tolerance</span>
        <span class="property-indicator"></span>
        <span class="property-type">double?</span>
    </dt>
    <dd>{{% md %}}A float between 0 and 1 that defines the tolerance for block padding as a decimal fraction of stripe size. The default value is `0.05`, which means 5 percent of stripe size. For the default values of 64 MiB ORC stripes and 256 MiB HDFS blocks, the default block padding tolerance of 5 percent reserves a maximum of 3.2 MiB for padding within the 256 MiB block. In such a case, if the available size within the block is more than 3.2 MiB, a new, smaller stripe is inserted to fit within that space. This ensures that no stripe crosses block boundaries and causes remote reads within a node-local task. Kinesis Data Firehose ignores this parameter when `enable_padding` is `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Row<wbr>Index<wbr>Stride</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The number of rows between index entries. The default is `10000` and the minimum is `1000`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Stripe<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The number of bytes in each stripe. The default is 64 MiB and the minimum is 8 MiB.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The Hadoop Distributed File System (HDFS) block size. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is 256 MiB and the minimum is 64 MiB. Kinesis Data Firehose uses this value for padding calculations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bloom<wbr>Filter<wbr>Columns</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of column names for which you want Kinesis Data Firehose to create bloom filters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bloom<wbr>Filter<wbr>False<wbr>Positive<wbr>Probability</span>
        <span class="property-indicator"></span>
        <span class="property-type">*float64</span>
    </dt>
    <dd>{{% md %}}The Bloom filter false positive probability (FPP). The lower the FPP, the bigger the Bloom filter. The default value is `0.05`, the minimum is `0`, and the maximum is `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The compression code to use over data blocks. The possible values are `UNCOMPRESSED`, `SNAPPY`, and `GZIP`, with the default being `SNAPPY`. Use `SNAPPY` for higher decompression speed. Use `GZIP` if the compression ratio is more important than speed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dictionary<wbr>Key<wbr>Threshold</span>
        <span class="property-indicator"></span>
        <span class="property-type">*float64</span>
    </dt>
    <dd>{{% md %}}A float that represents the fraction of the total number of non-null rows. To turn off dictionary encoding, set this fraction to a number that is less than the number of distinct keys in a dictionary. To always use dictionary encoding, set this threshold to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enable<wbr>Padding</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Set this to `true` to indicate that you want stripes to be padded to the HDFS block boundaries. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Format<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The version of the file to write. The possible values are `V0_11` and `V0_12`. The default is `V0_12`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Padding<wbr>Tolerance</span>
        <span class="property-indicator"></span>
        <span class="property-type">*float64</span>
    </dt>
    <dd>{{% md %}}A float between 0 and 1 that defines the tolerance for block padding as a decimal fraction of stripe size. The default value is `0.05`, which means 5 percent of stripe size. For the default values of 64 MiB ORC stripes and 256 MiB HDFS blocks, the default block padding tolerance of 5 percent reserves a maximum of 3.2 MiB for padding within the 256 MiB block. In such a case, if the available size within the block is more than 3.2 MiB, a new, smaller stripe is inserted to fit within that space. This ensures that no stripe crosses block boundaries and causes remote reads within a node-local task. Kinesis Data Firehose ignores this parameter when `enable_padding` is `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Row<wbr>Index<wbr>Stride</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The number of rows between index entries. The default is `10000` and the minimum is `1000`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Stripe<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The number of bytes in each stripe. The default is 64 MiB and the minimum is 8 MiB.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The Hadoop Distributed File System (HDFS) block size. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is 256 MiB and the minimum is 64 MiB. Kinesis Data Firehose uses this value for padding calculations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bloom<wbr>Filter<wbr>Columns</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of column names for which you want Kinesis Data Firehose to create bloom filters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bloom<wbr>Filter<wbr>False<wbr>Positive<wbr>Probability</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The Bloom filter false positive probability (FPP). The lower the FPP, the bigger the Bloom filter. The default value is `0.05`, the minimum is `0`, and the maximum is `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression code to use over data blocks. The possible values are `UNCOMPRESSED`, `SNAPPY`, and `GZIP`, with the default being `SNAPPY`. Use `SNAPPY` for higher decompression speed. Use `GZIP` if the compression ratio is more important than speed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dictionary<wbr>Key<wbr>Threshold</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}A float that represents the fraction of the total number of non-null rows. To turn off dictionary encoding, set this fraction to a number that is less than the number of distinct keys in a dictionary. To always use dictionary encoding, set this threshold to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enable<wbr>Padding</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Set this to `true` to indicate that you want stripes to be padded to the HDFS block boundaries. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>format<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The version of the file to write. The possible values are `V0_11` and `V0_12`. The default is `V0_12`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>padding<wbr>Tolerance</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}A float between 0 and 1 that defines the tolerance for block padding as a decimal fraction of stripe size. The default value is `0.05`, which means 5 percent of stripe size. For the default values of 64 MiB ORC stripes and 256 MiB HDFS blocks, the default block padding tolerance of 5 percent reserves a maximum of 3.2 MiB for padding within the 256 MiB block. In such a case, if the available size within the block is more than 3.2 MiB, a new, smaller stripe is inserted to fit within that space. This ensures that no stripe crosses block boundaries and causes remote reads within a node-local task. Kinesis Data Firehose ignores this parameter when `enable_padding` is `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>row<wbr>Index<wbr>Stride</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The number of rows between index entries. The default is `10000` and the minimum is `1000`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>stripe<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The number of bytes in each stripe. The default is 64 MiB and the minimum is 8 MiB.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The Hadoop Distributed File System (HDFS) block size. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is 256 MiB and the minimum is 64 MiB. Kinesis Data Firehose uses this value for padding calculations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bloom<wbr>Filter<wbr>Columns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of column names for which you want Kinesis Data Firehose to create bloom filters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bloom<wbr>Filter<wbr>False<wbr>Positive<wbr>Probability</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The Bloom filter false positive probability (FPP). The lower the FPP, the bigger the Bloom filter. The default value is `0.05`, the minimum is `0`, and the maximum is `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The compression code to use over data blocks. The possible values are `UNCOMPRESSED`, `SNAPPY`, and `GZIP`, with the default being `SNAPPY`. Use `SNAPPY` for higher decompression speed. Use `GZIP` if the compression ratio is more important than speed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dictionary<wbr>Key<wbr>Threshold</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}A float that represents the fraction of the total number of non-null rows. To turn off dictionary encoding, set this fraction to a number that is less than the number of distinct keys in a dictionary. To always use dictionary encoding, set this threshold to `1`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enable<wbr>Padding</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Set this to `true` to indicate that you want stripes to be padded to the HDFS block boundaries. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>format<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The version of the file to write. The possible values are `V0_11` and `V0_12`. The default is `V0_12`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>padding<wbr>Tolerance</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}A float between 0 and 1 that defines the tolerance for block padding as a decimal fraction of stripe size. The default value is `0.05`, which means 5 percent of stripe size. For the default values of 64 MiB ORC stripes and 256 MiB HDFS blocks, the default block padding tolerance of 5 percent reserves a maximum of 3.2 MiB for padding within the 256 MiB block. In such a case, if the available size within the block is more than 3.2 MiB, a new, smaller stripe is inserted to fit within that space. This ensures that no stripe crosses block boundaries and causes remote reads within a node-local task. Kinesis Data Firehose ignores this parameter when `enable_padding` is `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>row<wbr>Index<wbr>Stride</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of rows between index entries. The default is `10000` and the minimum is `1000`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>stripe<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of bytes in each stripe. The default is 64 MiB and the minimum is 8 MiB.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Output<wbr>Format<wbr>Configuration<wbr>Serializer<wbr>Parquet<wbr>Ser<wbr>De</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializerParquetSerDe">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializerParquetSerDe">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializerParquetSerDeArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationOutputFormatConfigurationSerializerParquetSerDeOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The Hadoop Distributed File System (HDFS) block size. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is 256 MiB and the minimum is 64 MiB. Kinesis Data Firehose uses this value for padding calculations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression code to use over data blocks. The possible values are `UNCOMPRESSED`, `SNAPPY`, and `GZIP`, with the default being `SNAPPY`. Use `SNAPPY` for higher decompression speed. Use `GZIP` if the compression ratio is more important than speed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enable<wbr>Dictionary<wbr>Compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Indicates whether to enable dictionary compression.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Max<wbr>Padding<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The maximum amount of padding to apply. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is `0`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Page<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The Parquet page size. Column chunks are divided into pages. A page is conceptually an indivisible unit (in terms of compression and encoding). The minimum value is 64 KiB and the default is 1 MiB.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Writer<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates the version of row format to output. The possible values are `V1` and `V2`. The default is `V1`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The Hadoop Distributed File System (HDFS) block size. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is 256 MiB and the minimum is 64 MiB. Kinesis Data Firehose uses this value for padding calculations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The compression code to use over data blocks. The possible values are `UNCOMPRESSED`, `SNAPPY`, and `GZIP`, with the default being `SNAPPY`. Use `SNAPPY` for higher decompression speed. Use `GZIP` if the compression ratio is more important than speed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enable<wbr>Dictionary<wbr>Compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether to enable dictionary compression.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Max<wbr>Padding<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The maximum amount of padding to apply. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is `0`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Page<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The Parquet page size. Column chunks are divided into pages. A page is conceptually an indivisible unit (in terms of compression and encoding). The minimum value is 64 KiB and the default is 1 MiB.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Writer<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Indicates the version of row format to output. The possible values are `V1` and `V2`. The default is `V1`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The Hadoop Distributed File System (HDFS) block size. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is 256 MiB and the minimum is 64 MiB. Kinesis Data Firehose uses this value for padding calculations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression code to use over data blocks. The possible values are `UNCOMPRESSED`, `SNAPPY`, and `GZIP`, with the default being `SNAPPY`. Use `SNAPPY` for higher decompression speed. Use `GZIP` if the compression ratio is more important than speed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enable<wbr>Dictionary<wbr>Compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Indicates whether to enable dictionary compression.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>max<wbr>Padding<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The maximum amount of padding to apply. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is `0`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>page<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The Parquet page size. Column chunks are divided into pages. A page is conceptually an indivisible unit (in terms of compression and encoding). The minimum value is 64 KiB and the default is 1 MiB.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>writer<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates the version of row format to output. The possible values are `V1` and `V2`. The default is `V1`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>block<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The Hadoop Distributed File System (HDFS) block size. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is 256 MiB and the minimum is 64 MiB. Kinesis Data Firehose uses this value for padding calculations.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The compression code to use over data blocks. The possible values are `UNCOMPRESSED`, `SNAPPY`, and `GZIP`, with the default being `SNAPPY`. Use `SNAPPY` for higher decompression speed. Use `GZIP` if the compression ratio is more important than speed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enable<wbr>Dictionary<wbr>Compression</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether to enable dictionary compression.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>max<wbr>Padding<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The maximum amount of padding to apply. This is useful if you intend to copy the data from Amazon S3 to HDFS before querying. The default is `0`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>page<wbr>Size<wbr>Bytes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The Parquet page size. Column chunks are divided into pages. A page is conceptually an indivisible unit (in terms of compression and encoding). The minimum value is 64 KiB and the default is 1 MiB.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>writer<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates the version of row format to output. The possible values are `V1` and `V2`. The default is `V1`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Data<wbr>Format<wbr>Conversion<wbr>Configuration<wbr>Schema<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationSchemaConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationSchemaConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationSchemaConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationDataFormatConversionConfigurationSchemaConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Catalog<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the AWS Glue Data Catalog. If you don't supply this, the AWS account ID is used by default.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the AWS Glue database that contains the schema for the output data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If you don't specify an AWS Region, the default is the current region.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Table<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the AWS Glue table that contains the column information that constitutes your data schema.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Catalog<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ID of the AWS Glue Data Catalog. If you don't supply this, the AWS account ID is used by default.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the AWS Glue database that contains the schema for the output data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}If you don't specify an AWS Region, the default is the current region.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Table<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the AWS Glue table that contains the column information that constitutes your data schema.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>catalog<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the AWS Glue Data Catalog. If you don't supply this, the AWS account ID is used by default.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>database<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the AWS Glue database that contains the schema for the output data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If you don't specify an AWS Region, the default is the current region.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>table<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the AWS Glue table that contains the column information that constitutes your data schema.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>version<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>catalog_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the AWS Glue Data Catalog. If you don't supply this, the AWS account ID is used by default.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>database_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the name of the AWS Glue database that contains the schema for the output data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}If you don't specify an AWS Region, the default is the current region.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>table_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the AWS Glue table that contains the column information that constitutes your data schema.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>version_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the table version for the output data schema. Defaults to `LATEST`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfigurationprocessor">List&lt;Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfigurationprocessor">[]Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Processor</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfigurationprocessor">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Processor[]?</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfigurationprocessor">List[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Processor]</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Processor</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfigurationProcessor">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfigurationProcessor">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfigurationProcessorArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfigurationProcessorOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfigurationprocessorparameter">List&lt;Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfigurationprocessorparameter">[]Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfigurationprocessorparameter">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter[]?</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurationprocessingconfigurationprocessorparameter">List[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter]</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfigurationProcessorParameter">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfigurationProcessorParameter">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfigurationProcessorParameterArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationProcessingConfigurationProcessorParameterOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>S3Backup<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationS3BackupConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationS3BackupConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationS3BackupConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationS3BackupConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurations3backupconfigurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>S3Backup<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurations3backupconfigurationcloudwatchloggingoptions">*Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>S3Backup<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurations3backupconfigurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>S3Backup<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch_<wbr>logging_<wbr>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamextendeds3configurations3backupconfigurationcloudwatchloggingoptions">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>S3Backup<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>key_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Extended<wbr>S3Configuration<wbr>S3Backup<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamExtendedS3ConfigurationS3BackupConfigurationCloudwatchLoggingOptions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamExtendedS3ConfigurationS3BackupConfigurationCloudwatchLoggingOptions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationS3BackupConfigurationCloudwatchLoggingOptionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamExtendedS3ConfigurationS3BackupConfigurationCloudwatchLoggingOptionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Kinesis<wbr>Source<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamKinesisSourceConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamKinesisSourceConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamKinesisSourceConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamKinesisSourceConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Kinesis<wbr>Stream<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The kinesis stream used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the role that provides access to the source Kinesis stream.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Kinesis<wbr>Stream<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The kinesis stream used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the role that provides access to the source Kinesis stream.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>kinesis<wbr>Stream<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The kinesis stream used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the role that provides access to the source Kinesis stream.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>kinesis<wbr>Stream<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The kinesis stream used as the source of the firehose delivery stream.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the role that provides access to the source Kinesis stream.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamRedshiftConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamRedshiftConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Cluster<wbr>Jdbcurl</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The jdbcurl of the redshift cluster.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Copy<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Copy options for copying the data from the s3 intermediate bucket into redshift, for example to change the default delimiter. For valid values, see the [AWS documentation](http://docs.aws.amazon.com/firehose/latest/APIReference/API_CopyCommand.html)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Data<wbr>Table<wbr>Columns</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The data table columns that will be targeted by the copy command.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Data<wbr>Table<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the table in the redshift cluster that the s3 bucket will copy to.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The password for the username above.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The length of time during which Firehose retries delivery after a failure, starting from the initial request and including the first attempt. The default value is 3600 seconds (60 minutes). Firehose does not retry if the value of DurationInSeconds is 0 (zero) or if the first delivery attempt takes longer than the current value.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The arn of the role the stream assumes.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurations3backupconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>S3Backup<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The configuration for backup in Amazon S3. Required if `s3_backup_mode` is `Enabled`. Supports the same fields as `s3_configuration` object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Amazon S3 backup mode.  Valid values are `Disabled` and `Enabled`.  Default value is `Disabled`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The username that the firehose delivery stream will assume. It is strongly recommended that the username and password provided is used exclusively for Amazon Kinesis Firehose purposes, and that the permissions for the account are restricted for Amazon Redshift INSERT permissions.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationcloudwatchloggingoptions">*Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Cluster<wbr>Jdbcurl</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The jdbcurl of the redshift cluster.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Copy<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Copy options for copying the data from the s3 intermediate bucket into redshift, for example to change the default delimiter. For valid values, see the [AWS documentation](http://docs.aws.amazon.com/firehose/latest/APIReference/API_CopyCommand.html)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Data<wbr>Table<wbr>Columns</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The data table columns that will be targeted by the copy command.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Data<wbr>Table<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the table in the redshift cluster that the s3 bucket will copy to.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The password for the username above.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The length of time during which Firehose retries delivery after a failure, starting from the initial request and including the first attempt. The default value is 3600 seconds (60 minutes). Firehose does not retry if the value of DurationInSeconds is 0 (zero) or if the first delivery attempt takes longer than the current value.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The arn of the role the stream assumes.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurations3backupconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>S3Backup<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}The configuration for backup in Amazon S3. Required if `s3_backup_mode` is `Enabled`. Supports the same fields as `s3_configuration` object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Amazon S3 backup mode.  Valid values are `Disabled` and `Enabled`.  Default value is `Disabled`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The username that the firehose delivery stream will assume. It is strongly recommended that the username and password provided is used exclusively for Amazon Kinesis Firehose purposes, and that the permissions for the account are restricted for Amazon Redshift INSERT permissions.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>cluster<wbr>Jdbcurl</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The jdbcurl of the redshift cluster.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>copy<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Copy options for copying the data from the s3 intermediate bucket into redshift, for example to change the default delimiter. For valid values, see the [AWS documentation](http://docs.aws.amazon.com/firehose/latest/APIReference/API_CopyCommand.html)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>data<wbr>Table<wbr>Columns</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The data table columns that will be targeted by the copy command.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>data<wbr>Table<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the table in the redshift cluster that the s3 bucket will copy to.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The password for the username above.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The length of time during which Firehose retries delivery after a failure, starting from the initial request and including the first attempt. The default value is 3600 seconds (60 minutes). Firehose does not retry if the value of DurationInSeconds is 0 (zero) or if the first delivery attempt takes longer than the current value.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The arn of the role the stream assumes.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurations3backupconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>S3Backup<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}The configuration for backup in Amazon S3. Required if `s3_backup_mode` is `Enabled`. Supports the same fields as `s3_configuration` object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Amazon S3 backup mode.  Valid values are `Disabled` and `Enabled`.  Default value is `Disabled`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The username that the firehose delivery stream will assume. It is strongly recommended that the username and password provided is used exclusively for Amazon Kinesis Firehose purposes, and that the permissions for the account are restricted for Amazon Redshift INSERT permissions.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch_<wbr>logging_<wbr>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationcloudwatchloggingoptions">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>cluster<wbr>Jdbcurl</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The jdbcurl of the redshift cluster.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>copy<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Copy options for copying the data from the s3 intermediate bucket into redshift, for example to change the default delimiter. For valid values, see the [AWS documentation](http://docs.aws.amazon.com/firehose/latest/APIReference/API_CopyCommand.html)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>data<wbr>Table<wbr>Columns</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The data table columns that will be targeted by the copy command.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>data<wbr>Table<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the table in the redshift cluster that the s3 bucket will copy to.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>password</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The password for the username above.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The length of time during which Firehose retries delivery after a failure, starting from the initial request and including the first attempt. The default value is 3600 seconds (60 minutes). Firehose does not retry if the value of DurationInSeconds is 0 (zero) or if the first delivery attempt takes longer than the current value.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The arn of the role the stream assumes.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurations3backupconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>S3Backup<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}The configuration for backup in Amazon S3. Required if `s3_backup_mode` is `Enabled`. Supports the same fields as `s3_configuration` object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Amazon S3 backup mode.  Valid values are `Disabled` and `Enabled`.  Default value is `Disabled`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>username</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The username that the firehose delivery stream will assume. It is strongly recommended that the username and password provided is used exclusively for Amazon Kinesis Firehose purposes, and that the permissions for the account are restricted for Amazon Redshift INSERT permissions.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamRedshiftConfigurationCloudwatchLoggingOptions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamRedshiftConfigurationCloudwatchLoggingOptions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationCloudwatchLoggingOptionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationCloudwatchLoggingOptionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfigurationprocessor">List&lt;Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfigurationprocessor">[]Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfigurationprocessor">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor[]?</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfigurationprocessor">List[Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor]</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfigurationProcessor">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfigurationProcessor">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfigurationProcessorArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfigurationProcessorOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfigurationprocessorparameter">List&lt;Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfigurationprocessorparameter">[]Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfigurationprocessorparameter">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter[]?</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurationprocessingconfigurationprocessorparameter">List[Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter]</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfigurationProcessorParameter">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfigurationProcessorParameter">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfigurationProcessorParameterArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationProcessingConfigurationProcessorParameterOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>S3Backup<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamRedshiftConfigurationS3BackupConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamRedshiftConfigurationS3BackupConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationS3BackupConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationS3BackupConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurations3backupconfigurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>S3Backup<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurations3backupconfigurationcloudwatchloggingoptions">*Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>S3Backup<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurations3backupconfigurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>S3Backup<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch_<wbr>logging_<wbr>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamredshiftconfigurations3backupconfigurationcloudwatchloggingoptions">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>S3Backup<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>key_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Redshift<wbr>Configuration<wbr>S3Backup<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamRedshiftConfigurationS3BackupConfigurationCloudwatchLoggingOptions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamRedshiftConfigurationS3BackupConfigurationCloudwatchLoggingOptions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationS3BackupConfigurationCloudwatchLoggingOptionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamRedshiftConfigurationS3BackupConfigurationCloudwatchLoggingOptionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamS3Configuration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamS3Configuration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamS3ConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamS3ConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configurationcloudwatchloggingoptions">*Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>bucket<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data for the specified period of time, in seconds, before delivering it to the destination. The default value is 300.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>buffer<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Buffer incoming data to the specified size, in MBs, before delivering it to the destination. The default value is 5.
We recommend setting SizeInMBs to a value greater than the amount of data you typically ingest into the delivery stream in 10 seconds. For example, if you typically ingest data at 1 MB/sec set SizeInMBs to be 10 MB or higher.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch_<wbr>logging_<wbr>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreams3configurationcloudwatchloggingoptions">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compression<wbr>Format</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The compression format. If no value is specified, the default is UNCOMPRESSED. Other supported values are GZIP, ZIP & Snappy. If the destination is redshift you cannot use ZIP or Snappy.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>key_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the KMS key ARN the stream will use to encrypt data. If not set, no encryption will
be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The "YYYY/MM/DD/HH" time format prefix is automatically used for delivered S3 files. You can specify an extra prefix to be added in front of the time format prefix. Note that if the prefix ends with a slash, it appears as a folder in the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The role that Kinesis Data Firehose can use to access AWS Glue. This role must be in the same account you use for Kinesis Data Firehose. Cross-account roles aren't allowed.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>S3Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamS3ConfigurationCloudwatchLoggingOptions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamS3ConfigurationCloudwatchLoggingOptions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamS3ConfigurationCloudwatchLoggingOptionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamS3ConfigurationCloudwatchLoggingOptionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Server<wbr>Side<wbr>Encryption</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamServerSideEncryption">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamServerSideEncryption">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamServerSideEncryptionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamServerSideEncryptionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Whether to enable encryption at rest. Default is `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Whether to enable encryption at rest. Default is `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Whether to enable encryption at rest. Default is `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Whether to enable encryption at rest. Default is `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamSplunkConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamSplunkConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamSplunkConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamSplunkConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hec<wbr>Acknowledgment<wbr>Timeout</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The amount of time, in seconds between 180 and 600, that Kinesis Firehose waits to receive an acknowledgment from Splunk after it sends it data.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Hec<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP Event Collector (HEC) endpoint to which Kinesis Firehose sends your data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hec<wbr>Endpoint<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The HEC endpoint type. Valid values are `Raw` or `Event`. The default value is `Raw`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Hec<wbr>Token</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The GUID that you obtain from your Splunk cluster when you create a new HEC endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}After an initial failure to deliver to Splunk, the total amount of time, in seconds between 0 to 7200, during which Firehose re-attempts delivery (including the first attempt).  After this time has elapsed, the failed documents are written to Amazon S3.  The default value is 300s.  There will be no retry if the value is 0.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Defines how documents should be delivered to Amazon S3.  Valid values are `FailedEventsOnly` and `AllEvents`.  Default value is `FailedEventsOnly`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationcloudwatchloggingoptions">*Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hec<wbr>Acknowledgment<wbr>Timeout</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The amount of time, in seconds between 180 and 600, that Kinesis Firehose waits to receive an acknowledgment from Splunk after it sends it data.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Hec<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP Event Collector (HEC) endpoint to which Kinesis Firehose sends your data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hec<wbr>Endpoint<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The HEC endpoint type. Valid values are `Raw` or `Event`. The default value is `Raw`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Hec<wbr>Token</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The GUID that you obtain from your Splunk cluster when you create a new HEC endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfiguration">*Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}After an initial failure to deliver to Splunk, the total amount of time, in seconds between 0 to 7200, during which Firehose re-attempts delivery (including the first attempt).  After this time has elapsed, the failed documents are written to Amazon S3.  The default value is 300s.  There will be no retry if the value is 0.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Defines how documents should be delivered to Amazon S3.  Valid values are `FailedEventsOnly` and `AllEvents`.  Default value is `FailedEventsOnly`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Logging<wbr>Options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationcloudwatchloggingoptions">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options?</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hec<wbr>Acknowledgment<wbr>Timeout</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The amount of time, in seconds between 180 and 600, that Kinesis Firehose waits to receive an acknowledgment from Splunk after it sends it data.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>hec<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP Event Collector (HEC) endpoint to which Kinesis Firehose sends your data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hec<wbr>Endpoint<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The HEC endpoint type. Valid values are `Raw` or `Event`. The default value is `Raw`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>hec<wbr>Token</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The GUID that you obtain from your Splunk cluster when you create a new HEC endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfiguration">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}After an initial failure to deliver to Splunk, the total amount of time, in seconds between 0 to 7200, during which Firehose re-attempts delivery (including the first attempt).  After this time has elapsed, the failed documents are written to Amazon S3.  The default value is 300s.  There will be no retry if the value is 0.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Defines how documents should be delivered to Amazon S3.  Valid values are `FailedEventsOnly` and `AllEvents`.  Default value is `FailedEventsOnly`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch_<wbr>logging_<wbr>options</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationcloudwatchloggingoptions">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options]</a></span>
    </dt>
    <dd>{{% md %}}The CloudWatch Logging Options for the delivery stream. More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hec<wbr>Acknowledgment<wbr>Timeout</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The amount of time, in seconds between 180 and 600, that Kinesis Firehose waits to receive an acknowledgment from Splunk after it sends it data.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>hec<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The HTTP Event Collector (HEC) endpoint to which Kinesis Firehose sends your data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hec<wbr>Endpoint<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The HEC endpoint type. Valid values are `Raw` or `Event`. The default value is `Raw`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>hec<wbr>Token</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The GUID that you obtain from your Splunk cluster when you create a new HEC endpoint.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processing<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfiguration">Dict[Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}The data processing configuration.  More details are given below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>retry<wbr>Duration</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}After an initial failure to deliver to Splunk, the total amount of time, in seconds between 0 to 7200, during which Firehose re-attempts delivery (including the first attempt).  After this time has elapsed, the failed documents are written to Amazon S3.  The default value is 300s.  There will be no retry if the value is 0.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Backup<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Defines how documents should be delivered to Amazon S3.  Valid values are `FailedEventsOnly` and `AllEvents`.  Default value is `FailedEventsOnly`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Cloudwatch<wbr>Logging<wbr>Options</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamSplunkConfigurationCloudwatchLoggingOptions">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamSplunkConfigurationCloudwatchLoggingOptions">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamSplunkConfigurationCloudwatchLoggingOptionsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamSplunkConfigurationCloudwatchLoggingOptionsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Group<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables the logging. Defaults to `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log_<wbr>group_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch group name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>log<wbr>Stream<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The CloudWatch log stream name for logging. This value is required if `enabled` is true.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamSplunkConfigurationProcessingConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamSplunkConfigurationProcessingConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamSplunkConfigurationProcessingConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamSplunkConfigurationProcessingConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfigurationprocessor">List&lt;Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfigurationprocessor">[]Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfigurationprocessor">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor[]?</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enables or disables data processing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>processors</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfigurationprocessor">List[Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor]</a></span>
    </dt>
    <dd>{{% md %}}Array of data processors. More details are given below
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamSplunkConfigurationProcessingConfigurationProcessor">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamSplunkConfigurationProcessingConfigurationProcessor">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamSplunkConfigurationProcessingConfigurationProcessorArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamSplunkConfigurationProcessingConfigurationProcessorOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfigurationprocessorparameter">List&lt;Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfigurationprocessorparameter">[]Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfigurationprocessorparameter">Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter[]?</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#firehosedeliverystreamsplunkconfigurationprocessingconfigurationprocessorparameter">List[Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter]</a></span>
    </dt>
    <dd>{{% md %}}Array of processor parameters. More details are given below
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of processor. Valid Values: `Lambda`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Firehose<wbr>Delivery<wbr>Stream<wbr>Splunk<wbr>Configuration<wbr>Processing<wbr>Configuration<wbr>Processor<wbr>Parameter</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#FirehoseDeliveryStreamSplunkConfigurationProcessingConfigurationProcessorParameter">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#FirehoseDeliveryStreamSplunkConfigurationProcessingConfigurationProcessorParameter">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamSplunkConfigurationProcessingConfigurationProcessorParameterArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/kinesis?tab=doc#FirehoseDeliveryStreamSplunkConfigurationProcessingConfigurationProcessorParameterOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameter name. Valid Values: `LambdaArn`, `NumberOfRetries`, `RoleArn`, `BufferSizeInMBs`, `BufferIntervalInSeconds`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>parameter<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Parameter value. Must be between 1 and 512 length (inclusive). When providing a Lambda ARN, you should specify the resource version as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







