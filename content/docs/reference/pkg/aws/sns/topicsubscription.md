
---
title: "TopicSubscription"
block_external_search_index: true
---

  Provides a resource for subscribing to SNS topics. Requires that an SNS topic exist for the subscription to attach to.
This resource allows you to automatically place messages sent to SNS topics in SQS queues, send them as HTTP(S) POST requests
to a given endpoint, send SMS messages, or notify devices / applications. The most likely use case will
probably be SQS queues.

> **NOTE:** If the SNS topic and SQS queue are in different AWS regions, it is important for the "aws.sns.TopicSubscription" to use an AWS provider that is in the same region of the SNS topic. If the "aws.sns.TopicSubscription" is using a provider with a different region than the SNS topic, the subscription will fail to create.

> **NOTE:** Setup of cross-account subscriptions from SNS topics to SQS queues requires the provider to have access to BOTH accounts.

> **NOTE:** If SNS topic and SQS queue are in different AWS accounts but the same region it is important for the "aws.sns.TopicSubscription" to use the AWS provider of the account with the SQS queue. If "aws.sns.TopicSubscription" is using a Provider with a different account than the SQS queue, the provider creates the subscriptions but does not keep state and tries to re-create the subscription at every apply.

> **NOTE:** If SNS topic and SQS queue are in different AWS accounts and different AWS regions it is important to recognize that the subscription needs to be initiated from the account with the SQS queue but in the region of the SNS topic.

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/sns_topic_subscription.html.markdown.



## Create a TopicSubscription Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/sns/#TopicSubscription">TopicSubscription</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/sns/#TopicSubscriptionArgs">TopicSubscriptionArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">TopicSubscription</span><span class="p">(resource_name, opts=None, </span>confirmation_timeout_in_minutes=None<span class="p">, </span>delivery_policy=None<span class="p">, </span>endpoint=None<span class="p">, </span>endpoint_auto_confirms=None<span class="p">, </span>filter_policy=None<span class="p">, </span>protocol=None<span class="p">, </span>raw_message_delivery=None<span class="p">, </span>topic=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewTopicSubscription<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/sns?tab=doc#TopicSubscriptionArgs">TopicSubscriptionArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/sns?tab=doc#TopicSubscription">TopicSubscription</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Sns.TopicSubscription.html">TopicSubscription</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Sns.Inputs.TopicSubscriptionArgs.html">TopicSubscriptionArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Confirmation<wbr>Timeout<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delivery<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Auto<wbr>Confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filter<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Raw<wbr>Message<wbr>Delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Confirmation<wbr>Timeout<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delivery<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Auto<wbr>Confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filter<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Raw<wbr>Message<wbr>Delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">interface{}</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>confirmation<wbr>Timeout<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delivery<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint<wbr>Auto<wbr>Confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filter<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>raw<wbr>Message<wbr>Delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">string | Topic</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>confirmation_<wbr>timeout_<wbr>in_<wbr>minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delivery_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint_<wbr>auto_<wbr>confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filter_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>raw_<wbr>message_<wbr>delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## TopicSubscription Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the subscription stored as a more user-friendly property
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Confirmation<wbr>Timeout<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Delivery<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Endpoint<wbr>Auto<wbr>Confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Filter<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Raw<wbr>Message<wbr>Delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
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
    <dd>{{% md %}}The ARN of the subscription stored as a more user-friendly property
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Confirmation<wbr>Timeout<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Delivery<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Endpoint<wbr>Auto<wbr>Confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Filter<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Raw<wbr>Message<wbr>Delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
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
    <dd>{{% md %}}The ARN of the subscription stored as a more user-friendly property
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>confirmation<wbr>Timeout<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>delivery<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>endpoint<wbr>Auto<wbr>Confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>filter<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>raw<wbr>Message<wbr>Delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
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
    <dd>{{% md %}}The ARN of the subscription stored as a more user-friendly property
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>confirmation_<wbr>timeout_<wbr>in_<wbr>minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>delivery_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>endpoint_<wbr>auto_<wbr>confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>filter_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>raw_<wbr>message_<wbr>delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing TopicSubscription Resource

Get an existing TopicSubscription resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/sns/#TopicSubscriptionState">TopicSubscriptionState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/sns/#TopicSubscription">TopicSubscription</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>arn=None<span class="p">, </span>confirmation_timeout_in_minutes=None<span class="p">, </span>delivery_policy=None<span class="p">, </span>endpoint=None<span class="p">, </span>endpoint_auto_confirms=None<span class="p">, </span>filter_policy=None<span class="p">, </span>protocol=None<span class="p">, </span>raw_message_delivery=None<span class="p">, </span>topic=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetTopicSubscription<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/sns?tab=doc#TopicSubscriptionState">TopicSubscriptionState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/sns?tab=doc#TopicSubscription">TopicSubscription</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Sns.TopicSubscription.html">TopicSubscription</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Sns.TopicSubscriptionState.html">TopicSubscriptionState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
    <dd>{{% md %}}The ARN of the subscription stored as a more user-friendly property
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Confirmation<wbr>Timeout<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delivery<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Auto<wbr>Confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filter<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Raw<wbr>Message<wbr>Delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
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
    <dd>{{% md %}}The ARN of the subscription stored as a more user-friendly property
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Confirmation<wbr>Timeout<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Delivery<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Endpoint<wbr>Auto<wbr>Confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filter<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Raw<wbr>Message<wbr>Delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">interface{}</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
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
    <dd>{{% md %}}The ARN of the subscription stored as a more user-friendly property
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>confirmation<wbr>Timeout<wbr>In<wbr>Minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delivery<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint<wbr>Auto<wbr>Confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filter<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>raw<wbr>Message<wbr>Delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">string | Topic</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
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
    <dd>{{% md %}}The ARN of the subscription stored as a more user-friendly property
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>confirmation_<wbr>timeout_<wbr>in_<wbr>minutes</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Integer indicating number of minutes to wait in retying mode for fetching subscription arn before marking it as failure. Only applicable for http and https protocols (default is 1 minute).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>delivery_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}JSON String with the delivery policy (retries, backoff, etc.) that will be used in the subscription - this only applies to HTTP/S subscriptions. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/DeliveryPolicies.html) for more details.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The endpoint to send data to, the contents will vary with the protocol. (see below for more information)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>endpoint_<wbr>auto_<wbr>confirms</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether the end point is capable of [auto confirming subscription](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToHttp.html#SendMessageToHttp.prepare) e.g., PagerDuty (default is false)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filter_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}JSON String with the filter policy that will be used in the subscription to filter messages seen by the target resource. Refer to the [SNS docs](https://docs.aws.amazon.com/sns/latest/dg/message-filtering.html) for more details.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>protocol</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The protocol to use. The possible values for this are: `sqs`, `sms`, `lambda`, `application`. (`http` or `https` are partially supported, see below) (`email` is an option but is unsupported, see below).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>raw_<wbr>message_<wbr>delivery</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean indicating whether or not to enable raw message delivery (the original message is directly passed, not wrapped in JSON with the original message in the message property) (default is false).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}The ARN of the SNS topic to subscribe to
{{% /md %}}</dd>

</dl>
{{% /choosable %}}









