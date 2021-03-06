
---
title: "UserPoolClient"
block_external_search_index: true
---

Provides a Cognito User Pool Client resource.

## Example Usage

### Create a basic user pool client

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const pool = new aws.cognito.UserPool("pool", {});
const client = new aws.cognito.UserPoolClient("client", {
    userPoolId: pool.id,
});
```

### Create a user pool client with no SRP authentication

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const pool = new aws.cognito.UserPool("pool", {});
const client = new aws.cognito.UserPoolClient("client", {
    explicitAuthFlows: ["ADMIN_NO_SRP_AUTH"],
    generateSecret: true,
    userPoolId: pool.id,
});
```

### Create a user pool client with pinpoint analytics

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const current = aws.getCallerIdentity();
const testUserPool = new aws.cognito.UserPool("test", {});
const testApp = new aws.pinpoint.App("test", {});
const testRole = new aws.iam.Role("test", {
    assumeRolePolicy: `{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": "sts:AssumeRole",
      "Principal": {
        "Service": "cognito-idp.amazonaws.com"
      },
      "Effect": "Allow",
      "Sid": ""
    }
  ]
}
`,
});
const testRolePolicy = new aws.iam.RolePolicy("test", {
    policy: pulumi.interpolate`{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "mobiletargeting:UpdateEndpoint",
        "mobiletargeting:PutItems"
      ],
      "Effect": "Allow",
      "Resource": "arn:aws:mobiletargeting:*:${current.accountId}:apps/${testApp.applicationId}*"
    }
  ]
}
`,
    role: testRole.id,
});
const testUserPoolClient = new aws.cognito.UserPoolClient("test", {
    analyticsConfiguration: {
        applicationId: testApp.applicationId,
        externalId: "some_id",
        roleArn: testRole.arn,
        userDataShared: true,
    },
    userPoolId: testUserPool.id,
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/cognito_user_pool_client.markdown.



## Create a UserPoolClient Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cognito/#UserPoolClient">UserPoolClient</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cognito/#UserPoolClientArgs">UserPoolClientArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">UserPoolClient</span><span class="p">(resource_name, opts=None, </span>allowed_oauth_flows=None<span class="p">, </span>allowed_oauth_flows_user_pool_client=None<span class="p">, </span>allowed_oauth_scopes=None<span class="p">, </span>analytics_configuration=None<span class="p">, </span>callback_urls=None<span class="p">, </span>default_redirect_uri=None<span class="p">, </span>explicit_auth_flows=None<span class="p">, </span>generate_secret=None<span class="p">, </span>logout_urls=None<span class="p">, </span>name=None<span class="p">, </span>prevent_user_existence_errors=None<span class="p">, </span>read_attributes=None<span class="p">, </span>refresh_token_validity=None<span class="p">, </span>supported_identity_providers=None<span class="p">, </span>user_pool_id=None<span class="p">, </span>write_attributes=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewUserPoolClient<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cognito?tab=doc#UserPoolClientArgs">UserPoolClientArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cognito?tab=doc#UserPoolClient">UserPoolClient</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cognito.UserPoolClient.html">UserPoolClient</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cognito.Inputs.UserPoolClientArgs.html">UserPoolClientArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Allowed<wbr>Oauth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Oauth<wbr>Flows<wbr>User<wbr>Pool<wbr>Client</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Oauth<wbr>Scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Analytics<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Callback<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Redirect<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Explicit<wbr>Auth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Generate<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Logout<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prevent<wbr>User<wbr>Existence<wbr>Errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Read<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Refresh<wbr>Token<wbr>Validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Supported<wbr>Identity<wbr>Providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>User<wbr>Pool<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Write<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Oauth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Oauth<wbr>Flows<wbr>User<wbr>Pool<wbr>Client</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Oauth<wbr>Scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Analytics<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">*User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Callback<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Redirect<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Explicit<wbr>Auth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Generate<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Logout<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prevent<wbr>User<wbr>Existence<wbr>Errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Read<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Refresh<wbr>Token<wbr>Validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Supported<wbr>Identity<wbr>Providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>User<wbr>Pool<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Write<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allowed<wbr>Oauth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allowed<wbr>Oauth<wbr>Flows<wbr>User<wbr>Pool<wbr>Client</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allowed<wbr>Oauth<wbr>Scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>analytics<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>callback<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Redirect<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>explicit<wbr>Auth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>generate<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>logout<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prevent<wbr>User<wbr>Existence<wbr>Errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>read<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>refresh<wbr>Token<wbr>Validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>supported<wbr>Identity<wbr>Providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>user<wbr>Pool<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>write<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allowed_<wbr>oauth_<wbr>flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allowed_<wbr>oauth_<wbr>flows_<wbr>user_<wbr>pool_<wbr>client</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allowed_<wbr>oauth_<wbr>scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>analytics_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">Dict[User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>callback_<wbr>urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>redirect_<wbr>uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>explicit_<wbr>auth_<wbr>flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>generate_<wbr>secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>logout_<wbr>urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prevent_<wbr>user_<wbr>existence_<wbr>errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>read_<wbr>attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>refresh_<wbr>token_<wbr>validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>supported_<wbr>identity_<wbr>providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>user_<wbr>pool_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>write_<wbr>attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## UserPoolClient Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Allowed<wbr>Oauth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Allowed<wbr>Oauth<wbr>Flows<wbr>User<wbr>Pool<wbr>Client</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Allowed<wbr>Oauth<wbr>Scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Analytics<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Callback<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Client<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The client secret of the user pool client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Redirect<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Explicit<wbr>Auth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Generate<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Logout<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Prevent<wbr>User<wbr>Existence<wbr>Errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Read<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Refresh<wbr>Token<wbr>Validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Supported<wbr>Identity<wbr>Providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>User<wbr>Pool<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Write<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Allowed<wbr>Oauth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Allowed<wbr>Oauth<wbr>Flows<wbr>User<wbr>Pool<wbr>Client</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Allowed<wbr>Oauth<wbr>Scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Analytics<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">*User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Callback<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Client<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The client secret of the user pool client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Default<wbr>Redirect<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Explicit<wbr>Auth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Generate<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Logout<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Prevent<wbr>User<wbr>Existence<wbr>Errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Read<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Refresh<wbr>Token<wbr>Validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Supported<wbr>Identity<wbr>Providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>User<wbr>Pool<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Write<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>allowed<wbr>Oauth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>allowed<wbr>Oauth<wbr>Flows<wbr>User<wbr>Pool<wbr>Client</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>allowed<wbr>Oauth<wbr>Scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>analytics<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>callback<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>client<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The client secret of the user pool client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default<wbr>Redirect<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>explicit<wbr>Auth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>generate<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>logout<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>prevent<wbr>User<wbr>Existence<wbr>Errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>read<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>refresh<wbr>Token<wbr>Validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>supported<wbr>Identity<wbr>Providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>user<wbr>Pool<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>write<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>allowed_<wbr>oauth_<wbr>flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>allowed_<wbr>oauth_<wbr>flows_<wbr>user_<wbr>pool_<wbr>client</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>allowed_<wbr>oauth_<wbr>scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>analytics_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">Dict[User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>callback_<wbr>urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>client_<wbr>secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The client secret of the user pool client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>default_<wbr>redirect_<wbr>uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>explicit_<wbr>auth_<wbr>flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>generate_<wbr>secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>logout_<wbr>urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>prevent_<wbr>user_<wbr>existence_<wbr>errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>read_<wbr>attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>refresh_<wbr>token_<wbr>validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>supported_<wbr>identity_<wbr>providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>user_<wbr>pool_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>write_<wbr>attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing UserPoolClient Resource

Get an existing UserPoolClient resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cognito/#UserPoolClientState">UserPoolClientState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cognito/#UserPoolClient">UserPoolClient</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>allowed_oauth_flows=None<span class="p">, </span>allowed_oauth_flows_user_pool_client=None<span class="p">, </span>allowed_oauth_scopes=None<span class="p">, </span>analytics_configuration=None<span class="p">, </span>callback_urls=None<span class="p">, </span>client_secret=None<span class="p">, </span>default_redirect_uri=None<span class="p">, </span>explicit_auth_flows=None<span class="p">, </span>generate_secret=None<span class="p">, </span>logout_urls=None<span class="p">, </span>name=None<span class="p">, </span>prevent_user_existence_errors=None<span class="p">, </span>read_attributes=None<span class="p">, </span>refresh_token_validity=None<span class="p">, </span>supported_identity_providers=None<span class="p">, </span>user_pool_id=None<span class="p">, </span>write_attributes=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetUserPoolClient<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cognito?tab=doc#UserPoolClientState">UserPoolClientState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cognito?tab=doc#UserPoolClient">UserPoolClient</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cognito.UserPoolClient.html">UserPoolClient</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Cognito.UserPoolClientState.html">UserPoolClientState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Allowed<wbr>Oauth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Oauth<wbr>Flows<wbr>User<wbr>Pool<wbr>Client</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Oauth<wbr>Scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Analytics<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Callback<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Client<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The client secret of the user pool client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Redirect<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Explicit<wbr>Auth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Generate<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Logout<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prevent<wbr>User<wbr>Existence<wbr>Errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Read<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Refresh<wbr>Token<wbr>Validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Supported<wbr>Identity<wbr>Providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>User<wbr>Pool<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Write<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Oauth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Oauth<wbr>Flows<wbr>User<wbr>Pool<wbr>Client</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Oauth<wbr>Scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Analytics<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">*User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Callback<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Client<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The client secret of the user pool client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Redirect<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Explicit<wbr>Auth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Generate<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Logout<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Prevent<wbr>User<wbr>Existence<wbr>Errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Read<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Refresh<wbr>Token<wbr>Validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Supported<wbr>Identity<wbr>Providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>User<wbr>Pool<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Write<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allowed<wbr>Oauth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allowed<wbr>Oauth<wbr>Flows<wbr>User<wbr>Pool<wbr>Client</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allowed<wbr>Oauth<wbr>Scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>analytics<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration?</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>callback<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>client<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The client secret of the user pool client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Redirect<wbr>Uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>explicit<wbr>Auth<wbr>Flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>generate<wbr>Secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>logout<wbr>Urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prevent<wbr>User<wbr>Existence<wbr>Errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>read<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>refresh<wbr>Token<wbr>Validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>supported<wbr>Identity<wbr>Providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>user<wbr>Pool<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>write<wbr>Attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allowed_<wbr>oauth_<wbr>flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth flows (code, implicit, client_credentials).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allowed_<wbr>oauth_<wbr>flows_<wbr>user_<wbr>pool_<wbr>client</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>allowed_<wbr>oauth_<wbr>scopes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed OAuth scopes (phone, email, openid, profile, and aws.cognito.signin.user.admin).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>analytics_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#userpoolclientanalyticsconfiguration">Dict[User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Pinpoint analytics configuration for collecting metrics for this user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>callback_<wbr>urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed callback URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>client_<wbr>secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The client secret of the user pool client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>redirect_<wbr>uri</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The default redirect URI. Must be in the list of callback URLs.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>explicit_<wbr>auth_<wbr>flows</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY,  USER_PASSWORD_AUTH, ALLOW_ADMIN_USER_PASSWORD_AUTH, ALLOW_CUSTOM_AUTH, ALLOW_USER_PASSWORD_AUTH, ALLOW_USER_SRP_AUTH, ALLOW_REFRESH_TOKEN_AUTH).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>generate_<wbr>secret</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Should an application secret be generated.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>logout_<wbr>urls</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of allowed logout URLs for the identity providers.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the application client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>prevent_<wbr>user_<wbr>existence_<wbr>errors</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Choose which errors and responses are returned by Cognito APIs during authentication, account confirmation, and password recovery when the user does not exist in the user pool. When set to `ENABLED` and the user does not exist, authentication returns an error indicating either the username or password was incorrect, and account confirmation and password recovery return a response indicating a code was sent to a simulated destination. When set to `LEGACY`, those APIs will return a `UserNotFoundException` exception if the user does not exist in the user pool.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>read_<wbr>attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can read from.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>refresh_<wbr>token_<wbr>validity</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The time limit in days refresh tokens are valid for.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>supported_<wbr>identity_<wbr>providers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of provider names for the identity providers that are supported on this client.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>user_<wbr>pool_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The user pool the client belongs to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>write_<wbr>attributes</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of user pool attributes the application client can write to.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>User<wbr>Pool<wbr>Client<wbr>Analytics<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#UserPoolClientAnalyticsConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#UserPoolClientAnalyticsConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cognito?tab=doc#UserPoolClientAnalyticsConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/cognito?tab=doc#UserPoolClientAnalyticsConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Application<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The application ID for an Amazon Pinpoint application.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>External<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}An ID for the Analytics Configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that authorizes Amazon Cognito to publish events to Amazon Pinpoint analytics.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>User<wbr>Data<wbr>Shared</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If set to `true`, Amazon Cognito will include user data in the events it publishes to Amazon Pinpoint analytics.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Application<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The application ID for an Amazon Pinpoint application.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>External<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}An ID for the Analytics Configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that authorizes Amazon Cognito to publish events to Amazon Pinpoint analytics.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>User<wbr>Data<wbr>Shared</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If set to `true`, Amazon Cognito will include user data in the events it publishes to Amazon Pinpoint analytics.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>application<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The application ID for an Amazon Pinpoint application.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>external<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}An ID for the Analytics Configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that authorizes Amazon Cognito to publish events to Amazon Pinpoint analytics.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>user<wbr>Data<wbr>Shared</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If set to `true`, Amazon Cognito will include user data in the events it publishes to Amazon Pinpoint analytics.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>application_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The application ID for an Amazon Pinpoint application.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>external<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}An ID for the Analytics Configuration.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ARN of an IAM role that authorizes Amazon Cognito to publish events to Amazon Pinpoint analytics.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>user<wbr>Data<wbr>Shared</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If set to `true`, Amazon Cognito will include user data in the events it publishes to Amazon Pinpoint analytics.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







