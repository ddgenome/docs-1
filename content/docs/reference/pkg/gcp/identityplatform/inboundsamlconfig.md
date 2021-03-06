
---
title: "InboundSamlConfig"
block_external_search_index: true
---

Inbound SAML configuration for a Identity Toolkit project.

You must enable the
[Google Identity Platform](https://console.cloud.google.com/marketplace/details/google-cloud-platform/customer-identity) in
the marketplace prior to using this resource.

> This content is derived from https://github.com/terraform-providers/terraform-provider-google/blob/master/website/docs/r/identity_platform_inbound_saml_config.html.markdown.



## Create a InboundSamlConfig Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/identityplatform/#InboundSamlConfig">InboundSamlConfig</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/identityplatform/#InboundSamlConfigArgs">InboundSamlConfigArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">InboundSamlConfig</span><span class="p">(resource_name, opts=None, </span>display_name=None<span class="p">, </span>enabled=None<span class="p">, </span>idp_config=None<span class="p">, </span>name=None<span class="p">, </span>project=None<span class="p">, </span>sp_config=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewInboundSamlConfig<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfigArgs">InboundSamlConfigArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfig">InboundSamlConfig</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Identityplatform.InboundSamlConfig.html">InboundSamlConfig</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.IdentityPlatform.Inputs.InboundSamlConfigArgs.html">InboundSamlConfigArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Idp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Pulumi.<wbr>Gcp.<wbr>Identity<wbr>Platform.<wbr>Inputs.<wbr>Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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

    <dt class="property-required"
            title="Required">
        <span>Sp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Pulumi.<wbr>Gcp.<wbr>Identity<wbr>Platform.<wbr>Inputs.<wbr>Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Idp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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

    <dt class="property-required"
            title="Required">
        <span>Sp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>idp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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

    <dt class="property-required"
            title="Required">
        <span>sp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>display_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>idp_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Dict[Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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

    <dt class="property-required"
            title="Required">
        <span>sp_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Dict[Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## InboundSamlConfig Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Idp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Pulumi.<wbr>Gcp.<wbr>Identity<wbr>Platform.<wbr>Outputs.<wbr>Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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
        <span>Sp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Pulumi.<wbr>Gcp.<wbr>Identity<wbr>Platform.<wbr>Outputs.<wbr>Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Idp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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
        <span>Sp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>idp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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
        <span>sp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>display_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>idp_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Dict[Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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
        <span>sp_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Dict[Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing InboundSamlConfig Resource

Get an existing InboundSamlConfig resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/identityplatform/#InboundSamlConfigState">InboundSamlConfigState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/identityplatform/#InboundSamlConfig">InboundSamlConfig</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>display_name=None<span class="p">, </span>enabled=None<span class="p">, </span>idp_config=None<span class="p">, </span>name=None<span class="p">, </span>project=None<span class="p">, </span>sp_config=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetInboundSamlConfig<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfigState">InboundSamlConfigState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfig">InboundSamlConfig</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Identityplatform.InboundSamlConfig.html">InboundSamlConfig</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Identityplatform.InboundSamlConfigState.html">InboundSamlConfigState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Display<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Idp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Pulumi.<wbr>Gcp.<wbr>Identity<wbr>Platform.<wbr>Inputs.<wbr>Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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
        <span>Sp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Pulumi.<wbr>Gcp.<wbr>Identity<wbr>Platform.<wbr>Inputs.<wbr>Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

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
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Idp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">*Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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
        <span>Sp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">*Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

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
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>idp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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
        <span>sp<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config?</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

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
    <dd>{{% md %}}Human friendly display name.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>enabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If this config allows users to sign in with the provider.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>idp_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfig">Dict[Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}SAML IdP configuration when the project acts as the relying party
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the InboundSamlConfig resource. Must start with 'saml.' and can only have alphanumeric characters, hyphens,
underscores or periods. The part after 'saml.' must also start with a lowercase letter, end with an alphanumeric
character, and have at least 2 characters.
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
        <span>sp_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfig">Dict[Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}SAML SP (Service Provider) configuration when the project acts as the relying party to receive and accept an
authentication assertion issued by a SAML identity provider.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#InboundSamlConfigIdpConfig">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#InboundSamlConfigIdpConfig">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfigIdpConfigArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfigIdpConfigOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Idp<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfigidpcertificate">List&lt;Pulumi.<wbr>Gcp.<wbr>Identity<wbr>Platform.<wbr>Inputs.<wbr>Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config<wbr>Idp<wbr>Certificate<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Idp<wbr>Entity<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sign<wbr>Request</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Sso<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Idp<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfigidpcertificate">[]Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config<wbr>Idp<wbr>Certificate</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Idp<wbr>Entity<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sign<wbr>Request</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Sso<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>idp<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfigidpcertificate">Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config<wbr>Idp<wbr>Certificate[]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>idp<wbr>Entity<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sign<wbr>Request</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>sso<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>idp<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigidpconfigidpcertificate">List[Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config<wbr>Idp<wbr>Certificate]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>idp<wbr>Entity<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sign<wbr>Request</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>sso<wbr>Url</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Inbound<wbr>Saml<wbr>Config<wbr>Idp<wbr>Config<wbr>Idp<wbr>Certificate</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#InboundSamlConfigIdpConfigIdpCertificate">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#InboundSamlConfigIdpConfigIdpCertificate">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfigIdpConfigIdpCertificateArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfigIdpConfigIdpCertificateOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>X509Certificate</span>
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
        <span>X509Certificate</span>
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
        <span>x509Certificate</span>
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
        <span>x509Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#InboundSamlConfigSpConfig">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#InboundSamlConfigSpConfig">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfigSpConfigArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfigSpConfigOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Callback<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sp<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfigspcertificate">List&lt;Pulumi.<wbr>Gcp.<wbr>Identity<wbr>Platform.<wbr>Inputs.<wbr>Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config<wbr>Sp<wbr>Certificate<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sp<wbr>Entity<wbr>Id</span>
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
        <span>Callback<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sp<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfigspcertificate">[]Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config<wbr>Sp<wbr>Certificate</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sp<wbr>Entity<wbr>Id</span>
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
        <span>callback<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sp<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfigspcertificate">Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config<wbr>Sp<wbr>Certificate[]?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sp<wbr>Entity<wbr>Id</span>
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
        <span>callback<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sp<wbr>Certificates</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#inboundsamlconfigspconfigspcertificate">List[Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config<wbr>Sp<wbr>Certificate]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sp<wbr>Entity<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Inbound<wbr>Saml<wbr>Config<wbr>Sp<wbr>Config<wbr>Sp<wbr>Certificate</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#InboundSamlConfigSpConfigSpCertificate">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#InboundSamlConfigSpConfigSpCertificate">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfigSpConfigSpCertificateArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/identityplatform?tab=doc#InboundSamlConfigSpConfigSpCertificateOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>X509Certificate</span>
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
        <span>X509Certificate</span>
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
        <span>x509Certificate</span>
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
        <span>x509Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}







