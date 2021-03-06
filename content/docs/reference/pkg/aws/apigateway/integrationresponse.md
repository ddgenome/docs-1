
---
title: "IntegrationResponse"
block_external_search_index: true
---

Provides an HTTP Method Integration Response for an API Gateway Resource.

> **Note:** Depends on having `aws.apigateway.Integration` inside your rest api. To ensure this
you might need to add an explicit `depends_on` for clean runs.

## Example Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const myDemoAPI = new aws.apigateway.RestApi("MyDemoAPI", {
    description: "This is my API for demonstration purposes",
});
const myDemoResource = new aws.apigateway.Resource("MyDemoResource", {
    parentId: myDemoAPI.rootResourceId,
    pathPart: "mydemoresource",
    restApi: myDemoAPI.id,
});
const myDemoMethod = new aws.apigateway.Method("MyDemoMethod", {
    authorization: "NONE",
    httpMethod: "GET",
    resourceId: myDemoResource.id,
    restApi: myDemoAPI.id,
});
const myDemoIntegration = new aws.apigateway.Integration("MyDemoIntegration", {
    httpMethod: myDemoMethod.httpMethod,
    resourceId: myDemoResource.id,
    restApi: myDemoAPI.id,
    type: "MOCK",
});
const response200 = new aws.apigateway.MethodResponse("response_200", {
    httpMethod: myDemoMethod.httpMethod,
    resourceId: myDemoResource.id,
    restApi: myDemoAPI.id,
    statusCode: "200",
});
const myDemoIntegrationResponse = new aws.apigateway.IntegrationResponse("MyDemoIntegrationResponse", {
    httpMethod: myDemoMethod.httpMethod,
    resourceId: myDemoResource.id,
    // Transforms the backend JSON response to XML
    responseTemplates: {
        "application/xml": `#set($inputRoot = $input.path('$'))
<?xml version="1.0" encoding="UTF-8"?>
<message>
    $inputRoot.body
</message>
`,
    },
    restApi: myDemoAPI.id,
    statusCode: response200.statusCode,
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/api_gateway_integration_response.html.markdown.



## Create a IntegrationResponse Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/apigateway/#IntegrationResponse">IntegrationResponse</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/apigateway/#IntegrationResponseArgs">IntegrationResponseArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">IntegrationResponse</span><span class="p">(resource_name, opts=None, </span>content_handling=None<span class="p">, </span>http_method=None<span class="p">, </span>resource_id=None<span class="p">, </span>response_parameters=None<span class="p">, </span>response_templates=None<span class="p">, </span>rest_api=None<span class="p">, </span>selection_pattern=None<span class="p">, </span>status_code=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewIntegrationResponse<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/apigateway?tab=doc#IntegrationResponseArgs">IntegrationResponseArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/apigateway?tab=doc#IntegrationResponse">IntegrationResponse</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Apigateway.IntegrationResponse.html">IntegrationResponse</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.ApiGateway.Inputs.IntegrationResponseArgs.html">IntegrationResponseArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Content<wbr>Handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Http<wbr>Method</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Response<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Response<wbr>Templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Rest<wbr>Api</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Selection<wbr>Pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Content<wbr>Handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Http<wbr>Method</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Response<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Response<wbr>Templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Rest<wbr>Api</span>
        <span class="property-indicator"></span>
        <span class="property-type">interface{}</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Selection<wbr>Pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>content<wbr>Handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>http<wbr>Method</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>response<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>response<wbr>Templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>rest<wbr>Api</span>
        <span class="property-indicator"></span>
        <span class="property-type">string | RestApi</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>selection<wbr>Pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>content_<wbr>handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>http_<wbr>method</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>resource_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>response_<wbr>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>response_<wbr>templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>rest_<wbr>api</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>selection_<wbr>pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>status_<wbr>code</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## IntegrationResponse Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Content<wbr>Handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Http<wbr>Method</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Response<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Response<wbr>Templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Rest<wbr>Api</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Selection<wbr>Pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Content<wbr>Handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Http<wbr>Method</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Response<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Response<wbr>Templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Rest<wbr>Api</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Selection<wbr>Pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>content<wbr>Handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>http<wbr>Method</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>response<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>response<wbr>Templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>rest<wbr>Api</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>selection<wbr>Pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>content_<wbr>handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>http_<wbr>method</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>resource_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>response_<wbr>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>response_<wbr>templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>rest_<wbr>api</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>selection_<wbr>pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>status_<wbr>code</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing IntegrationResponse Resource

Get an existing IntegrationResponse resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/apigateway/#IntegrationResponseState">IntegrationResponseState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/apigateway/#IntegrationResponse">IntegrationResponse</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>content_handling=None<span class="p">, </span>http_method=None<span class="p">, </span>resource_id=None<span class="p">, </span>response_parameters=None<span class="p">, </span>response_templates=None<span class="p">, </span>rest_api=None<span class="p">, </span>selection_pattern=None<span class="p">, </span>status_code=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetIntegrationResponse<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/apigateway?tab=doc#IntegrationResponseState">IntegrationResponseState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/apigateway?tab=doc#IntegrationResponse">IntegrationResponse</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Apigateway.IntegrationResponse.html">IntegrationResponse</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Apigateway.IntegrationResponseState.html">IntegrationResponseState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Content<wbr>Handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Http<wbr>Method</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Response<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Response<wbr>Templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rest<wbr>Api</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Selection<wbr>Pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Content<wbr>Handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Http<wbr>Method</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Response<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Response<wbr>Templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rest<wbr>Api</span>
        <span class="property-indicator"></span>
        <span class="property-type">interface{}</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Selection<wbr>Pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>content<wbr>Handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>http<wbr>Method</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>response<wbr>Parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>response<wbr>Templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rest<wbr>Api</span>
        <span class="property-indicator"></span>
        <span class="property-type">string | RestApi</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>selection<wbr>Pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>status<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>content_<wbr>handling</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies how to handle request payload content type conversions. Supported values are `CONVERT_TO_BINARY` and `CONVERT_TO_TEXT`. If this property is not defined, the response payload will be passed through from the integration response to the method response without modification.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>http_<wbr>method</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The HTTP method (`GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`, `ANY`)
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>resource_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The API resource ID
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>response_<wbr>parameters</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A map of response parameters that can be read from the backend response.
For example: `response_parameters = { "method.response.header.X-Some-Header" = "integration.response.header.X-Some-Other-Header" }`
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>response_<wbr>templates</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}A map specifying the templates used to transform the integration response body
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rest_<wbr>api</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}The ID of the associated REST API
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>selection_<wbr>pattern</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Specifies the regular expression pattern used to choose
an integration response based on the response from the backend. Setting this to `-` makes the integration the default one.
If the backend is an `AWS` Lambda function, the AWS Lambda function error header is matched.
For all other `HTTP` and `AWS` backends, the HTTP status code is matched.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>status_<wbr>code</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The HTTP status code
{{% /md %}}</dd>

</dl>
{{% /choosable %}}









