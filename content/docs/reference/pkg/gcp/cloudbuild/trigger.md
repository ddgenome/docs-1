
---
title: "Trigger"
block_external_search_index: true
---

Configuration for an automated build in response to source repository changes.


To get more information about Trigger, see:

* [API documentation](https://cloud.google.com/cloud-build/docs/api/reference/rest/)
* How-to Guides
    * [Automating builds using build triggers](https://cloud.google.com/cloud-build/docs/running-builds/automate-builds)

## Example Usage - Cloudbuild Trigger Filename


```typescript
import * as pulumi from "@pulumi/pulumi";
import * as gcp from "@pulumi/gcp";

const filename_trigger = new gcp.cloudbuild.Trigger("filename-trigger", {
    filename: "cloudbuild.yaml",
    substitutions: {
        _BAZ: "qux",
        _FOO: "bar",
    },
    triggerTemplate: {
        branchName: "master",
        repoName: "my-repo",
    },
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-google/blob/master/website/docs/r/cloudbuild_trigger.html.markdown.



## Create a Trigger Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/cloudbuild/#Trigger">Trigger</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/cloudbuild/#TriggerArgs">TriggerArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">Trigger</span><span class="p">(resource_name, opts=None, </span>build=None<span class="p">, </span>description=None<span class="p">, </span>disabled=None<span class="p">, </span>filename=None<span class="p">, </span>github=None<span class="p">, </span>ignored_files=None<span class="p">, </span>included_files=None<span class="p">, </span>name=None<span class="p">, </span>project=None<span class="p">, </span>substitutions=None<span class="p">, </span>trigger_template=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewTrigger<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerArgs">TriggerArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#Trigger">Trigger</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Cloudbuild.Trigger.html">Trigger</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.CloudBuild.Inputs.TriggerArgs.html">TriggerArgs</a></span>? <span class="nx">args = null<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Inputs.<wbr>Trigger<wbr>Build<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Inputs.<wbr>Trigger<wbr>Github<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ignored<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Included<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>Substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Trigger<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Inputs.<wbr>Trigger<wbr>Trigger<wbr>Template<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">*Trigger<wbr>Build</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">*Trigger<wbr>Github</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ignored<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Included<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>Substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Trigger<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">*Trigger<wbr>Trigger<wbr>Template</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">Trigger<wbr>Build?</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">Trigger<wbr>Github?</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ignored<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>included<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>trigger<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">Trigger<wbr>Trigger<wbr>Template?</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">Dict[Trigger<wbr>Build]</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">Dict[Trigger<wbr>Github]</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ignored_<wbr>files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>included_<wbr>files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>trigger_<wbr>template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">Dict[Trigger<wbr>Trigger<wbr>Template]</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## Trigger Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Outputs.<wbr>Trigger<wbr>Build?</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Create<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Time when the trigger was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Outputs.<wbr>Trigger<wbr>Github?</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ignored<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Included<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>Substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Trigger<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Trigger<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Outputs.<wbr>Trigger<wbr>Trigger<wbr>Template?</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">*Trigger<wbr>Build</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Create<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Time when the trigger was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">*Trigger<wbr>Github</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ignored<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Included<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>Substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Trigger<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Trigger<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">*Trigger<wbr>Trigger<wbr>Template</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">Trigger<wbr>Build?</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>create<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Time when the trigger was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">Trigger<wbr>Github?</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ignored<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>included<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>trigger<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>trigger<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">Trigger<wbr>Trigger<wbr>Template?</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">Dict[Trigger<wbr>Build]</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>create_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Time when the trigger was created.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">Dict[Trigger<wbr>Github]</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ignored_<wbr>files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>included_<wbr>files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>trigger_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the trigger.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>trigger_<wbr>template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">Dict[Trigger<wbr>Trigger<wbr>Template]</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing Trigger Resource

Get an existing Trigger resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/cloudbuild/#TriggerState">TriggerState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/gcp/cloudbuild/#Trigger">Trigger</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>build=None<span class="p">, </span>create_time=None<span class="p">, </span>description=None<span class="p">, </span>disabled=None<span class="p">, </span>filename=None<span class="p">, </span>github=None<span class="p">, </span>ignored_files=None<span class="p">, </span>included_files=None<span class="p">, </span>name=None<span class="p">, </span>project=None<span class="p">, </span>substitutions=None<span class="p">, </span>trigger_id=None<span class="p">, </span>trigger_template=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetTrigger<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerState">TriggerState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#Trigger">Trigger</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Cloudbuild.Trigger.html">Trigger</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Gcp/Pulumi.Gcp.Cloudbuild.TriggerState.html">TriggerState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Inputs.<wbr>Trigger<wbr>Build<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Create<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Time when the trigger was created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Inputs.<wbr>Trigger<wbr>Github<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ignored<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Included<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>Substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary<string, string>?</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Trigger<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Trigger<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Inputs.<wbr>Trigger<wbr>Trigger<wbr>Template<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">*Trigger<wbr>Build</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Create<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Time when the trigger was created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Description</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">*Trigger<wbr>Github</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ignored<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Included<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>Substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]string</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Trigger<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Trigger<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">*Trigger<wbr>Trigger<wbr>Template</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">Trigger<wbr>Build?</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>create<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Time when the trigger was created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">Trigger<wbr>Github?</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ignored<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>included<wbr>Files</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: string}?</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>trigger<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>trigger<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">Trigger<wbr>Trigger<wbr>Template?</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>build</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuild">Dict[Trigger<wbr>Build]</a></span>
    </dt>
    <dd>{{% md %}}Contents of the build template. Either a filename or build template must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>create_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Time when the trigger was created.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>description</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Human-readable description of the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>disabled</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Whether the trigger is disabled or not. If true, the trigger will never result in a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>filename</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Path, from the source root, to a file whose contents is used for the template. Either a filename or build template must
be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>github</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithub">Dict[Trigger<wbr>Github]</a></span>
    </dt>
    <dd>{{% md %}}Describes the configuration of a trigger that creates a build whenever a GitHub event is received. One of
'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ignored_<wbr>files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If ignoredFiles and changed files are both empty, then they are not used to determine whether or not
to trigger a build. If ignoredFiles is not empty, then we ignore any files that match any of the ignored_file globs. If
the change has no files that are outside of the ignoredFiles globs, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>included_<wbr>files</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}ignoredFiles and includedFiles are file glob matches using https://golang.org/pkg/path/filepath/#Match extended with
support for '**'. If any of the files altered in the commit pass the ignoredFiles filter and includedFiles is empty,
then as far as this filter is concerned, we should trigger the build. If any of the files altered in the commit pass the
ignoredFiles filter and includedFiles is not empty, then we make sure that at least one of those files matches a
includedFiles glob. If not, then we do not trigger a build.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Name of the trigger. Must be unique within the project.
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
        <span>substitutions</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, str]</span>
    </dt>
    <dd>{{% md %}}Substitutions data for Build resource.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>trigger_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The unique identifier for the trigger.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>trigger_<wbr>template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggertriggertemplate">Dict[Trigger<wbr>Trigger<wbr>Template]</a></span>
    </dt>
    <dd>{{% md %}}Template describing the types of source changes to trigger a build. Branch and tag names in trigger templates are
interpreted as regular expressions. Any branch or tag change that matches that regular expression will trigger a build.
One of 'trigger_template' or 'github' must be provided.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Trigger<wbr>Build</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TriggerBuild">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TriggerBuild">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerBuildArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerBuildOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Images</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Steps</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuildstep">List&lt;Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Inputs.<wbr>Trigger<wbr>Build<wbr>Step<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Timeout</span>
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
        <span>Images</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Steps</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuildstep">[]Trigger<wbr>Build<wbr>Step</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Timeout</span>
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
        <span>images</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>steps</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuildstep">Trigger<wbr>Build<wbr>Step[]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>timeout</span>
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
        <span>images</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>steps</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuildstep">List[Trigger<wbr>Build<wbr>Step]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>timeout</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Trigger<wbr>Build<wbr>Step</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TriggerBuildStep">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TriggerBuildStep">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerBuildStepArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerBuildStepOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Args</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dir</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Entrypoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Envs</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}an identifier for the resource with format `projects/{{project}}/triggers/{{trigger_id}}`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Secret<wbr>Envs</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Timeout</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Timing</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Volumes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuildstepvolume">List&lt;Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Inputs.<wbr>Trigger<wbr>Build<wbr>Step<wbr>Volume<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Wait<wbr>Fors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Args</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dir</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Entrypoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Envs</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}an identifier for the resource with format `projects/{{project}}/triggers/{{trigger_id}}`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Secret<wbr>Envs</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Timeout</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Timing</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Volumes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuildstepvolume">[]Trigger<wbr>Build<wbr>Step<wbr>Volume</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Wait<wbr>Fors</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>args</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dir</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>entrypoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>envs</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}an identifier for the resource with format `projects/{{project}}/triggers/{{trigger_id}}`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>secret<wbr>Envs</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>timeout</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>timing</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>volumes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuildstepvolume">Trigger<wbr>Build<wbr>Step<wbr>Volume[]?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>wait<wbr>Fors</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>args</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dir</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>entrypoint</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>envs</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}an identifier for the resource with format `projects/{{project}}/triggers/{{trigger_id}}`
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>secret<wbr>Envs</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>timeout</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>timing</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>volumes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggerbuildstepvolume">List[Trigger<wbr>Build<wbr>Step<wbr>Volume]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>wait<wbr>Fors</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Trigger<wbr>Build<wbr>Step<wbr>Volume</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TriggerBuildStepVolume">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TriggerBuildStepVolume">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerBuildStepVolumeArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerBuildStepVolumeOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Path</span>
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
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Path</span>
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
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>path</span>
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
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>path</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Trigger<wbr>Github</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TriggerGithub">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TriggerGithub">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerGithubArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerGithubOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Owner</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Pull<wbr>Request</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithubpullrequest">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Inputs.<wbr>Trigger<wbr>Github<wbr>Pull<wbr>Request<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Push</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithubpush">Pulumi.<wbr>Gcp.<wbr>Cloud<wbr>Build.<wbr>Inputs.<wbr>Trigger<wbr>Github<wbr>Push<wbr>Args?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Owner</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Pull<wbr>Request</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithubpullrequest">*Trigger<wbr>Github<wbr>Pull<wbr>Request</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Push</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithubpush">*Trigger<wbr>Github<wbr>Push</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>owner</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>pull<wbr>Request</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithubpullrequest">Trigger<wbr>Github<wbr>Pull<wbr>Request?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>push</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithubpush">Trigger<wbr>Github<wbr>Push?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>owner</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>pull<wbr>Request</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithubpullrequest">Dict[Trigger<wbr>Github<wbr>Pull<wbr>Request]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>push</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#triggergithubpush">Dict[Trigger<wbr>Github<wbr>Push]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Trigger<wbr>Github<wbr>Pull<wbr>Request</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TriggerGithubPullRequest">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TriggerGithubPullRequest">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerGithubPullRequestArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerGithubPullRequestOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Branch</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Comment<wbr>Control</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Branch</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Comment<wbr>Control</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>branch</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>comment<wbr>Control</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>branch</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>comment<wbr>Control</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Trigger<wbr>Github<wbr>Push</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TriggerGithubPush">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TriggerGithubPush">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerGithubPushArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerGithubPushOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Branch</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tag</span>
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
        <span>Branch</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tag</span>
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
        <span>branch</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tag</span>
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
        <span>branch</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tag</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Trigger<wbr>Trigger<wbr>Template</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/input/#TriggerTriggerTemplate">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/gcp/types/output/#TriggerTriggerTemplate">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerTriggerTemplateArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-gcp/sdk/go/gcp/cloudbuild?tab=doc#TriggerTriggerTemplateOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Branch<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Commit<wbr>Sha</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dir</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Project<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Repo<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tag<wbr>Name</span>
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
        <span>Branch<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Commit<wbr>Sha</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dir</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Project<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Repo<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tag<wbr>Name</span>
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
        <span>branch<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>commit<wbr>Sha</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dir</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>project<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>repo<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tag<wbr>Name</span>
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
        <span>branch<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>commit<wbr>Sha</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dir</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>project_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>repo<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tag<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}







