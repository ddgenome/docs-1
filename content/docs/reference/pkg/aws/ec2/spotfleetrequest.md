
---
title: "SpotFleetRequest"
block_external_search_index: true
---

Provides an EC2 Spot Fleet Request resource. This allows a fleet of Spot
instances to be requested on the Spot market.

## Example Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

// Request a Spot fleet
const cheapCompute = new aws.ec2.SpotFleetRequest("cheap_compute", {
    allocationStrategy: "diversified",
    iamFleetRole: "arn:aws:iam::12345678:role/spot-fleet",
    launchSpecifications: [
        {
            ami: "ami-1234",
            iamInstanceProfileArn: aws_iam_instance_profile_example.arn,
            instanceType: "m4.10xlarge",
            placementTenancy: "dedicated",
            spotPrice: "2.793",
        },
        {
            ami: "ami-5678",
            availabilityZone: "us-west-1a",
            iamInstanceProfileArn: aws_iam_instance_profile_example.arn,
            instanceType: "m4.4xlarge",
            keyName: "my-key",
            rootBlockDevices: [{
                volumeSize: 300,
                volumeType: "gp2",
            }],
            spotPrice: "1.117",
            subnetId: "subnet-1234",
            tags: {
                Name: "spot-fleet-example",
            },
            weightedCapacity: "35",
        },
    ],
    spotPrice: "0.03",
    targetCapacity: 6,
    validUntil: "2019-11-04T20:44:20Z",
});
```

> **NOTE:** This provider does not support the functionality where multiple `subnet_id` or `availability_zone` parameters can be specified in the same
launch configuration block. If you want to specify multiple values, then separate launch configuration blocks should be used:

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const foo = new aws.ec2.SpotFleetRequest("foo", {
    iamFleetRole: "arn:aws:iam::12345678:role/spot-fleet",
    launchSpecifications: [
        {
            ami: "ami-d06a90b0",
            availabilityZone: "us-west-2a",
            instanceType: "m1.small",
            keyName: "my-key",
        },
        {
            ami: "ami-d06a90b0",
            availabilityZone: "us-west-2a",
            instanceType: "m5.large",
            keyName: "my-key",
        },
    ],
    spotPrice: "0.005",
    targetCapacity: 2,
    validUntil: "2019-11-04T20:44:20Z",
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-aws/blob/master/website/docs/r/spot_fleet_request.html.markdown.



## Create a SpotFleetRequest Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/ec2/#SpotFleetRequest">SpotFleetRequest</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/ec2/#SpotFleetRequestArgs">SpotFleetRequestArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">SpotFleetRequest</span><span class="p">(resource_name, opts=None, </span>allocation_strategy=None<span class="p">, </span>excess_capacity_termination_policy=None<span class="p">, </span>fleet_type=None<span class="p">, </span>iam_fleet_role=None<span class="p">, </span>instance_interruption_behaviour=None<span class="p">, </span>instance_pools_to_use_count=None<span class="p">, </span>launch_specifications=None<span class="p">, </span>load_balancers=None<span class="p">, </span>replace_unhealthy_instances=None<span class="p">, </span>spot_price=None<span class="p">, </span>target_capacity=None<span class="p">, </span>target_group_arns=None<span class="p">, </span>terminate_instances_with_expiration=None<span class="p">, </span>valid_from=None<span class="p">, </span>valid_until=None<span class="p">, </span>wait_for_fulfillment=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewSpotFleetRequest<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequestArgs">SpotFleetRequestArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequest">SpotFleetRequest</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Ec2.SpotFleetRequest.html">SpotFleetRequest</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Ec2.Inputs.SpotFleetRequestArgs.html">SpotFleetRequestArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Allocation<wbr>Strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Excess<wbr>Capacity<wbr>Termination<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Fleet<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Iam<wbr>Fleet<wbr>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Instance<wbr>Interruption<wbr>Behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Instance<wbr>Pools<wbr>To<wbr>Use<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Launch<wbr>Specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">List&lt;Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Load<wbr>Balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Replace<wbr>Unhealthy<wbr>Instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Target<wbr>Capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Group<wbr>Arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Terminate<wbr>Instances<wbr>With<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Valid<wbr>From</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Valid<wbr>Until</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Wait<wbr>For<wbr>Fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Allocation<wbr>Strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Excess<wbr>Capacity<wbr>Termination<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Fleet<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Iam<wbr>Fleet<wbr>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Instance<wbr>Interruption<wbr>Behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Instance<wbr>Pools<wbr>To<wbr>Use<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Launch<wbr>Specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">[]Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Load<wbr>Balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Replace<wbr>Unhealthy<wbr>Instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Target<wbr>Capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Group<wbr>Arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Terminate<wbr>Instances<wbr>With<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Valid<wbr>From</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Valid<wbr>Until</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Wait<wbr>For<wbr>Fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allocation<wbr>Strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>excess<wbr>Capacity<wbr>Termination<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>fleet<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>iam<wbr>Fleet<wbr>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>instance<wbr>Interruption<wbr>Behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>instance<wbr>Pools<wbr>To<wbr>Use<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>launch<wbr>Specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification[]</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>load<wbr>Balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>replace<wbr>Unhealthy<wbr>Instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>target<wbr>Capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Group<wbr>Arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>terminate<wbr>Instances<wbr>With<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>valid<wbr>From</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>valid<wbr>Until</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>wait<wbr>For<wbr>Fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allocation_<wbr>strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>excess_<wbr>capacity_<wbr>termination_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>fleet_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>iam_<wbr>fleet_<wbr>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>instance_<wbr>interruption_<wbr>behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>instance_<wbr>pools_<wbr>to_<wbr>use_<wbr>count</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>launch_<wbr>specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">List[Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification]</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>load_<wbr>balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>replace_<wbr>unhealthy_<wbr>instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>spot_<wbr>price</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>target_<wbr>capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>group_<wbr>arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>terminate_<wbr>instances_<wbr>with_<wbr>expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>valid_<wbr>from</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>valid_<wbr>until</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>wait_<wbr>for_<wbr>fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## SpotFleetRequest Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Allocation<wbr>Strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Client<wbr>Token</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Excess<wbr>Capacity<wbr>Termination<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Fleet<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Iam<wbr>Fleet<wbr>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Instance<wbr>Interruption<wbr>Behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Instance<wbr>Pools<wbr>To<wbr>Use<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Launch<wbr>Specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">List&lt;Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification&gt;</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Load<wbr>Balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Replace<wbr>Unhealthy<wbr>Instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Spot<wbr>Request<wbr>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The state of the Spot fleet request.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target<wbr>Capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target<wbr>Group<wbr>Arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Terminate<wbr>Instances<wbr>With<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Valid<wbr>From</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Valid<wbr>Until</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Wait<wbr>For<wbr>Fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Allocation<wbr>Strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Client<wbr>Token</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Excess<wbr>Capacity<wbr>Termination<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Fleet<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Iam<wbr>Fleet<wbr>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Instance<wbr>Interruption<wbr>Behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Instance<wbr>Pools<wbr>To<wbr>Use<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Launch<wbr>Specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">[]Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Load<wbr>Balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Replace<wbr>Unhealthy<wbr>Instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Spot<wbr>Request<wbr>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The state of the Spot fleet request.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target<wbr>Capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Target<wbr>Group<wbr>Arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Terminate<wbr>Instances<wbr>With<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Valid<wbr>From</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Valid<wbr>Until</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Wait<wbr>For<wbr>Fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>allocation<wbr>Strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>client<wbr>Token</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>excess<wbr>Capacity<wbr>Termination<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>fleet<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>iam<wbr>Fleet<wbr>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>instance<wbr>Interruption<wbr>Behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>instance<wbr>Pools<wbr>To<wbr>Use<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>launch<wbr>Specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification[]</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>load<wbr>Balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>replace<wbr>Unhealthy<wbr>Instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>spot<wbr>Request<wbr>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The state of the Spot fleet request.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target<wbr>Capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target<wbr>Group<wbr>Arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>terminate<wbr>Instances<wbr>With<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>valid<wbr>From</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>valid<wbr>Until</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>wait<wbr>For<wbr>Fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>allocation_<wbr>strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>client_<wbr>token</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>excess_<wbr>capacity_<wbr>termination_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>fleet_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>iam_<wbr>fleet_<wbr>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>instance_<wbr>interruption_<wbr>behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>instance_<wbr>pools_<wbr>to_<wbr>use_<wbr>count</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>launch_<wbr>specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">List[Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification]</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>load_<wbr>balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>replace_<wbr>unhealthy_<wbr>instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>spot_<wbr>price</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>spot_<wbr>request_<wbr>state</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The state of the Spot fleet request.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target_<wbr>capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>target_<wbr>group_<wbr>arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>terminate_<wbr>instances_<wbr>with_<wbr>expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>valid_<wbr>from</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>valid_<wbr>until</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>wait_<wbr>for_<wbr>fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing SpotFleetRequest Resource

Get an existing SpotFleetRequest resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">pulumi.Input&lt;pulumi.ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/ec2/#SpotFleetRequestState">SpotFleetRequestState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/ec2/#SpotFleetRequest">SpotFleetRequest</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>allocation_strategy=None<span class="p">, </span>client_token=None<span class="p">, </span>excess_capacity_termination_policy=None<span class="p">, </span>fleet_type=None<span class="p">, </span>iam_fleet_role=None<span class="p">, </span>instance_interruption_behaviour=None<span class="p">, </span>instance_pools_to_use_count=None<span class="p">, </span>launch_specifications=None<span class="p">, </span>load_balancers=None<span class="p">, </span>replace_unhealthy_instances=None<span class="p">, </span>spot_price=None<span class="p">, </span>spot_request_state=None<span class="p">, </span>target_capacity=None<span class="p">, </span>target_group_arns=None<span class="p">, </span>terminate_instances_with_expiration=None<span class="p">, </span>valid_from=None<span class="p">, </span>valid_until=None<span class="p">, </span>wait_for_fulfillment=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetSpotFleetRequest<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">pulumi.IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequestState">SpotFleetRequestState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequest">SpotFleetRequest</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Ec2.SpotFleetRequest.html">SpotFleetRequest</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Pulumi.Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Ec2.SpotFleetRequestState.html">SpotFleetRequestState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">Pulumi.CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Allocation<wbr>Strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Client<wbr>Token</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Excess<wbr>Capacity<wbr>Termination<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Fleet<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iam<wbr>Fleet<wbr>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Instance<wbr>Interruption<wbr>Behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Instance<wbr>Pools<wbr>To<wbr>Use<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Launch<wbr>Specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">List&lt;Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Load<wbr>Balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Replace<wbr>Unhealthy<wbr>Instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Spot<wbr>Request<wbr>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The state of the Spot fleet request.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Group<wbr>Arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Terminate<wbr>Instances<wbr>With<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Valid<wbr>From</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Valid<wbr>Until</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Wait<wbr>For<wbr>Fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Allocation<wbr>Strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Client<wbr>Token</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Excess<wbr>Capacity<wbr>Termination<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Fleet<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iam<wbr>Fleet<wbr>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Instance<wbr>Interruption<wbr>Behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Instance<wbr>Pools<wbr>To<wbr>Use<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Launch<wbr>Specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">[]Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Load<wbr>Balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Replace<wbr>Unhealthy<wbr>Instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Spot<wbr>Request<wbr>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The state of the Spot fleet request.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Group<wbr>Arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Terminate<wbr>Instances<wbr>With<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Valid<wbr>From</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Valid<wbr>Until</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Wait<wbr>For<wbr>Fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allocation<wbr>Strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>client<wbr>Token</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>excess<wbr>Capacity<wbr>Termination<wbr>Policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>fleet<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iam<wbr>Fleet<wbr>Role</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>instance<wbr>Interruption<wbr>Behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>instance<wbr>Pools<wbr>To<wbr>Use<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>launch<wbr>Specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification[]?</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>load<wbr>Balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>replace<wbr>Unhealthy<wbr>Instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>spot<wbr>Request<wbr>State</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The state of the Spot fleet request.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Group<wbr>Arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>terminate<wbr>Instances<wbr>With<wbr>Expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>valid<wbr>From</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>valid<wbr>Until</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>wait<wbr>For<wbr>Fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allocation_<wbr>strategy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates how to allocate the target capacity across
the Spot pools specified by the Spot fleet request. The default is
`lowestPrice`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>client_<wbr>token</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>excess_<wbr>capacity_<wbr>termination_<wbr>policy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated if the target capacity of the Spot fleet
request is decreased below the current size of the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>fleet_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The type of fleet request. Indicates whether the Spot Fleet only requests the target
capacity or also attempts to maintain it. Default is `maintain`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iam_<wbr>fleet_<wbr>role</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Grants the Spot fleet permission to terminate
Spot instances on your behalf when you cancel its Spot fleet request using
CancelSpotFleetRequests or when the Spot fleet request expires, if you set
terminateInstancesWithExpiration.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>instance_<wbr>interruption_<wbr>behaviour</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Indicates whether a Spot
instance stops or terminates when it is interrupted. Default is
`terminate`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>instance_<wbr>pools_<wbr>to_<wbr>use_<wbr>count</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}
The number of Spot pools across which to allocate your target Spot capacity.
Valid only when `allocation_strategy` is set to `lowestPrice`. Spot Fleet selects
the cheapest Spot pools and evenly allocates your target Spot capacity across
the number of Spot pools that you specify.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>launch_<wbr>specifications</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecification">List[Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification]</a></span>
    </dt>
    <dd>{{% md %}}Used to define the launch configuration of the
spot-fleet request. Can be specified multiple times to define different bids
across different markets and instance types.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>load_<wbr>balancers</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of elastic load balancer names to add to the Spot fleet.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>replace_<wbr>unhealthy_<wbr>instances</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether Spot fleet should replace unhealthy instances. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>spot_<wbr>price</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>spot_<wbr>request_<wbr>state</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The state of the Spot fleet request.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of units to request. You can choose to set the
target capacity in terms of instances or a performance characteristic that is
important to your application workload, such as vCPUs, memory, or I/O.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>group_<wbr>arns</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}A list of `aws.alb.TargetGroup` ARNs, for use with Application Load Balancing.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>terminate_<wbr>instances_<wbr>with_<wbr>expiration</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Indicates whether running Spot
instances should be terminated when the Spot fleet request expires.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>valid_<wbr>from</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The start date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). The default is to start fulfilling the request immediately.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>valid_<wbr>until</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The end date and time of the request, in UTC [RFC3339](https://tools.ietf.org/html/rfc3339#section-5.8) format(for example, YYYY-MM-DDTHH:MM:SSZ). At this point, no new Spot instance requests are placed or enabled to fulfill the request. Defaults to 24 hours.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>wait_<wbr>for_<wbr>fulfillment</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If set, this provider will
wait for the Spot Request to be fulfilled, and will throw an error if the
timeout of 10m is reached.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#SpotFleetRequestLaunchSpecification">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#SpotFleetRequestLaunchSpecification">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequestLaunchSpecificationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequestLaunchSpecificationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Ami</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Associate<wbr>Public<wbr>Ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ebs<wbr>Block<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationebsblockdevice">List&lt;Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Ebs<wbr>Block<wbr>Device<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ebs<wbr>Optimized</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ephemeral<wbr>Block<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationephemeralblockdevice">List&lt;Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Ephemeral<wbr>Block<wbr>Device<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iam<wbr>Instance<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iam<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Instance<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Monitoring</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Placement<wbr>Group</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Placement<wbr>Tenancy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Root<wbr>Block<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationrootblockdevice">List&lt;Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Root<wbr>Block<wbr>Device<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
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
        <span>User<wbr>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpc<wbr>Security<wbr>Group<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Weighted<wbr>Capacity</span>
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
        <span>Ami</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Associate<wbr>Public<wbr>Ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ebs<wbr>Block<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationebsblockdevice">[]Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Ebs<wbr>Block<wbr>Device</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ebs<wbr>Optimized</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ephemeral<wbr>Block<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationephemeralblockdevice">[]Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Ephemeral<wbr>Block<wbr>Device</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iam<wbr>Instance<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iam<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Instance<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Monitoring</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Placement<wbr>Group</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Placement<wbr>Tenancy</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Root<wbr>Block<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationrootblockdevice">[]Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Root<wbr>Block<wbr>Device</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
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
        <span>User<wbr>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Vpc<wbr>Security<wbr>Group<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Weighted<wbr>Capacity</span>
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
        <span>ami</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>associate<wbr>Public<wbr>Ip<wbr>Address</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>availability<wbr>Zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ebs<wbr>Block<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationebsblockdevice">Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Ebs<wbr>Block<wbr>Device[]?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ebs<wbr>Optimized</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ephemeral<wbr>Block<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationephemeralblockdevice">Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Ephemeral<wbr>Block<wbr>Device[]?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iam<wbr>Instance<wbr>Profile</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iam<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>instance<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>key<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>monitoring</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>placement<wbr>Group</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>placement<wbr>Tenancy</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>root<wbr>Block<wbr>Devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationrootblockdevice">Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Root<wbr>Block<wbr>Device[]?</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>spot<wbr>Price</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subnet<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
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
        <span>user<wbr>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpc<wbr>Security<wbr>Group<wbr>Ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>weighted<wbr>Capacity</span>
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
        <span>ami</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>associate_<wbr>public_<wbr>ip_<wbr>address</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>availability_<wbr>zone</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ebs_<wbr>block_<wbr>devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationebsblockdevice">List[Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Ebs<wbr>Block<wbr>Device]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ebs_<wbr>optimized</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ephemeral_<wbr>block_<wbr>devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationephemeralblockdevice">List[Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Ephemeral<wbr>Block<wbr>Device]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iam_<wbr>instance_<wbr>profile</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iam<wbr>Instance<wbr>Profile<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>instance_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>key_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>monitoring</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>placement_<wbr>group</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>placement_<wbr>tenancy</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>root_<wbr>block_<wbr>devices</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#spotfleetrequestlaunchspecificationrootblockdevice">List[Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Root<wbr>Block<wbr>Device]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>spot_<wbr>price</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The maximum bid price per unit hour.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subnet_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
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
        <span>user_<wbr>data</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>vpc_<wbr>security_<wbr>group_<wbr>ids</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>weighted<wbr>Capacity</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Ebs<wbr>Block<wbr>Device</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#SpotFleetRequestLaunchSpecificationEbsBlockDevice">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#SpotFleetRequestLaunchSpecificationEbsBlockDevice">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequestLaunchSpecificationEbsBlockDeviceArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequestLaunchSpecificationEbsBlockDeviceOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Encrypted</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iops</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Volume<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Volume<wbr>Type</span>
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
        <span>Delete<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Encrypted</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iops</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Volume<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Volume<wbr>Type</span>
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
        <span>delete<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>encrypted</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iops</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>snapshot<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>volume<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>volume<wbr>Type</span>
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
        <span>delete<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>device_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>encrypted</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iops</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>key_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>snapshot_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>volume_<wbr>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>volume<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Ephemeral<wbr>Block<wbr>Device</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#SpotFleetRequestLaunchSpecificationEphemeralBlockDevice">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#SpotFleetRequestLaunchSpecificationEphemeralBlockDevice">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequestLaunchSpecificationEphemeralBlockDeviceArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequestLaunchSpecificationEphemeralBlockDeviceOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Virtual<wbr>Name</span>
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
        <span>Device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Virtual<wbr>Name</span>
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
        <span>device<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>virtual<wbr>Name</span>
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
        <span>device_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>virtual<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Spot<wbr>Fleet<wbr>Request<wbr>Launch<wbr>Specification<wbr>Root<wbr>Block<wbr>Device</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#SpotFleetRequestLaunchSpecificationRootBlockDevice">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#SpotFleetRequestLaunchSpecificationRootBlockDevice">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequestLaunchSpecificationRootBlockDeviceArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/go/aws/ec2?tab=doc#SpotFleetRequestLaunchSpecificationRootBlockDeviceOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Delete<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Encrypted</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iops</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Volume<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Volume<wbr>Type</span>
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
        <span>Delete<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Encrypted</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Iops</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Volume<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Volume<wbr>Type</span>
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
        <span>delete<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>encrypted</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iops</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>volume<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>volume<wbr>Type</span>
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
        <span>delete<wbr>On<wbr>Termination</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>encrypted</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>iops</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>key_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>volume_<wbr>size</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>volume<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}







