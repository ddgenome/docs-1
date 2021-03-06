
---
title: "ReceiptRule"
block_external_search_index: true
---

Provides an SES receipt rule resource

## Example Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

// Add a header to the email and store it in S3
const store = new aws.ses.ReceiptRule("store", {
    addHeaderActions: [{
        headerName: "Custom-Header",
        headerValue: "Added by SES",
        position: 1,
    }],
    enabled: true,
    recipients: ["karen@example.com"],
    ruleSetName: "default-rule-set",
    s3Actions: [{
        bucketName: "emails",
        position: 2,
    }],
    scanEnabled: true,
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/ses_receipt_rule.html.markdown.



## Create a ReceiptRule Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/ses/#ReceiptRule">ReceiptRule</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/ses/#ReceiptRuleArgs">ReceiptRuleArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">ReceiptRule</span><span class="p">(resource_name, opts=None, </span>add_header_actions=None<span class="p">, </span>after=None<span class="p">, </span>bounce_actions=None<span class="p">, </span>enabled=None<span class="p">, </span>lambda_actions=None<span class="p">, </span>name=None<span class="p">, </span>recipients=None<span class="p">, </span>rule_set_name=None<span class="p">, </span>s3_actions=None<span class="p">, </span>scan_enabled=None<span class="p">, </span>sns_actions=None<span class="p">, </span>stop_actions=None<span class="p">, </span>tls_policy=None<span class="p">, </span>workmail_actions=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewReceiptRule<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleArgs">ReceiptRuleArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRule">ReceiptRule</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Ses.ReceiptRule.html">ReceiptRule</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Ses.Inputs.ReceiptRuleArgs.html">ReceiptRuleArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Add<wbr>Header<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">List&lt;Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>After</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bounce<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">List&lt;Receipt<wbr>Rule<wbr>Bounce<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Lambda<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">List&lt;Receipt<wbr>Rule<wbr>Lambda<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Rule<wbr>Set<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">List&lt;Receipt<wbr>Rule<wbr>S3Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Scan<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sns<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">List&lt;Receipt<wbr>Rule<wbr>Sns<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Stop<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">List&lt;Receipt<wbr>Rule<wbr>Stop<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tls<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Workmail<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">List&lt;Receipt<wbr>Rule<wbr>Workmail<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Add<wbr>Header<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">[]Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>After</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bounce<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">[]Receipt<wbr>Rule<wbr>Bounce<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Lambda<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">[]Receipt<wbr>Rule<wbr>Lambda<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Rule<wbr>Set<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">[]Receipt<wbr>Rule<wbr>S3Action</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Scan<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sns<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">[]Receipt<wbr>Rule<wbr>Sns<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Stop<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">[]Receipt<wbr>Rule<wbr>Stop<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tls<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Workmail<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">[]Receipt<wbr>Rule<wbr>Workmail<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>add<wbr>Header<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>after</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bounce<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">Receipt<wbr>Rule<wbr>Bounce<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>lambda<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">Receipt<wbr>Rule<wbr>Lambda<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>rule<wbr>Set<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">Receipt<wbr>Rule<wbr>S3Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>scan<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sns<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">Receipt<wbr>Rule<wbr>Sns<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>stop<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">Receipt<wbr>Rule<wbr>Stop<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tls<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>workmail<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">Receipt<wbr>Rule<wbr>Workmail<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>add_<wbr>header_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">List[Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>after</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bounce_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">List[Receipt<wbr>Rule<wbr>Bounce<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>lambda_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">List[Receipt<wbr>Rule<wbr>Lambda<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>rule_<wbr>set_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">List[Receipt<wbr>Rule<wbr>S3Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>scan_<wbr>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sns_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">List[Receipt<wbr>Rule<wbr>Sns<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>stop_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">List[Receipt<wbr>Rule<wbr>Stop<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tls_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>workmail_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">List[Receipt<wbr>Rule<wbr>Workmail<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## ReceiptRule Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Add<wbr>Header<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">List&lt;Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>After</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Bounce<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">List&lt;Receipt<wbr>Rule<wbr>Bounce<wbr>Action&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Lambda<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">List&lt;Receipt<wbr>Rule<wbr>Lambda<wbr>Action&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Rule<wbr>Set<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>S3Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">List&lt;Receipt<wbr>Rule<wbr>S3Action&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Scan<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sns<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">List&lt;Receipt<wbr>Rule<wbr>Sns<wbr>Action&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Stop<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">List&lt;Receipt<wbr>Rule<wbr>Stop<wbr>Action&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tls<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Workmail<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">List&lt;Receipt<wbr>Rule<wbr>Workmail<wbr>Action&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Add<wbr>Header<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">[]Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>After</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Bounce<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">[]Receipt<wbr>Rule<wbr>Bounce<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Lambda<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">[]Receipt<wbr>Rule<wbr>Lambda<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Rule<wbr>Set<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>S3Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">[]Receipt<wbr>Rule<wbr>S3Action</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Scan<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sns<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">[]Receipt<wbr>Rule<wbr>Sns<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Stop<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">[]Receipt<wbr>Rule<wbr>Stop<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Tls<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Workmail<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">[]Receipt<wbr>Rule<wbr>Workmail<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>add<wbr>Header<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>after</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>bounce<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">Receipt<wbr>Rule<wbr>Bounce<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>lambda<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">Receipt<wbr>Rule<wbr>Lambda<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>rule<wbr>Set<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>s3Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">Receipt<wbr>Rule<wbr>S3Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>scan<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sns<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">Receipt<wbr>Rule<wbr>Sns<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>stop<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">Receipt<wbr>Rule<wbr>Stop<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tls<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>workmail<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">Receipt<wbr>Rule<wbr>Workmail<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>add_<wbr>header_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">List[Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>after</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>bounce_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">List[Receipt<wbr>Rule<wbr>Bounce<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>lambda_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">List[Receipt<wbr>Rule<wbr>Lambda<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>rule_<wbr>set_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>s3_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">List[Receipt<wbr>Rule<wbr>S3Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>scan_<wbr>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sns_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">List[Receipt<wbr>Rule<wbr>Sns<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>stop_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">List[Receipt<wbr>Rule<wbr>Stop<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>tls_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>workmail_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">List[Receipt<wbr>Rule<wbr>Workmail<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing ReceiptRule Resource

Get an existing ReceiptRule resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/ses/#ReceiptRuleState">ReceiptRuleState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/ses/#ReceiptRule">ReceiptRule</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>add_header_actions=None<span class="p">, </span>after=None<span class="p">, </span>bounce_actions=None<span class="p">, </span>enabled=None<span class="p">, </span>lambda_actions=None<span class="p">, </span>name=None<span class="p">, </span>recipients=None<span class="p">, </span>rule_set_name=None<span class="p">, </span>s3_actions=None<span class="p">, </span>scan_enabled=None<span class="p">, </span>sns_actions=None<span class="p">, </span>stop_actions=None<span class="p">, </span>tls_policy=None<span class="p">, </span>workmail_actions=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetReceiptRule<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleState">ReceiptRuleState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRule">ReceiptRule</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Ses.ReceiptRule.html">ReceiptRule</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Ses.ReceiptRuleState.html">ReceiptRuleState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Add<wbr>Header<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">List&lt;Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>After</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bounce<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">List&lt;Receipt<wbr>Rule<wbr>Bounce<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Lambda<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">List&lt;Receipt<wbr>Rule<wbr>Lambda<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rule<wbr>Set<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">List&lt;Receipt<wbr>Rule<wbr>S3Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Scan<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sns<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">List&lt;Receipt<wbr>Rule<wbr>Sns<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Stop<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">List&lt;Receipt<wbr>Rule<wbr>Stop<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tls<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Workmail<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">List&lt;Receipt<wbr>Rule<wbr>Workmail<wbr>Action<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Add<wbr>Header<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">[]Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>After</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Bounce<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">[]Receipt<wbr>Rule<wbr>Bounce<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Lambda<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">[]Receipt<wbr>Rule<wbr>Lambda<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rule<wbr>Set<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">[]Receipt<wbr>Rule<wbr>S3Action</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Scan<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sns<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">[]Receipt<wbr>Rule<wbr>Sns<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Stop<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">[]Receipt<wbr>Rule<wbr>Stop<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tls<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Workmail<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">[]Receipt<wbr>Rule<wbr>Workmail<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>add<wbr>Header<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>after</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bounce<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">Receipt<wbr>Rule<wbr>Bounce<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>lambda<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">Receipt<wbr>Rule<wbr>Lambda<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rule<wbr>Set<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">Receipt<wbr>Rule<wbr>S3Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>scan<wbr>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sns<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">Receipt<wbr>Rule<wbr>Sns<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>stop<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">Receipt<wbr>Rule<wbr>Stop<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tls<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>workmail<wbr>Actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">Receipt<wbr>Rule<wbr>Workmail<wbr>Action[]?</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>add_<wbr>header_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleaddheaderaction">List[Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Add Header Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>after</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the rule to place this rule after
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>bounce_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulebounceaction">List[Receipt<wbr>Rule<wbr>Bounce<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Bounce Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, the rule will be enabled
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>lambda_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulelambdaaction">List[Receipt<wbr>Rule<wbr>Lambda<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Lambda Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>recipients</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of email addresses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rule_<wbr>set_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the rule set
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrules3action">List[Receipt<wbr>Rule<wbr>S3Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of S3 Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>scan_<wbr>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If true, incoming emails will be scanned for spam and viruses
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sns_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulesnsaction">List[Receipt<wbr>Rule<wbr>Sns<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of SNS Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>stop_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptrulestopaction">List[Receipt<wbr>Rule<wbr>Stop<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of Stop Action blocks. Documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tls_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Require or Optional
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>workmail_<wbr>actions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#receiptruleworkmailaction">List[Receipt<wbr>Rule<wbr>Workmail<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}A list of WorkMail Action blocks. Documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Receipt<wbr>Rule<wbr>Add<wbr>Header<wbr>Action</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#ReceiptRuleAddHeaderAction">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#ReceiptRuleAddHeaderAction">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleAddHeaderActionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleAddHeaderActionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Header<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the header to add
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Header<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The value of the header to add
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Header<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the header to add
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Header<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The value of the header to add
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>header<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the header to add
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>header<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The value of the header to add
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>header<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the header to add
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>header<wbr>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The value of the header to add
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Receipt<wbr>Rule<wbr>Bounce<wbr>Action</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#ReceiptRuleBounceAction">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#ReceiptRuleBounceAction">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleBounceActionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleBounceActionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Message</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The message to send
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Sender</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The email address of the sender
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Smtp<wbr>Reply<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The RFC 5321 SMTP reply code
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The RFC 3463 SMTP enhanced status code
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Message</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The message to send
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Sender</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The email address of the sender
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Smtp<wbr>Reply<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The RFC 5321 SMTP reply code
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The RFC 3463 SMTP enhanced status code
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>message</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The message to send
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>sender</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The email address of the sender
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>smtp<wbr>Reply<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The RFC 5321 SMTP reply code
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The RFC 3463 SMTP enhanced status code
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>message</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The message to send
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>sender</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The email address of the sender
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>smtp<wbr>Reply<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The RFC 5321 SMTP reply code
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>status_<wbr>code</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The RFC 3463 SMTP enhanced status code
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Receipt<wbr>Rule<wbr>Lambda<wbr>Action</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#ReceiptRuleLambdaAction">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#ReceiptRuleLambdaAction">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleLambdaActionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleLambdaActionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Function<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the Lambda function to invoke
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Invocation<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Event or RequestResponse
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Function<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the Lambda function to invoke
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Invocation<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Event or RequestResponse
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>function<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the Lambda function to invoke
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>invocation<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Event or RequestResponse
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>function_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the Lambda function to invoke
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>invocation<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Event or RequestResponse
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Receipt<wbr>Rule<wbr>S3Action</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#ReceiptRuleS3Action">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#ReceiptRuleS3Action">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleS3ActionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleS3ActionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Bucket<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of the KMS key
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Object<wbr>Key<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The key prefix of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
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
    <dd>{{% md %}}The name of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of the KMS key
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Object<wbr>Key<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The key prefix of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
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
    <dd>{{% md %}}The name of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of the KMS key
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>object<wbr>Key<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The key prefix of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
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
    <dd>{{% md %}}The name of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>key_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the KMS key
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>object<wbr>Key<wbr>Prefix</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The key prefix of the S3 bucket
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Receipt<wbr>Rule<wbr>Sns<wbr>Action</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#ReceiptRuleSnsAction">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#ReceiptRuleSnsAction">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleSnsActionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleSnsActionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Receipt<wbr>Rule<wbr>Stop<wbr>Action</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#ReceiptRuleStopAction">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#ReceiptRuleStopAction">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleStopActionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleStopActionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Scope</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The scope to apply
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Scope</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The scope to apply
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>scope</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The scope to apply
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>scope</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The scope to apply
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Receipt<wbr>Rule<wbr>Workmail<wbr>Action</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#ReceiptRuleWorkmailAction">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#ReceiptRuleWorkmailAction">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleWorkmailActionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ses?tab=doc#ReceiptRuleWorkmailActionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Organization<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the WorkMail organization
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Organization<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the WorkMail organization
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Position</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>organization<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of the WorkMail organization
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>organization<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of the WorkMail organization
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>position</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The position of the action in the receipt rule
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>topic_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an SNS topic to notify
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







