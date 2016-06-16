---
layout: post
title:  Requirement definition
root: ../../../
categories: DOCUMENTATION-1.2.0
parent: [devops, tosca_concepts, tosca_ref_definitions]
node_name: tosca_ref_requirement_definition
weight: 500
---

A requirement definition allows specification of a requirement that a node need to fulfill to be instanciated.

## Keynames

{: .table .table-bordered}
| Keyname         | Type                | Required | Description |
|:----------------|:--------------------|:---------|:------------|
| type (Alien 4 Cloud supports also relationship_type) | string | no      | The optional reserved keyname used to provide a named Relationship Type to use when fulfilling the associated named requirement. |
| occurences     | range             | no       | Lower boundary by which a requirement MUST be matched. Valid values are any positive number, 0 meaning that the requirement is optional. Defaults to 1. and Upper boundary by which a requirement MUST be matched for Node Templates. Valid values are any positive number or _unbounded_ string that means that there is no upper limit. Defaults to 1. |

## Grammar

{% highlight yaml %}
# using type
<requirement_name>: <capability_type or node_type>
type: <relationship_type>
occurences: <occurences>

# alien 4 cloud specific support more meaningful
<requirement_name>: <capability_type or node_type>
relationship_type: <relationship_type>
occurences: <occurences>
{% endhighlight %}

## Example

{% highlight yaml %}
node_types:
  fastconnect.nodes.RequirementSample:
  requirements:
    - host: tosca.nodes.Compute
      relationship_type: tosca.relationships.HostedOn
      occurences: [0, unbounded]
{% endhighlight %}