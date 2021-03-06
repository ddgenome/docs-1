
---
title: "Bucket"
block_external_search_index: true
---

Provides a S3 bucket resource.

## Example Usage

### Private Bucket w/ Tags

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const bucket = new aws.s3.Bucket("b", {
    acl: "private",
    tags: {
        Environment: "Dev",
        Name: "My bucket",
    },
});
```

### Static Website Hosting

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";
import * as fs from "fs";

const bucket = new aws.s3.Bucket("b", {
    acl: "public-read",
    policy: fs.readFileSync("policy.json", "utf-8"),
    website: {
        errorDocument: "error.html",
        indexDocument: "index.html",
        routingRules: `[{
    "Condition": {
        "KeyPrefixEquals": "docs/"
    },
    "Redirect": {
        "ReplaceKeyPrefixWith": "documents/"
    }
}]
`,
    },
});
```

### Using CORS

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const bucket = new aws.s3.Bucket("b", {
    acl: "public-read",
    corsRules: [{
        allowedHeaders: ["*"],
        allowedMethods: [
            "PUT",
            "POST",
        ],
        allowedOrigins: ["https://s3-website-test.mydomain.com"],
        exposeHeaders: ["ETag"],
        maxAgeSeconds: 3000,
    }],
});
```

### Using versioning

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const bucket = new aws.s3.Bucket("b", {
    acl: "private",
    versioning: {
        enabled: true,
    },
});
```

### Enable Logging

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const logBucket = new aws.s3.Bucket("log_bucket", {
    acl: "log-delivery-write",
});
const bucket = new aws.s3.Bucket("b", {
    acl: "private",
    loggings: [{
        targetBucket: logBucket.id,
        targetPrefix: "log/",
    }],
});
```

### Using object lifecycle

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const bucket = new aws.s3.Bucket("bucket", {
    acl: "private",
    lifecycleRules: [
        {
            enabled: true,
            expiration: {
                days: 90,
            },
            id: "log",
            prefix: "log/",
            tags: {
                autoclean: "true",
                rule: "log",
            },
            transitions: [
                {
                    days: 30,
                    storageClass: "STANDARD_IA", // or "ONEZONE_IA"
                },
                {
                    days: 60,
                    storageClass: "GLACIER",
                },
            ],
        },
        {
            enabled: true,
            expiration: {
                date: "2016-01-12",
            },
            id: "tmp",
            prefix: "tmp/",
        },
    ],
});
const versioningBucket = new aws.s3.Bucket("versioning_bucket", {
    acl: "private",
    lifecycleRules: [{
        enabled: true,
        noncurrentVersionExpiration: {
            days: 90,
        },
        noncurrentVersionTransitions: [
            {
                days: 30,
                storageClass: "STANDARD_IA",
            },
            {
                days: 60,
                storageClass: "GLACIER",
            },
        ],
        prefix: "config/",
    }],
    versioning: {
        enabled: true,
    },
});
```

### Using replication configuration

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const central = new aws.Provider("central", {
    region: "eu-central-1",
});
const replicationRole = new aws.iam.Role("replication", {
    assumeRolePolicy: `{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": "sts:AssumeRole",
      "Principal": {
        "Service": "s3.amazonaws.com"
      },
      "Effect": "Allow",
      "Sid": ""
    }
  ]
}
`,
});
const destination = new aws.s3.Bucket("destination", {
    region: "eu-west-1",
    versioning: {
        enabled: true,
    },
});
const bucket = new aws.s3.Bucket("bucket", {
    acl: "private",
    region: "eu-central-1",
    replicationConfiguration: {
        role: replicationRole.arn,
        rules: [{
            destination: {
                bucket: destination.arn,
                storageClass: "STANDARD",
            },
            id: "foobar",
            prefix: "foo",
            status: "Enabled",
        }],
    },
    versioning: {
        enabled: true,
    },
}, {provider: central});
const replicationPolicy = new aws.iam.Policy("replication", {
    policy: pulumi.interpolate`{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "s3:GetReplicationConfiguration",
        "s3:ListBucket"
      ],
      "Effect": "Allow",
      "Resource": [
        "${bucket.arn}"
      ]
    },
    {
      "Action": [
        "s3:GetObjectVersion",
        "s3:GetObjectVersionAcl"
      ],
      "Effect": "Allow",
      "Resource": [
        "${bucket.arn}/*"
      ]
    },
    {
      "Action": [
        "s3:ReplicateObject",
        "s3:ReplicateDelete"
      ],
      "Effect": "Allow",
      "Resource": "${destination.arn}/*"
    }
  ]
}
`,
});
const replicationRolePolicyAttachment = new aws.iam.RolePolicyAttachment("replication", {
    policyArn: replicationPolicy.arn,
    role: replicationRole.name,
});
```

### Enable Default Server Side Encryption

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const mykey = new aws.kms.Key("mykey", {
    deletionWindowInDays: 10,
    description: "This key is used to encrypt bucket objects",
});
const mybucket = new aws.s3.Bucket("mybucket", {
    serverSideEncryptionConfiguration: {
        rule: {
            applyServerSideEncryptionByDefault: {
                kmsMasterKeyId: mykey.arn,
                sseAlgorithm: "aws:kms",
            },
        },
    },
});
```

