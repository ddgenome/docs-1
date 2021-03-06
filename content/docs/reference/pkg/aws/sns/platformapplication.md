
---
title: "PlatformApplication"
block_external_search_index: true
---

Provides an SNS platform application resource

## Example Usage

### Apple Push Notification Service (APNS)

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const apnsApplication = new aws.sns.PlatformApplication("apns_application", {
    platform: "APNS",
    platformCredential: "<APNS PRIVATE KEY>",
    platformPrincipal: "<APNS CERTIFICATE>",
});
```

### Google Cloud Messaging (GCM)

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const gcmApplication = new aws.sns.PlatformApplication("gcm_application", {
    platform: "GCM",
    platformCredential: "<GCM API KEY>",
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/sns_platform_application.html.markdown.



## Create a PlatformApplication Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/sns/#PlatformApplication">PlatformApplication</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/sns/#PlatformApplicationArgs">PlatformApplicationArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">PlatformApplication</span><span class="p">(resource_name, opts=None, </span>event_delivery_failure_topic_arn=None<span class="p">, </span>event_endpoint_created_topic_arn=None<span class="p">, </span>event_endpoint_deleted_topic_arn=None<span class="p">, </span>event_endpoint_updated_topic_arn=None<span class="p">, </span>failure_feedback_role_arn=None<span class="p">, </span>name=None<span class="p">, </span>platform=None<span class="p">, </span>platform_credential=None<span class="p">, </span>platform_principal=None<span class="p">, </span>success_feedback_role_arn=None<span class="p">, </span>success_feedback_sample_rate=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewPlatformApplication<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/sns?tab=doc#PlatformApplicationArgs">PlatformApplicationArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/sns?tab=doc#PlatformApplication">PlatformApplication</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Sns.PlatformApplication.html">PlatformApplication</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Sns.Inputs.PlatformApplicationArgs.html">PlatformApplicationArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Event<wbr>Delivery<wbr>Failure<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Created<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Deleted<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Updated<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Failure<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Platform<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Platform<wbr>Principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Success<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Success<wbr>Feedback<wbr>Sample<wbr>Rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Delivery<wbr>Failure<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Created<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Deleted<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Updated<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Failure<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Platform<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Platform<wbr>Principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Success<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Success<wbr>Feedback<wbr>Sample<wbr>Rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>event<wbr>Delivery<wbr>Failure<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event<wbr>Endpoint<wbr>Created<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event<wbr>Endpoint<wbr>Deleted<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event<wbr>Endpoint<wbr>Updated<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>failure<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>platform<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>platform<wbr>Principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>success<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>success<wbr>Feedback<wbr>Sample<wbr>Rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>event_<wbr>delivery_<wbr>failure_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event_<wbr>endpoint_<wbr>created_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event_<wbr>endpoint_<wbr>deleted_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event_<wbr>endpoint_<wbr>updated_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>failure_<wbr>feedback_<wbr>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>platform_<wbr>credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>platform_<wbr>principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>success_<wbr>feedback_<wbr>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>success_<wbr>feedback_<wbr>sample_<wbr>rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## PlatformApplication Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS platform application
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Event<wbr>Delivery<wbr>Failure<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Event<wbr>Endpoint<wbr>Created<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Event<wbr>Endpoint<wbr>Deleted<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Event<wbr>Endpoint<wbr>Updated<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Failure<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Platform<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Platform<wbr>Principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Success<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Success<wbr>Feedback<wbr>Sample<wbr>Rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
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
    <dd>{{% md %}}The ARN of the SNS platform application
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Event<wbr>Delivery<wbr>Failure<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Event<wbr>Endpoint<wbr>Created<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Event<wbr>Endpoint<wbr>Deleted<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Event<wbr>Endpoint<wbr>Updated<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Failure<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Platform<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Platform<wbr>Principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Success<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Success<wbr>Feedback<wbr>Sample<wbr>Rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
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
    <dd>{{% md %}}The ARN of the SNS platform application
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>event<wbr>Delivery<wbr>Failure<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>event<wbr>Endpoint<wbr>Created<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>event<wbr>Endpoint<wbr>Deleted<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>event<wbr>Endpoint<wbr>Updated<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>failure<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>platform<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>platform<wbr>Principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>success<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>success<wbr>Feedback<wbr>Sample<wbr>Rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
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
    <dd>{{% md %}}The ARN of the SNS platform application
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>event_<wbr>delivery_<wbr>failure_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>event_<wbr>endpoint_<wbr>created_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>event_<wbr>endpoint_<wbr>deleted_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>event_<wbr>endpoint_<wbr>updated_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>failure_<wbr>feedback_<wbr>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>platform_<wbr>credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>platform_<wbr>principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>success_<wbr>feedback_<wbr>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>success_<wbr>feedback_<wbr>sample_<wbr>rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing PlatformApplication Resource

Get an existing PlatformApplication resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/sns/#PlatformApplicationState">PlatformApplicationState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/sns/#PlatformApplication">PlatformApplication</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>arn=None<span class="p">, </span>event_delivery_failure_topic_arn=None<span class="p">, </span>event_endpoint_created_topic_arn=None<span class="p">, </span>event_endpoint_deleted_topic_arn=None<span class="p">, </span>event_endpoint_updated_topic_arn=None<span class="p">, </span>failure_feedback_role_arn=None<span class="p">, </span>name=None<span class="p">, </span>platform=None<span class="p">, </span>platform_credential=None<span class="p">, </span>platform_principal=None<span class="p">, </span>success_feedback_role_arn=None<span class="p">, </span>success_feedback_sample_rate=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetPlatformApplication<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/sns?tab=doc#PlatformApplicationState">PlatformApplicationState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/sns?tab=doc#PlatformApplication">PlatformApplication</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Sns.PlatformApplication.html">PlatformApplication</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Sns.PlatformApplicationState.html">PlatformApplicationState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
    <dd>{{% md %}}The ARN of the SNS platform application
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Delivery<wbr>Failure<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Created<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Deleted<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Updated<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Failure<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Platform<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Platform<wbr>Principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Success<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Success<wbr>Feedback<wbr>Sample<wbr>Rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
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
    <dd>{{% md %}}The ARN of the SNS platform application
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Delivery<wbr>Failure<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Created<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Deleted<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Event<wbr>Endpoint<wbr>Updated<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Failure<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Platform<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Platform<wbr>Principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Success<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Success<wbr>Feedback<wbr>Sample<wbr>Rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
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
    <dd>{{% md %}}The ARN of the SNS platform application
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event<wbr>Delivery<wbr>Failure<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event<wbr>Endpoint<wbr>Created<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event<wbr>Endpoint<wbr>Deleted<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event<wbr>Endpoint<wbr>Updated<wbr>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>failure<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>platform<wbr>Credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>platform<wbr>Principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>success<wbr>Feedback<wbr>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>success<wbr>Feedback<wbr>Sample<wbr>Rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
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
    <dd>{{% md %}}The ARN of the SNS platform application
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event_<wbr>delivery_<wbr>failure_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a delivery to any of the platform endpoints associated with your platform application encounters a permanent failure.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event_<wbr>endpoint_<wbr>created_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when a new platform endpoint is added to your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event_<wbr>endpoint_<wbr>deleted_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is deleted from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>event_<wbr>endpoint_<wbr>updated_<wbr>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}SNS Topic triggered when an existing platform endpoint is changed from your platform application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>failure_<wbr>feedback_<wbr>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive failure feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The friendly name for the SNS platform application
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>platform</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The platform that the app is registered with. See [Platform][1] for supported platforms.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>platform_<wbr>credential</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Application Platform credential. See [Credential][1] for type of credential required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>platform_<wbr>principal</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Application Platform principal. See [Principal][2] for type of principal required for platform. The value of this attribute when stored into the state is only a hash of the real value, so therefore it is not practical to use this as an attribute for other resources.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>success_<wbr>feedback_<wbr>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The IAM role permitted to receive success feedback for this application.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>success_<wbr>feedback_<wbr>sample_<wbr>rate</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The percentage of success to sample (0-100)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}









