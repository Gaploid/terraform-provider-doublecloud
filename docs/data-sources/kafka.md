---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "doublecloud_kafka Data Source - terraform-provider-doublecloud"
subcategory: ""
description: |-
  Kafka data source
---

# doublecloud_kafka (Data Source)

Kafka data source



<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `project_id` (String) Project identifier

### Optional

- `cloud_type` (String) Cloud type (aws, gcp, azure)
- `connection_info` (Attributes) (see [below for nested schema](#nestedatt--connection_info))
- `description` (String) Description of cluster
- `id` (String) Cluster identifier
- `name` (String) Name of cluster
- `private_connection_info` (Attributes) (see [below for nested schema](#nestedatt--private_connection_info))
- `region_id` (String) Region of cluster
- `version` (String) Version of ClickHouse DBMS

<a id="nestedatt--connection_info"></a>
### Nested Schema for `connection_info`

Optional:

- `connection_string` (String) String to use in clients
- `password` (String) Password for Apache Kafka® user
- `user` (String) Apache Kafka® user


<a id="nestedatt--private_connection_info"></a>
### Nested Schema for `private_connection_info`

Optional:

- `connection_string` (String) String to use in clients
- `password` (String) Password for Apache Kafka® user
- `user` (String) Apache Kafka® user