### Using ACL policy grants

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const currentUser = aws.getCanonicalUserId();
const bucket = new aws.s3.Bucket("bucket", {
    grants: [
        {
            id: currentUser.id,
            permission: ["FULL_ACCESS"],
            type: "CanonicalUser",
        },
        {
            permission: [
                "READ",
                "WRITE",
            ],
            type: "Group",
            uri: "http://acs.amazonaws.com/groups/s3/LogDelivery",
        },
    ],
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/s3_bucket.html.markdown.



## Create a Bucket Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/s3/#Bucket">Bucket</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/s3/#BucketArgs">BucketArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">Bucket</span><span class="p">(resource_name, opts=None, </span>acceleration_status=None<span class="p">, </span>acl=None<span class="p">, </span>arn=None<span class="p">, </span>bucket=None<span class="p">, </span>bucket_prefix=None<span class="p">, </span>cors_rules=None<span class="p">, </span>force_destroy=None<span class="p">, </span>grants=None<span class="p">, </span>hosted_zone_id=None<span class="p">, </span>lifecycle_rules=None<span class="p">, </span>loggings=None<span class="p">, </span>object_lock_configuration=None<span class="p">, </span>policy=None<span class="p">, </span>region=None<span class="p">, </span>replication_configuration=None<span class="p">, </span>request_payer=None<span class="p">, </span>server_side_encryption_configuration=None<span class="p">, </span>tags=None<span class="p">, </span>versioning=None<span class="p">, </span>website=None<span class="p">, </span>website_domain=None<span class="p">, </span>website_endpoint=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewBucket<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketArgs">BucketArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#Bucket">Bucket</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.S3.Bucket.html">Bucket</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.S3.Inputs.BucketArgs.html">BucketArgs</a></span>? <span class="nx">args = null<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Acceleration<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cors<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">List&lt;Bucket<wbr>Cors<wbr>Rule<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Force<wbr>Destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">List&lt;Bucket<wbr>Grant<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hosted<wbr>Zone<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Lifecycle<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">List&lt;Bucket<wbr>Lifecycle<wbr>Rule<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">List&lt;Bucket<wbr>Logging<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Object<wbr>Lock<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Replication<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">Bucket<wbr>Replication<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Request<wbr>Payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Server<wbr>Side<wbr>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">Bucket<wbr>Versioning<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">Bucket<wbr>Website<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website<wbr>Domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Acceleration<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">interface{}</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cors<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">[]Bucket<wbr>Cors<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Force<wbr>Destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">[]Bucket<wbr>Grant</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hosted<wbr>Zone<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Lifecycle<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">[]Bucket<wbr>Lifecycle<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">[]Bucket<wbr>Logging</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Object<wbr>Lock<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">*Bucket<wbr>Object<wbr>Lock<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">interface{}</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Replication<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">*Bucket<wbr>Replication<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Request<wbr>Payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Server<wbr>Side<wbr>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">*Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">*Bucket<wbr>Versioning</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">*Bucket<wbr>Website</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website<wbr>Domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>acceleration<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">string | CannedAcl</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cors<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">Bucket<wbr>Cors<wbr>Rule[]?</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>force<wbr>Destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">Bucket<wbr>Grant[]?</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hosted<wbr>Zone<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>lifecycle<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">Bucket<wbr>Lifecycle<wbr>Rule[]?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">Bucket<wbr>Logging[]?</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>object<wbr>Lock<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">Bucket<wbr>Object<wbr>Lock<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string | PolicyDocument</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>replication<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">Bucket<wbr>Replication<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>request<wbr>Payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>server<wbr>Side<wbr>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">Bucket<wbr>Versioning?</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">Bucket<wbr>Website?</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website<wbr>Domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>acceleration_<wbr>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket_<wbr>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cors_<wbr>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">List[Bucket<wbr>Cors<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>force_<wbr>destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">List[Bucket<wbr>Grant]</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hosted_<wbr>zone_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>lifecycle_<wbr>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">List[Bucket<wbr>Lifecycle<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">List[Bucket<wbr>Logging]</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>object_<wbr>lock_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">Dict[Bucket<wbr>Object<wbr>Lock<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>replication_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">Dict[Bucket<wbr>Replication<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>request_<wbr>payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>server_<wbr>side_<wbr>encryption_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">Dict[Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">Dict[Bucket<wbr>Versioning]</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">Dict[Bucket<wbr>Website]</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website_<wbr>domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website_<wbr>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## Bucket Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Acceleration<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Bucket<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The bucket domain name. Will be of format `bucketname.s3.amazonaws.com`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Bucket<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Bucket<wbr>Regional<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The bucket region-specific domain name. The bucket domain name including the region name, please refer [here](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) for format. Note: The AWS CloudFront allows specifying S3 region-specific endpoint when creating S3 origin, it will prevent [redirect issues](https://forums.aws.amazon.com/thread.jspa?threadID=216814) from CloudFront to S3 Origin URL.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Cors<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">List&lt;Bucket<wbr>Cors<wbr>Rule&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Force<wbr>Destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">List&lt;Bucket<wbr>Grant&gt;?</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hosted<wbr>Zone<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Lifecycle<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">List&lt;Bucket<wbr>Lifecycle<wbr>Rule&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">List&lt;Bucket<wbr>Logging&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Object<wbr>Lock<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">Bucket<wbr>Object<wbr>Lock<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Replication<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">Bucket<wbr>Replication<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Request<wbr>Payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Server<wbr>Side<wbr>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">Bucket<wbr>Versioning</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">Bucket<wbr>Website?</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Website<wbr>Domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Website<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Acceleration<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Bucket<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The bucket domain name. Will be of format `bucketname.s3.amazonaws.com`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Bucket<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Bucket<wbr>Regional<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The bucket region-specific domain name. The bucket domain name including the region name, please refer [here](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) for format. Note: The AWS CloudFront allows specifying S3 region-specific endpoint when creating S3 origin, it will prevent [redirect issues](https://forums.aws.amazon.com/thread.jspa?threadID=216814) from CloudFront to S3 Origin URL.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Cors<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">[]Bucket<wbr>Cors<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Force<wbr>Destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">[]Bucket<wbr>Grant</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Hosted<wbr>Zone<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Lifecycle<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">[]Bucket<wbr>Lifecycle<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">[]Bucket<wbr>Logging</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Object<wbr>Lock<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">*Bucket<wbr>Object<wbr>Lock<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Replication<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">*Bucket<wbr>Replication<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Request<wbr>Payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Server<wbr>Side<wbr>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">*Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">Bucket<wbr>Versioning</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">*Bucket<wbr>Website</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Website<wbr>Domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Website<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>acceleration<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>bucket<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The bucket domain name. Will be of format `bucketname.s3.amazonaws.com`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>bucket<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>bucket<wbr>Regional<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The bucket region-specific domain name. The bucket domain name including the region name, please refer [here](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) for format. Note: The AWS CloudFront allows specifying S3 region-specific endpoint when creating S3 origin, it will prevent [redirect issues](https://forums.aws.amazon.com/thread.jspa?threadID=216814) from CloudFront to S3 Origin URL.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>cors<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">Bucket<wbr>Cors<wbr>Rule[]?</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>force<wbr>Destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">Bucket<wbr>Grant[]?</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hosted<wbr>Zone<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>lifecycle<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">Bucket<wbr>Lifecycle<wbr>Rule[]?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">Bucket<wbr>Logging[]?</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>object<wbr>Lock<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">Bucket<wbr>Object<wbr>Lock<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>replication<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">Bucket<wbr>Replication<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>request<wbr>Payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>server<wbr>Side<wbr>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">Bucket<wbr>Versioning</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">Bucket<wbr>Website?</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>website<wbr>Domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>website<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>acceleration_<wbr>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>bucket_<wbr>domain_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The bucket domain name. Will be of format `bucketname.s3.amazonaws.com`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>bucket_<wbr>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>bucket_<wbr>regional_<wbr>domain_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The bucket region-specific domain name. The bucket domain name including the region name, please refer [here](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) for format. Note: The AWS CloudFront allows specifying S3 region-specific endpoint when creating S3 origin, it will prevent [redirect issues](https://forums.aws.amazon.com/thread.jspa?threadID=216814) from CloudFront to S3 Origin URL.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>cors_<wbr>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">List[Bucket<wbr>Cors<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>force_<wbr>destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">List[Bucket<wbr>Grant]</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>hosted_<wbr>zone_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>lifecycle_<wbr>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">List[Bucket<wbr>Lifecycle<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">List[Bucket<wbr>Logging]</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>object_<wbr>lock_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">Dict[Bucket<wbr>Object<wbr>Lock<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>replication_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">Dict[Bucket<wbr>Replication<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>request_<wbr>payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>server_<wbr>side_<wbr>encryption_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">Dict[Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">Dict[Bucket<wbr>Versioning]</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">Dict[Bucket<wbr>Website]</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>website_<wbr>domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>website_<wbr>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing Bucket Resource

Get an existing Bucket resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/s3/#BucketState">BucketState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/s3/#Bucket">Bucket</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>acceleration_status=None<span class="p">, </span>acl=None<span class="p">, </span>arn=None<span class="p">, </span>bucket=None<span class="p">, </span>bucket_domain_name=None<span class="p">, </span>bucket_prefix=None<span class="p">, </span>bucket_regional_domain_name=None<span class="p">, </span>cors_rules=None<span class="p">, </span>force_destroy=None<span class="p">, </span>grants=None<span class="p">, </span>hosted_zone_id=None<span class="p">, </span>lifecycle_rules=None<span class="p">, </span>loggings=None<span class="p">, </span>object_lock_configuration=None<span class="p">, </span>policy=None<span class="p">, </span>region=None<span class="p">, </span>replication_configuration=None<span class="p">, </span>request_payer=None<span class="p">, </span>server_side_encryption_configuration=None<span class="p">, </span>tags=None<span class="p">, </span>versioning=None<span class="p">, </span>website=None<span class="p">, </span>website_domain=None<span class="p">, </span>website_endpoint=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetBucket<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketState">BucketState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#Bucket">Bucket</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.S3.Bucket.html">Bucket</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.S3.BucketState.html">BucketState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Acceleration<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The bucket domain name. Will be of format `bucketname.s3.amazonaws.com`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Regional<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The bucket region-specific domain name. The bucket domain name including the region name, please refer [here](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) for format. Note: The AWS CloudFront allows specifying S3 region-specific endpoint when creating S3 origin, it will prevent [redirect issues](https://forums.aws.amazon.com/thread.jspa?threadID=216814) from CloudFront to S3 Origin URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cors<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">List&lt;Bucket<wbr>Cors<wbr>Rule<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Force<wbr>Destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">List&lt;Bucket<wbr>Grant<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hosted<wbr>Zone<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Lifecycle<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">List&lt;Bucket<wbr>Lifecycle<wbr>Rule<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">List&lt;Bucket<wbr>Logging<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Object<wbr>Lock<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Replication<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">Bucket<wbr>Replication<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Request<wbr>Payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Server<wbr>Side<wbr>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">Bucket<wbr>Versioning<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">Bucket<wbr>Website<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website<wbr>Domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Acceleration<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">interface{}</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The bucket domain name. Will be of format `bucketname.s3.amazonaws.com`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bucket<wbr>Regional<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The bucket region-specific domain name. The bucket domain name including the region name, please refer [here](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) for format. Note: The AWS CloudFront allows specifying S3 region-specific endpoint when creating S3 origin, it will prevent [redirect issues](https://forums.aws.amazon.com/thread.jspa?threadID=216814) from CloudFront to S3 Origin URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cors<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">[]Bucket<wbr>Cors<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Force<wbr>Destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">[]Bucket<wbr>Grant</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Hosted<wbr>Zone<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Lifecycle<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">[]Bucket<wbr>Lifecycle<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">[]Bucket<wbr>Logging</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Object<wbr>Lock<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">*Bucket<wbr>Object<wbr>Lock<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">interface{}</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Region</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Replication<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">*Bucket<wbr>Replication<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Request<wbr>Payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Server<wbr>Side<wbr>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">*Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">*Bucket<wbr>Versioning</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">*Bucket<wbr>Website</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website<wbr>Domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Website<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>acceleration<wbr>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">string | CannedAcl</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The bucket domain name. Will be of format `bucketname.s3.amazonaws.com`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket<wbr>Regional<wbr>Domain<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The bucket region-specific domain name. The bucket domain name including the region name, please refer [here](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) for format. Note: The AWS CloudFront allows specifying S3 region-specific endpoint when creating S3 origin, it will prevent [redirect issues](https://forums.aws.amazon.com/thread.jspa?threadID=216814) from CloudFront to S3 Origin URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cors<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">Bucket<wbr>Cors<wbr>Rule[]?</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>force<wbr>Destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">Bucket<wbr>Grant[]?</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hosted<wbr>Zone<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>lifecycle<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">Bucket<wbr>Lifecycle<wbr>Rule[]?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">Bucket<wbr>Logging[]?</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>object<wbr>Lock<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">Bucket<wbr>Object<wbr>Lock<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string | PolicyDocument</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>replication<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">Bucket<wbr>Replication<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>request<wbr>Payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>server<wbr>Side<wbr>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">Bucket<wbr>Versioning?</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">Bucket<wbr>Website?</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website<wbr>Domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website<wbr>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>acceleration_<wbr>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Sets the accelerate configuration of an existing bucket. Can be `Enabled` or `Suspended`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>acl</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}The [canned ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) to apply. Defaults to "private".  Conflicts with `grant`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the bucket. Will be of format `arn:aws:s3:::bucketname`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the bucket. If omitted, this provider will assign a random, unique name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket_<wbr>domain_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The bucket domain name. Will be of format `bucketname.s3.amazonaws.com`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket_<wbr>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Creates a unique bucket name beginning with the specified prefix. Conflicts with `bucket`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bucket_<wbr>regional_<wbr>domain_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The bucket region-specific domain name. The bucket domain name including the region name, please refer [here](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) for format. Note: The AWS CloudFront allows specifying S3 region-specific endpoint when creating S3 origin, it will prevent [redirect issues](https://forums.aws.amazon.com/thread.jspa?threadID=216814) from CloudFront to S3 Origin URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cors_<wbr>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketcorsrule">List[Bucket<wbr>Cors<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}A rule of [Cross-Origin Resource Sharing](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>force_<wbr>destroy</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}A boolean that indicates all objects (including any [locked objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html)) should be deleted from the bucket so that the bucket can be destroyed without error. These objects are *not* recoverable.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>grants</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketgrant">List[Bucket<wbr>Grant]</a></span>
    </dt>
    <dd>{{% md %}}An [ACL policy grant](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#sample-acl) (documented below). Conflicts with `acl`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>hosted_<wbr>zone_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The [Route 53 Hosted Zone ID](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_website_region_endpoints) for this bucket's region.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>lifecycle_<wbr>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerule">List[Bucket<wbr>Lifecycle<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [object lifecycle management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>loggings</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlogging">List[Bucket<wbr>Logging]</a></span>
    </dt>
    <dd>{{% md %}}A settings of [bucket logging](https://docs.aws.amazon.com/AmazonS3/latest/UG/ManagingBucketLogging.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>object_<wbr>lock_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfiguration">Dict[Bucket<wbr>Object<wbr>Lock<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [S3 object locking](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A valid [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) JSON document.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>region</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}If specified, the AWS region this bucket should reside in. Otherwise, the region used by the callee.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>replication_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfiguration">Dict[Bucket<wbr>Replication<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [replication configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>request_<wbr>payer</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies who should bear the cost of Amazon S3 data transfer.
Can be either `BucketOwner` or `Requester`. By default, the owner of the S3 bucket would incur
the costs of any data transfer. See [Requester Pays Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)
developer guide for more information.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>server_<wbr>side_<wbr>encryption_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfiguration">Dict[Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}A configuration of [server-side encryption configuration](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags to assign to the bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>versioning</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketversioning">Dict[Bucket<wbr>Versioning]</a></span>
    </dt>
    <dd>{{% md %}}A state of [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) (documented below)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketwebsite">Dict[Bucket<wbr>Website]</a></span>
    </dt>
    <dd>{{% md %}}A website object (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website_<wbr>domain</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The domain of the website endpoint, if the bucket is configured with a website. If not, this will be an empty string. This is used to create Route 53 alias records.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>website_<wbr>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The website endpoint, if the bucket is configured with a website. If not, this will be an empty string.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Bucket<wbr>Cors<wbr>Rule</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketCorsRule">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketCorsRule">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketCorsRuleArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketCorsRuleOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Specifies which headers are allowed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Allowed<wbr>Methods</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}Specifies which methods are allowed. Can be `GET`, `PUT`, `POST`, `DELETE` or `HEAD`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Allowed<wbr>Origins</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}Specifies which origins are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Expose<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}Specifies expose header in the response.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Max<wbr>Age<wbr>Seconds</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies time in seconds that browser can cache the response for a preflight request.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Specifies which headers are allowed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Allowed<wbr>Methods</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Specifies which methods are allowed. Can be `GET`, `PUT`, `POST`, `DELETE` or `HEAD`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Allowed<wbr>Origins</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Specifies which origins are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Expose<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}Specifies expose header in the response.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Max<wbr>Age<wbr>Seconds</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies time in seconds that browser can cache the response for a preflight request.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allowed<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Specifies which headers are allowed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>allowed<wbr>Methods</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}Specifies which methods are allowed. Can be `GET`, `PUT`, `POST`, `DELETE` or `HEAD`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>allowed<wbr>Origins</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}Specifies which origins are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>expose<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}Specifies expose header in the response.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>max<wbr>Age<wbr>Seconds</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies time in seconds that browser can cache the response for a preflight request.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allowed<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Specifies which headers are allowed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>allowed<wbr>Methods</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Specifies which methods are allowed. Can be `GET`, `PUT`, `POST`, `DELETE` or `HEAD`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>allowed<wbr>Origins</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Specifies which origins are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>expose<wbr>Headers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}Specifies expose header in the response.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>max<wbr>Age<wbr>Seconds</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies time in seconds that browser can cache the response for a preflight request.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Grant</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketGrant">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketGrant">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketGrantArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketGrantOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Canonical user id to grant for. Used only when `type` is `CanonicalUser`.  
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Permissions</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}List of permissions to apply for grantee. Valid values are `READ`, `WRITE`, `READ_ACP`, `WRITE_ACP`, `FULL_ACCESS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}- Type of grantee to apply for. Valid values are `CanonicalUser` and `Group`. `AmazonCustomerByEmail` is not supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Uri address to grant for. Used only when `type` is `Group`.
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
    <dd>{{% md %}}Canonical user id to grant for. Used only when `type` is `CanonicalUser`.  
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Permissions</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of permissions to apply for grantee. Valid values are `READ`, `WRITE`, `READ_ACP`, `WRITE_ACP`, `FULL_ACCESS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}- Type of grantee to apply for. Valid values are `CanonicalUser` and `Group`. `AmazonCustomerByEmail` is not supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Uri address to grant for. Used only when `type` is `Group`.
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
    <dd>{{% md %}}Canonical user id to grant for. Used only when `type` is `CanonicalUser`.  
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>permissions</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}List of permissions to apply for grantee. Valid values are `READ`, `WRITE`, `READ_ACP`, `WRITE_ACP`, `FULL_ACCESS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}- Type of grantee to apply for. Valid values are `CanonicalUser` and `Group`. `AmazonCustomerByEmail` is not supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Uri address to grant for. Used only when `type` is `Group`.
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
    <dd>{{% md %}}Canonical user id to grant for. Used only when `type` is `CanonicalUser`.  
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>permissions</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of permissions to apply for grantee. Valid values are `READ`, `WRITE`, `READ_ACP`, `WRITE_ACP`, `FULL_ACCESS`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}- Type of grantee to apply for. Valid values are `CanonicalUser` and `Group`. `AmazonCustomerByEmail` is not supported.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Uri address to grant for. Used only when `type` is `Group`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Lifecycle<wbr>Rule</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketLifecycleRule">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketLifecycleRule">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLifecycleRuleArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLifecycleRuleOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Abort<wbr>Incomplete<wbr>Multipart<wbr>Upload<wbr>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after initiating a multipart upload when the multipart upload must be completed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Specifies lifecycle rule status.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecycleruleexpiration">Bucket<wbr>Lifecycle<wbr>Rule<wbr>Expiration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Specifies a period in the object's expire (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Unique identifier for the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Noncurrent<wbr>Version<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerulenoncurrentversionexpiration">Bucket<wbr>Lifecycle<wbr>Rule<wbr>Noncurrent<wbr>Version<wbr>Expiration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Specifies when noncurrent object versions expire (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Noncurrent<wbr>Version<wbr>Transitions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerulenoncurrentversiontransition">List&lt;Bucket<wbr>Lifecycle<wbr>Rule<wbr>Noncurrent<wbr>Version<wbr>Transition<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Specifies when noncurrent object versions transitions (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Object key prefix identifying one or more objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}Specifies object tags key and value.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Transitions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecycleruletransition">List&lt;Bucket<wbr>Lifecycle<wbr>Rule<wbr>Transition<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Specifies a period in the object's transitions (documented below).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Abort<wbr>Incomplete<wbr>Multipart<wbr>Upload<wbr>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after initiating a multipart upload when the multipart upload must be completed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Specifies lifecycle rule status.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecycleruleexpiration">*Bucket<wbr>Lifecycle<wbr>Rule<wbr>Expiration</a></span>
    </dt>
    <dd>{{% md %}}Specifies a period in the object's expire (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Unique identifier for the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Noncurrent<wbr>Version<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerulenoncurrentversionexpiration">*Bucket<wbr>Lifecycle<wbr>Rule<wbr>Noncurrent<wbr>Version<wbr>Expiration</a></span>
    </dt>
    <dd>{{% md %}}Specifies when noncurrent object versions expire (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Noncurrent<wbr>Version<wbr>Transitions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerulenoncurrentversiontransition">[]Bucket<wbr>Lifecycle<wbr>Rule<wbr>Noncurrent<wbr>Version<wbr>Transition</a></span>
    </dt>
    <dd>{{% md %}}Specifies when noncurrent object versions transitions (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Object key prefix identifying one or more objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Specifies object tags key and value.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Transitions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecycleruletransition">[]Bucket<wbr>Lifecycle<wbr>Rule<wbr>Transition</a></span>
    </dt>
    <dd>{{% md %}}Specifies a period in the object's transitions (documented below).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>abort<wbr>Incomplete<wbr>Multipart<wbr>Upload<wbr>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after initiating a multipart upload when the multipart upload must be completed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}Specifies lifecycle rule status.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecycleruleexpiration">Bucket<wbr>Lifecycle<wbr>Rule<wbr>Expiration?</a></span>
    </dt>
    <dd>{{% md %}}Specifies a period in the object's expire (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Unique identifier for the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>noncurrent<wbr>Version<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerulenoncurrentversionexpiration">Bucket<wbr>Lifecycle<wbr>Rule<wbr>Noncurrent<wbr>Version<wbr>Expiration?</a></span>
    </dt>
    <dd>{{% md %}}Specifies when noncurrent object versions expire (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>noncurrent<wbr>Version<wbr>Transitions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerulenoncurrentversiontransition">Bucket<wbr>Lifecycle<wbr>Rule<wbr>Noncurrent<wbr>Version<wbr>Transition[]?</a></span>
    </dt>
    <dd>{{% md %}}Specifies when noncurrent object versions transitions (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Object key prefix identifying one or more objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}Specifies object tags key and value.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>transitions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecycleruletransition">Bucket<wbr>Lifecycle<wbr>Rule<wbr>Transition[]?</a></span>
    </dt>
    <dd>{{% md %}}Specifies a period in the object's transitions (documented below).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>abort<wbr>Incomplete<wbr>Multipart<wbr>Upload<wbr>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after initiating a multipart upload when the multipart upload must be completed.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Specifies lifecycle rule status.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecycleruleexpiration">Dict[Bucket<wbr>Lifecycle<wbr>Rule<wbr>Expiration]</a></span>
    </dt>
    <dd>{{% md %}}Specifies a period in the object's expire (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Unique identifier for the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>noncurrent<wbr>Version<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerulenoncurrentversionexpiration">Dict[Bucket<wbr>Lifecycle<wbr>Rule<wbr>Noncurrent<wbr>Version<wbr>Expiration]</a></span>
    </dt>
    <dd>{{% md %}}Specifies when noncurrent object versions expire (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>noncurrent<wbr>Version<wbr>Transitions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecyclerulenoncurrentversiontransition">List[Bucket<wbr>Lifecycle<wbr>Rule<wbr>Noncurrent<wbr>Version<wbr>Transition]</a></span>
    </dt>
    <dd>{{% md %}}Specifies when noncurrent object versions transitions (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Object key prefix identifying one or more objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Specifies object tags key and value.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>transitions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketlifecycleruletransition">List[Bucket<wbr>Lifecycle<wbr>Rule<wbr>Transition]</a></span>
    </dt>
    <dd>{{% md %}}Specifies a period in the object's transitions (documented below).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Lifecycle<wbr>Rule<wbr>Expiration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketLifecycleRuleExpiration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketLifecycleRuleExpiration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLifecycleRuleExpirationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLifecycleRuleExpirationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the date after which you want the corresponding action to take effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after object creation when the specific rule action takes effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Expired<wbr>Object<wbr>Delete<wbr>Marker</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}On a versioned bucket (versioning-enabled or versioning-suspended bucket), you can add this element in the lifecycle configuration to direct Amazon S3 to delete expired object delete markers.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the date after which you want the corresponding action to take effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after object creation when the specific rule action takes effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Expired<wbr>Object<wbr>Delete<wbr>Marker</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}On a versioned bucket (versioning-enabled or versioning-suspended bucket), you can add this element in the lifecycle configuration to direct Amazon S3 to delete expired object delete markers.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>date</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the date after which you want the corresponding action to take effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>days</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after object creation when the specific rule action takes effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>expired<wbr>Object<wbr>Delete<wbr>Marker</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}On a versioned bucket (versioning-enabled or versioning-suspended bucket), you can add this element in the lifecycle configuration to direct Amazon S3 to delete expired object delete markers.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>date</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the date after which you want the corresponding action to take effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>days</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after object creation when the specific rule action takes effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>expired<wbr>Object<wbr>Delete<wbr>Marker</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}On a versioned bucket (versioning-enabled or versioning-suspended bucket), you can add this element in the lifecycle configuration to direct Amazon S3 to delete expired object delete markers.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Lifecycle<wbr>Rule<wbr>Noncurrent<wbr>Version<wbr>Expiration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketLifecycleRuleNoncurrentVersionExpiration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketLifecycleRuleNoncurrentVersionExpiration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLifecycleRuleNoncurrentVersionExpirationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLifecycleRuleNoncurrentVersionExpirationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days an object is noncurrent object versions expire.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days an object is noncurrent object versions expire.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>days</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days an object is noncurrent object versions expire.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>days</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days an object is noncurrent object versions expire.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Lifecycle<wbr>Rule<wbr>Noncurrent<wbr>Version<wbr>Transition</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketLifecycleRuleNoncurrentVersionTransition">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketLifecycleRuleNoncurrentVersionTransition">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLifecycleRuleNoncurrentVersionTransitionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLifecycleRuleNoncurrentVersionTransitionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days an object is noncurrent object versions expire.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Storage<wbr>Class</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Amazon S3 storage class to which you want the noncurrent versions object to transition. Can be `ONEZONE_IA`, `STANDARD_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days an object is noncurrent object versions expire.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Storage<wbr>Class</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Amazon S3 storage class to which you want the noncurrent versions object to transition. Can be `ONEZONE_IA`, `STANDARD_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>days</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days an object is noncurrent object versions expire.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>storage<wbr>Class</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Amazon S3 storage class to which you want the noncurrent versions object to transition. Can be `ONEZONE_IA`, `STANDARD_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>days</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days an object is noncurrent object versions expire.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>storage_<wbr>class</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Amazon S3 storage class to which you want the noncurrent versions object to transition. Can be `ONEZONE_IA`, `STANDARD_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Lifecycle<wbr>Rule<wbr>Transition</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketLifecycleRuleTransition">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketLifecycleRuleTransition">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLifecycleRuleTransitionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLifecycleRuleTransitionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the date after which you want the corresponding action to take effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after object creation when the specific rule action takes effect.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Storage<wbr>Class</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Amazon S3 storage class to which you want the object to transition. Can be `ONEZONE_IA`, `STANDARD_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Date</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the date after which you want the corresponding action to take effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after object creation when the specific rule action takes effect.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Storage<wbr>Class</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Amazon S3 storage class to which you want the object to transition. Can be `ONEZONE_IA`, `STANDARD_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>date</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the date after which you want the corresponding action to take effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>days</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after object creation when the specific rule action takes effect.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>storage<wbr>Class</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Specifies the Amazon S3 storage class to which you want the object to transition. Can be `ONEZONE_IA`, `STANDARD_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>date</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the date after which you want the corresponding action to take effect.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>days</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Specifies the number of days after object creation when the specific rule action takes effect.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>storage_<wbr>class</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the Amazon S3 storage class to which you want the object to transition. Can be `ONEZONE_IA`, `STANDARD_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Logging</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketLogging">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketLogging">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLoggingArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketLoggingOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Target<wbr>Bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the bucket that will receive the log objects.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}To specify a key prefix for log objects.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Target<wbr>Bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the bucket that will receive the log objects.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}To specify a key prefix for log objects.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>target<wbr>Bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the bucket that will receive the log objects.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}To specify a key prefix for log objects.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>target<wbr>Bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the bucket that will receive the log objects.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}To specify a key prefix for log objects.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Object<wbr>Lock<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketObjectLockConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketObjectLockConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketObjectLockConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketObjectLockConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Object<wbr>Lock<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Indicates whether this bucket has an Object Lock configuration enabled. Valid value is `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfigurationrule">Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Rule<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The Object Lock rule in place for this bucket.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Object<wbr>Lock<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Indicates whether this bucket has an Object Lock configuration enabled. Valid value is `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfigurationrule">*Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}The Object Lock rule in place for this bucket.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>object<wbr>Lock<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Indicates whether this bucket has an Object Lock configuration enabled. Valid value is `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfigurationrule">Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Rule?</a></span>
    </dt>
    <dd>{{% md %}}The Object Lock rule in place for this bucket.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>object<wbr>Lock<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates whether this bucket has an Object Lock configuration enabled. Valid value is `Enabled`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfigurationrule">Dict[Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}The Object Lock rule in place for this bucket.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Rule</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketObjectLockConfigurationRule">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketObjectLockConfigurationRule">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketObjectLockConfigurationRuleArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketObjectLockConfigurationRuleOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Default<wbr>Retention</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfigurationruledefaultretention">Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Rule<wbr>Default<wbr>Retention<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}The default retention period that you want to apply to new objects placed in this bucket.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Default<wbr>Retention</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfigurationruledefaultretention">Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Rule<wbr>Default<wbr>Retention</a></span>
    </dt>
    <dd>{{% md %}}The default retention period that you want to apply to new objects placed in this bucket.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>default<wbr>Retention</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfigurationruledefaultretention">Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Rule<wbr>Default<wbr>Retention</a></span>
    </dt>
    <dd>{{% md %}}The default retention period that you want to apply to new objects placed in this bucket.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>default<wbr>Retention</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketobjectlockconfigurationruledefaultretention">Dict[Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Rule<wbr>Default<wbr>Retention]</a></span>
    </dt>
    <dd>{{% md %}}The default retention period that you want to apply to new objects placed in this bucket.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Object<wbr>Lock<wbr>Configuration<wbr>Rule<wbr>Default<wbr>Retention</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketObjectLockConfigurationRuleDefaultRetention">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketObjectLockConfigurationRuleDefaultRetention">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketObjectLockConfigurationRuleDefaultRetentionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketObjectLockConfigurationRuleDefaultRetentionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The number of days that you want to specify for the default retention period.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The default Object Lock retention mode you want to apply to new objects placed in this bucket. Valid values are `GOVERNANCE` and `COMPLIANCE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Years</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The number of years that you want to specify for the default retention period.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Days</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The number of days that you want to specify for the default retention period.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The default Object Lock retention mode you want to apply to new objects placed in this bucket. Valid values are `GOVERNANCE` and `COMPLIANCE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Years</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The number of years that you want to specify for the default retention period.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>days</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The number of days that you want to specify for the default retention period.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The default Object Lock retention mode you want to apply to new objects placed in this bucket. Valid values are `GOVERNANCE` and `COMPLIANCE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>years</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The number of years that you want to specify for the default retention period.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>days</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of days that you want to specify for the default retention period.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>mode</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The default Object Lock retention mode you want to apply to new objects placed in this bucket. Valid values are `GOVERNANCE` and `COMPLIANCE`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>years</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of years that you want to specify for the default retention period.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Replication<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketReplicationConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketReplicationConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the IAM role for Amazon S3 to assume when replicating the objects.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrule">List&lt;Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}Specifies the rules managing the replication (documented below).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the IAM role for Amazon S3 to assume when replicating the objects.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrule">[]Bucket<wbr>Replication<wbr>Configuration<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}Specifies the rules managing the replication (documented below).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the IAM role for Amazon S3 to assume when replicating the objects.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrule">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule[]</a></span>
    </dt>
    <dd>{{% md %}}Specifies the rules managing the replication (documented below).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the IAM role for Amazon S3 to assume when replicating the objects.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrule">List[Bucket<wbr>Replication<wbr>Configuration<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}Specifies the rules managing the replication (documented below).
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Replication<wbr>Configuration<wbr>Rule</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketReplicationConfigurationRule">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketReplicationConfigurationRule">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationruledestination">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Destination<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Specifies the destination for the rule (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filter</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulefilter">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Filter<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Filter that identifies subset of objects to which the replication rule applies (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Unique identifier for the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Object keyname prefix identifying one or more objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The priority associated with the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Selection<wbr>Criteria</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulesourceselectioncriteria">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Source<wbr>Selection<wbr>Criteria<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Specifies special object selection criteria (documented below).
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The status of the rule. Either `Enabled` or `Disabled`. The rule is ignored if status is not Enabled.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationruledestination">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Destination</a></span>
    </dt>
    <dd>{{% md %}}Specifies the destination for the rule (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filter</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulefilter">*Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Filter</a></span>
    </dt>
    <dd>{{% md %}}Filter that identifies subset of objects to which the replication rule applies (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Unique identifier for the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Object keyname prefix identifying one or more objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The priority associated with the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Selection<wbr>Criteria</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulesourceselectioncriteria">*Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Source<wbr>Selection<wbr>Criteria</a></span>
    </dt>
    <dd>{{% md %}}Specifies special object selection criteria (documented below).
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The status of the rule. Either `Enabled` or `Disabled`. The rule is ignored if status is not Enabled.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>destination</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationruledestination">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Destination</a></span>
    </dt>
    <dd>{{% md %}}Specifies the destination for the rule (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filter</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulefilter">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Filter?</a></span>
    </dt>
    <dd>{{% md %}}Filter that identifies subset of objects to which the replication rule applies (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Unique identifier for the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Object keyname prefix identifying one or more objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The priority associated with the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source<wbr>Selection<wbr>Criteria</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulesourceselectioncriteria">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Source<wbr>Selection<wbr>Criteria?</a></span>
    </dt>
    <dd>{{% md %}}Specifies special object selection criteria (documented below).
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The status of the rule. Either `Enabled` or `Disabled`. The rule is ignored if status is not Enabled.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>destination</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationruledestination">Dict[Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Destination]</a></span>
    </dt>
    <dd>{{% md %}}Specifies the destination for the rule (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filter</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulefilter">Dict[Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Filter]</a></span>
    </dt>
    <dd>{{% md %}}Filter that identifies subset of objects to which the replication rule applies (documented below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Unique identifier for the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Object keyname prefix identifying one or more objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>priority</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The priority associated with the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source<wbr>Selection<wbr>Criteria</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulesourceselectioncriteria">Dict[Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Source<wbr>Selection<wbr>Criteria]</a></span>
    </dt>
    <dd>{{% md %}}Specifies special object selection criteria (documented below).
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>status</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The status of the rule. Either `Enabled` or `Disabled`. The rule is ignored if status is not Enabled.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Destination</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketReplicationConfigurationRuleDestination">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketReplicationConfigurationRuleDestination">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleDestinationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleDestinationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Access<wbr>Control<wbr>Translation</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationruledestinationaccesscontroltranslation">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Destination<wbr>Access<wbr>Control<wbr>Translation<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Specifies the overrides to use for object owners on replication. Must be used in conjunction with `account_id` owner override configuration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Account<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Account ID to use for overriding the object owner on replication. Must be used in conjunction with `access_control_translation` override configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket where you want Amazon S3 to store replicas of the object identified by the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Replica<wbr>Kms<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Destination KMS encryption key ARN for SSE-KMS replication. Must be used in conjunction with
`sse_kms_encrypted_objects` source selection criteria.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Class</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The class of storage used to store the object. Can be `STANDARD`, `REDUCED_REDUNDANCY`, `STANDARD_IA`, `ONEZONE_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Access<wbr>Control<wbr>Translation</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationruledestinationaccesscontroltranslation">*Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Destination<wbr>Access<wbr>Control<wbr>Translation</a></span>
    </dt>
    <dd>{{% md %}}Specifies the overrides to use for object owners on replication. Must be used in conjunction with `account_id` owner override configuration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Account<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Account ID to use for overriding the object owner on replication. Must be used in conjunction with `access_control_translation` override configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket where you want Amazon S3 to store replicas of the object identified by the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Replica<wbr>Kms<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Destination KMS encryption key ARN for SSE-KMS replication. Must be used in conjunction with
`sse_kms_encrypted_objects` source selection criteria.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Storage<wbr>Class</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The class of storage used to store the object. Can be `STANDARD`, `REDUCED_REDUNDANCY`, `STANDARD_IA`, `ONEZONE_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>access<wbr>Control<wbr>Translation</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationruledestinationaccesscontroltranslation">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Destination<wbr>Access<wbr>Control<wbr>Translation?</a></span>
    </dt>
    <dd>{{% md %}}Specifies the overrides to use for object owners on replication. Must be used in conjunction with `account_id` owner override configuration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>account<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Account ID to use for overriding the object owner on replication. Must be used in conjunction with `access_control_translation` override configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket where you want Amazon S3 to store replicas of the object identified by the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>replica<wbr>Kms<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Destination KMS encryption key ARN for SSE-KMS replication. Must be used in conjunction with
`sse_kms_encrypted_objects` source selection criteria.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage<wbr>Class</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The class of storage used to store the object. Can be `STANDARD`, `REDUCED_REDUNDANCY`, `STANDARD_IA`, `ONEZONE_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>access<wbr>Control<wbr>Translation</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationruledestinationaccesscontroltranslation">Dict[Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Destination<wbr>Access<wbr>Control<wbr>Translation]</a></span>
    </dt>
    <dd>{{% md %}}Specifies the overrides to use for object owners on replication. Must be used in conjunction with `account_id` owner override configuration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>account_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Account ID to use for overriding the object owner on replication. Must be used in conjunction with `access_control_translation` override configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>bucket</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the S3 bucket where you want Amazon S3 to store replicas of the object identified by the rule.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>replica<wbr>Kms<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Destination KMS encryption key ARN for SSE-KMS replication. Must be used in conjunction with
`sse_kms_encrypted_objects` source selection criteria.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>storage_<wbr>class</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The class of storage used to store the object. Can be `STANDARD`, `REDUCED_REDUNDANCY`, `STANDARD_IA`, `ONEZONE_IA`, `INTELLIGENT_TIERING`, `GLACIER`, or `DEEP_ARCHIVE`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Destination<wbr>Access<wbr>Control<wbr>Translation</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketReplicationConfigurationRuleDestinationAccessControlTranslation">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketReplicationConfigurationRuleDestinationAccessControlTranslation">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleDestinationAccessControlTranslationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleDestinationAccessControlTranslationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Owner</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The override value for the owner on replicated objects. Currently only `Destination` is supported.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Owner</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The override value for the owner on replicated objects. Currently only `Destination` is supported.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>owner</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The override value for the owner on replicated objects. Currently only `Destination` is supported.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>owner</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The override value for the owner on replicated objects. Currently only `Destination` is supported.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Filter</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketReplicationConfigurationRuleFilter">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketReplicationConfigurationRuleFilter">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleFilterArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleFilterOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Object keyname prefix that identifies subset of objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, object>?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags that identifies subset of objects to which the rule applies.
The rule applies only to objects having all the tags in its tagset.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Object keyname prefix that identifies subset of objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}A mapping of tags that identifies subset of objects to which the rule applies.
The rule applies only to objects having all the tags in its tagset.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Object keyname prefix that identifies subset of objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}?</span>
    </dt>
    <dd>{{% md %}}A mapping of tags that identifies subset of objects to which the rule applies.
The rule applies only to objects having all the tags in its tagset.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Object keyname prefix that identifies subset of objects to which the rule applies.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A mapping of tags that identifies subset of objects to which the rule applies.
The rule applies only to objects having all the tags in its tagset.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Source<wbr>Selection<wbr>Criteria</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketReplicationConfigurationRuleSourceSelectionCriteria">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketReplicationConfigurationRuleSourceSelectionCriteria">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleSourceSelectionCriteriaArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleSourceSelectionCriteriaOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Sse<wbr>Kms<wbr>Encrypted<wbr>Objects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulesourceselectioncriteriassekmsencryptedobjects">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Source<wbr>Selection<wbr>Criteria<wbr>Sse<wbr>Kms<wbr>Encrypted<wbr>Objects<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Match SSE-KMS encrypted objects (documented below). If specified, `replica_kms_key_id`
in `destination` must be specified as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Sse<wbr>Kms<wbr>Encrypted<wbr>Objects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulesourceselectioncriteriassekmsencryptedobjects">*Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Source<wbr>Selection<wbr>Criteria<wbr>Sse<wbr>Kms<wbr>Encrypted<wbr>Objects</a></span>
    </dt>
    <dd>{{% md %}}Match SSE-KMS encrypted objects (documented below). If specified, `replica_kms_key_id`
in `destination` must be specified as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>sse<wbr>Kms<wbr>Encrypted<wbr>Objects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulesourceselectioncriteriassekmsencryptedobjects">Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Source<wbr>Selection<wbr>Criteria<wbr>Sse<wbr>Kms<wbr>Encrypted<wbr>Objects?</a></span>
    </dt>
    <dd>{{% md %}}Match SSE-KMS encrypted objects (documented below). If specified, `replica_kms_key_id`
in `destination` must be specified as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>sse<wbr>Kms<wbr>Encrypted<wbr>Objects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketreplicationconfigurationrulesourceselectioncriteriassekmsencryptedobjects">Dict[Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Source<wbr>Selection<wbr>Criteria<wbr>Sse<wbr>Kms<wbr>Encrypted<wbr>Objects]</a></span>
    </dt>
    <dd>{{% md %}}Match SSE-KMS encrypted objects (documented below). If specified, `replica_kms_key_id`
in `destination` must be specified as well.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Replication<wbr>Configuration<wbr>Rule<wbr>Source<wbr>Selection<wbr>Criteria<wbr>Sse<wbr>Kms<wbr>Encrypted<wbr>Objects</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketReplicationConfigurationRuleSourceSelectionCriteriaSseKmsEncryptedObjects">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketReplicationConfigurationRuleSourceSelectionCriteriaSseKmsEncryptedObjects">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleSourceSelectionCriteriaSseKmsEncryptedObjectsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketReplicationConfigurationRuleSourceSelectionCriteriaSseKmsEncryptedObjectsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean which indicates if this criteria is enabled.
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
    <dd>{{% md %}}Boolean which indicates if this criteria is enabled.
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
    <dd>{{% md %}}Boolean which indicates if this criteria is enabled.
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
    <dd>{{% md %}}Boolean which indicates if this criteria is enabled.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketServerSideEncryptionConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketServerSideEncryptionConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketServerSideEncryptionConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketServerSideEncryptionConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfigurationrule">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Rule<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}A single object for server-side encryption by default configuration. (documented below)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfigurationrule">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}A single object for server-side encryption by default configuration. (documented below)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfigurationrule">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}A single object for server-side encryption by default configuration. (documented below)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfigurationrule">Dict[Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}A single object for server-side encryption by default configuration. (documented below)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Rule</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketServerSideEncryptionConfigurationRule">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketServerSideEncryptionConfigurationRule">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketServerSideEncryptionConfigurationRuleArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketServerSideEncryptionConfigurationRuleOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Apply<wbr>Server<wbr>Side<wbr>Encryption<wbr>By<wbr>Default</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfigurationruleapplyserversideencryptionbydefault">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Rule<wbr>Apply<wbr>Server<wbr>Side<wbr>Encryption<wbr>By<wbr>Default<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}A single object for setting server-side encryption by default. (documented below)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Apply<wbr>Server<wbr>Side<wbr>Encryption<wbr>By<wbr>Default</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfigurationruleapplyserversideencryptionbydefault">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Rule<wbr>Apply<wbr>Server<wbr>Side<wbr>Encryption<wbr>By<wbr>Default</a></span>
    </dt>
    <dd>{{% md %}}A single object for setting server-side encryption by default. (documented below)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>apply<wbr>Server<wbr>Side<wbr>Encryption<wbr>By<wbr>Default</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfigurationruleapplyserversideencryptionbydefault">Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Rule<wbr>Apply<wbr>Server<wbr>Side<wbr>Encryption<wbr>By<wbr>Default</a></span>
    </dt>
    <dd>{{% md %}}A single object for setting server-side encryption by default. (documented below)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>apply<wbr>Server<wbr>Side<wbr>Encryption<wbr>By<wbr>Default</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#bucketserversideencryptionconfigurationruleapplyserversideencryptionbydefault">Dict[Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Rule<wbr>Apply<wbr>Server<wbr>Side<wbr>Encryption<wbr>By<wbr>Default]</a></span>
    </dt>
    <dd>{{% md %}}A single object for setting server-side encryption by default. (documented below)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Server<wbr>Side<wbr>Encryption<wbr>Configuration<wbr>Rule<wbr>Apply<wbr>Server<wbr>Side<wbr>Encryption<wbr>By<wbr>Default</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketServerSideEncryptionConfigurationRuleApplyServerSideEncryptionByDefault">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketServerSideEncryptionConfigurationRuleApplyServerSideEncryptionByDefault">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketServerSideEncryptionConfigurationRuleApplyServerSideEncryptionByDefaultArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketServerSideEncryptionConfigurationRuleApplyServerSideEncryptionByDefaultOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Master<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The AWS KMS master key ID used for the SSE-KMS encryption. This can only be used when you set the value of `sse_algorithm` as `aws:kms`. The default `aws/s3` AWS KMS master key is used if this element is absent while the `sse_algorithm` is `aws:kms`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Sse<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The server-side encryption algorithm to use. Valid values are `AES256` and `aws:kms`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Master<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The AWS KMS master key ID used for the SSE-KMS encryption. This can only be used when you set the value of `sse_algorithm` as `aws:kms`. The default `aws/s3` AWS KMS master key is used if this element is absent while the `sse_algorithm` is `aws:kms`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Sse<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The server-side encryption algorithm to use. Valid values are `AES256` and `aws:kms`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Master<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The AWS KMS master key ID used for the SSE-KMS encryption. This can only be used when you set the value of `sse_algorithm` as `aws:kms`. The default `aws/s3` AWS KMS master key is used if this element is absent while the `sse_algorithm` is `aws:kms`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>sse<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The server-side encryption algorithm to use. Valid values are `AES256` and `aws:kms`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>master_<wbr>key_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The AWS KMS master key ID used for the SSE-KMS encryption. This can only be used when you set the value of `sse_algorithm` as `aws:kms`. The default `aws/s3` AWS KMS master key is used if this element is absent while the `sse_algorithm` is `aws:kms`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>sse<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The server-side encryption algorithm to use. Valid values are `AES256` and `aws:kms`
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Versioning</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketVersioning">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketVersioning">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketVersioningArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketVersioningOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enable versioning. Once you version-enable a bucket, it can never return to an unversioned state. You can, however, suspend versioning on that bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Mfa<wbr>Delete</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Enable MFA delete for either `Change the versioning state of your bucket` or `Permanently delete an object version`. Default is `false`.
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
    <dd>{{% md %}}Enable versioning. Once you version-enable a bucket, it can never return to an unversioned state. You can, however, suspend versioning on that bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Mfa<wbr>Delete</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Enable MFA delete for either `Change the versioning state of your bucket` or `Permanently delete an object version`. Default is `false`.
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
    <dd>{{% md %}}Enable versioning. Once you version-enable a bucket, it can never return to an unversioned state. You can, however, suspend versioning on that bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>mfa<wbr>Delete</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Enable MFA delete for either `Change the versioning state of your bucket` or `Permanently delete an object version`. Default is `false`.
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
    <dd>{{% md %}}Enable versioning. Once you version-enable a bucket, it can never return to an unversioned state. You can, however, suspend versioning on that bucket.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>mfa<wbr>Delete</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Enable MFA delete for either `Change the versioning state of your bucket` or `Permanently delete an object version`. Default is `false`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Bucket<wbr>Website</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#BucketWebsite">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#BucketWebsite">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketWebsiteArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/s3?tab=doc#BucketWebsiteOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Error<wbr>Document</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An absolute path to the document to return in case of a 4XX error.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Index<wbr>Document</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Amazon S3 returns this index document when requests are made to the root domain or any of the subfolders.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Redirect<wbr>All<wbr>Requests<wbr>To</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A hostname to redirect all website requests for this bucket to. Hostname can optionally be prefixed with a protocol (`http://` or `https://`) to use when redirecting requests. The default is the protocol that is used in the original request.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Routing<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type">Union<string, ImmutableArray<string>>?</span>
    </dt>
    <dd>{{% md %}}A json array containing [routing rules](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-websiteconfiguration-routingrules.html)
describing redirect behavior and when redirects are applied.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Error<wbr>Document</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}An absolute path to the document to return in case of a 4XX error.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Index<wbr>Document</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Amazon S3 returns this index document when requests are made to the root domain or any of the subfolders.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Redirect<wbr>All<wbr>Requests<wbr>To</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}A hostname to redirect all website requests for this bucket to. Hostname can optionally be prefixed with a protocol (`http://` or `https://`) to use when redirecting requests. The default is the protocol that is used in the original request.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Routing<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type">interface{}</span>
    </dt>
    <dd>{{% md %}}A json array containing [routing rules](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-websiteconfiguration-routingrules.html)
describing redirect behavior and when redirects are applied.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>error<wbr>Document</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}An absolute path to the document to return in case of a 4XX error.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>index<wbr>Document</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Amazon S3 returns this index document when requests are made to the root domain or any of the subfolders.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>redirect<wbr>All<wbr>Requests<wbr>To</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}A hostname to redirect all website requests for this bucket to. Hostname can optionally be prefixed with a protocol (`http://` or `https://`) to use when redirecting requests. The default is the protocol that is used in the original request.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>routing<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type">string | RoutingRule[]</span>
    </dt>
    <dd>{{% md %}}A json array containing [routing rules](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-websiteconfiguration-routingrules.html)
describing redirect behavior and when redirects are applied.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>error<wbr>Document</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}An absolute path to the document to return in case of a 4XX error.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>index<wbr>Document</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Amazon S3 returns this index document when requests are made to the root domain or any of the subfolders.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>redirect<wbr>All<wbr>Requests<wbr>To</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}A hostname to redirect all website requests for this bucket to. Hostname can optionally be prefixed with a protocol (`http://` or `https://`) to use when redirecting requests. The default is the protocol that is used in the original request.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>routing<wbr>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}A json array containing [routing rules](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-websiteconfiguration-routingrules.html)
describing redirect behavior and when redirects are applied.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







