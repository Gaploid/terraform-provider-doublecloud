---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "doublecloud_transfer_endpoint Resource - terraform-provider-doublecloud"
subcategory: ""
description: |-
  Transfer endpoint resource
---

# doublecloud_transfer_endpoint (Resource)

Transfer endpoint resource

## Example Usage

```terraform
resource "doublecloud_transfer_endpoint" "sample-pg2ch-source" {
  name = "sample-pg2ch-source"
  project_id = var.project_id
  settings {
    postgres_source {
      connection {
        on_premise {
          hosts = [
            "mypostgresql.host"
          ]
          port = 5432
        }
      }
      database = "postgres"
      user = "postgres"
      password = var.postgresql_postgres_password
    }
  }
}

resource "doublecloud_transfer_endpoint" "sample-pg2ch-target" {
  name = "sample-pg2ch-target"
  project_id = var.project_id
  settings {
    clickhouse_target {
      clickhouse_cleanup_policy = "DROP"
      connection {
        address {
            cluster_id = "chcexampleexampleexa"
        }
        database = "default"
        password = var.clickhouse_admin_password
        user = "admin"
      }
    }
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Name of endpoint
- `project_id` (String) Project identifier

### Optional

- `description` (String) Description of endpoint
- `settings` (Block, Optional) Settings (see [below for nested schema](#nestedblock--settings))

### Read-Only

- `id` (String) Transfer endpoint id

<a id="nestedblock--settings"></a>
### Nested Schema for `settings`

Optional:

- `aws_cloudtrail_source` (Block, Optional) (see [below for nested schema](#nestedblock--settings--aws_cloudtrail_source))
- `clickhouse_source` (Block, Optional) (see [below for nested schema](#nestedblock--settings--clickhouse_source))
- `clickhouse_target` (Block, Optional) (see [below for nested schema](#nestedblock--settings--clickhouse_target))
- `facebookmarketing_source` (Block, Optional) (see [below for nested schema](#nestedblock--settings--facebookmarketing_source))
- `googleads_source` (Block, Optional) (see [below for nested schema](#nestedblock--settings--googleads_source))
- `kafka_source` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source))
- `kafka_target` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_target))
- `linkedinads_source` (Block, Optional) (see [below for nested schema](#nestedblock--settings--linkedinads_source))
- `mongo_source` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mongo_source))
- `mongo_target` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mongo_target))
- `mysql_source` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mysql_source))
- `mysql_target` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mysql_target))
- `postgres_source` (Block, Optional) (see [below for nested schema](#nestedblock--settings--postgres_source))
- `postgres_target` (Block, Optional) (see [below for nested schema](#nestedblock--settings--postgres_target))
- `s3_source` (Block, Optional) (see [below for nested schema](#nestedblock--settings--s3_source))

<a id="nestedblock--settings--aws_cloudtrail_source"></a>
### Nested Schema for `settings.aws_cloudtrail_source`

Optional:

- `key_id` (String, Sensitive) AWS CloudTrail Access Key ID. See [documentation](https://docs.airbyte.io/integrations/sources/aws-cloudtrail) for information on how to obtain this value.
- `region_name` (String) The default AWS region; for example, `us-west-1`.
- `secret_key` (String, Sensitive) AWS CloudTrail Secret Key. See [documentation](https://docs.airbyte.io/integrations/sources/aws-cloudtrail) for information on how to obtain this value.
- `start_date` (String) The date from which replication should start. Note that in AWS CloudTrail, historical data are available for the last 90 days only. Format `YYYY-MM-DD`; for example, `2021-01-25`.


<a id="nestedblock--settings--clickhouse_source"></a>
### Nested Schema for `settings.clickhouse_source`

Optional:

- `connection` (Block, Optional) (see [below for nested schema](#nestedblock--settings--clickhouse_source--connection))
- `exclude_tables` (List of String)
- `include_tables` (List of String)

<a id="nestedblock--settings--clickhouse_source--connection"></a>
### Nested Schema for `settings.clickhouse_source.connection`

Optional:

- `address` (Block, Optional) (see [below for nested schema](#nestedblock--settings--clickhouse_source--connection--address))
- `database` (String)
- `password` (String, Sensitive)
- `user` (String)

<a id="nestedblock--settings--clickhouse_source--connection--address"></a>
### Nested Schema for `settings.clickhouse_source.connection.address`

Optional:

- `cluster_id` (String)
- `on_premise` (Block, Optional) (see [below for nested schema](#nestedblock--settings--clickhouse_source--connection--address--on_premise))

<a id="nestedblock--settings--clickhouse_source--connection--address--on_premise"></a>
### Nested Schema for `settings.clickhouse_source.connection.address.on_premise`

Optional:

- `http_port` (Number)
- `native_port` (Number)
- `shard` (Block List) (see [below for nested schema](#nestedblock--settings--clickhouse_source--connection--address--on_premise--shard))
- `tls_mode` (Block, Optional) (see [below for nested schema](#nestedblock--settings--clickhouse_source--connection--address--on_premise--tls_mode))

<a id="nestedblock--settings--clickhouse_source--connection--address--on_premise--shard"></a>
### Nested Schema for `settings.clickhouse_source.connection.address.on_premise.shard`

Optional:

- `hosts` (List of String)
- `name` (String)


<a id="nestedblock--settings--clickhouse_source--connection--address--on_premise--tls_mode"></a>
### Nested Schema for `settings.clickhouse_source.connection.address.on_premise.tls_mode`

Optional:

- `ca_certificate` (String) X.509 certificate of the certificate authority which issued the server's certificate, in PEM format. When CA certificate is specified TLS is used to connect to the server






<a id="nestedblock--settings--clickhouse_target"></a>
### Nested Schema for `settings.clickhouse_target`

Optional:

- `alt_name` (Block List) (see [below for nested schema](#nestedblock--settings--clickhouse_target--alt_name))
- `clickhouse_cleanup_policy` (String)
- `clickhouse_cluster_name` (String) clickhouse_cluster_name
- `connection` (Block, Optional) (see [below for nested schema](#nestedblock--settings--clickhouse_target--connection))

<a id="nestedblock--settings--clickhouse_target--alt_name"></a>
### Nested Schema for `settings.clickhouse_target.alt_name`

Optional:

- `from_name` (String)
- `to_name` (String)


<a id="nestedblock--settings--clickhouse_target--connection"></a>
### Nested Schema for `settings.clickhouse_target.connection`

Optional:

- `address` (Block, Optional) (see [below for nested schema](#nestedblock--settings--clickhouse_target--connection--address))
- `database` (String)
- `password` (String, Sensitive)
- `user` (String)

<a id="nestedblock--settings--clickhouse_target--connection--address"></a>
### Nested Schema for `settings.clickhouse_target.connection.address`

Optional:

- `cluster_id` (String)
- `on_premise` (Block, Optional) (see [below for nested schema](#nestedblock--settings--clickhouse_target--connection--address--on_premise))

<a id="nestedblock--settings--clickhouse_target--connection--address--on_premise"></a>
### Nested Schema for `settings.clickhouse_target.connection.address.on_premise`

Optional:

- `http_port` (Number)
- `native_port` (Number)
- `shard` (Block List) (see [below for nested schema](#nestedblock--settings--clickhouse_target--connection--address--on_premise--shard))
- `tls_mode` (Block, Optional) (see [below for nested schema](#nestedblock--settings--clickhouse_target--connection--address--on_premise--tls_mode))

<a id="nestedblock--settings--clickhouse_target--connection--address--on_premise--shard"></a>
### Nested Schema for `settings.clickhouse_target.connection.address.on_premise.shard`

Optional:

- `hosts` (List of String)
- `name` (String)


<a id="nestedblock--settings--clickhouse_target--connection--address--on_premise--tls_mode"></a>
### Nested Schema for `settings.clickhouse_target.connection.address.on_premise.tls_mode`

Optional:

- `ca_certificate` (String) X.509 certificate of the certificate authority which issued the server's certificate, in PEM format. When CA certificate is specified TLS is used to connect to the server






<a id="nestedblock--settings--facebookmarketing_source"></a>
### Nested Schema for `settings.facebookmarketing_source`

Optional:

- `access_token` (String, Sensitive) The value of the access token. See  [documentation](https://docs.airbyte.io/integrations/sources/facebook-marketing) for more information on the meaning of this token and how to obtain it
- `account_id` (String) The Facebook Ad account ID to use when pulling data from the Facebook Marketing API. Example: `111111111111111`
- `custom_insights` (Attributes List) Insights. Each entry must have a name and can contains `fields`, `breakdowns`, or `action_breakdowns` (see [below for nested schema](#nestedatt--settings--facebookmarketing_source--custom_insights))
- `end_date` (String) The date until which you'd like to replicate data for all incremental streams, in the format `YYYY-MM-DDT00:00:00Z`. All data generated between `start_date` and this date will be replicated. Not setting this option will result in always syncing the latest data. Example: `2017-01-25T23:59:59Z`
- `fetch_thumbnail_images` (Boolean) In each Ad Creative, fetch the `thumbnail_url` and store the result in `thumbnail_data_url`
- `include_deleted` (Boolean) Include data from deleted Campaigns, Ads, and AdSets
- `start_date` (String) The date from which to replicate data for all incremental streams, in the format `YYYY-MM-DDT00:00:00Z`. All data generated after this date and before `end_date` (if set) will be replicated. Example: `2017-01-25T00:00:00Z`

<a id="nestedatt--settings--facebookmarketing_source--custom_insights"></a>
### Nested Schema for `settings.facebookmarketing_source.custom_insights`

Optional:

- `action_breakdowns` (List of String) `action_breakdowns` request parameter
- `breakdowns` (List of String) `breakdowns` request parameter
- `fields` (List of String) `fields` request parameter
- `name` (String) The name of the insight



<a id="nestedblock--settings--googleads_source"></a>
### Nested Schema for `settings.googleads_source`

Optional:

- `conversion_window_days` (Number)
- `credentials` (Block, Optional) (see [below for nested schema](#nestedblock--settings--googleads_source--credentials))
- `custom_queries` (Attributes List) (see [below for nested schema](#nestedatt--settings--googleads_source--custom_queries))
- `customer_id` (String)
- `end_date` (String)
- `login_customer_id` (String)
- `start_date` (String)

<a id="nestedblock--settings--googleads_source--credentials"></a>
### Nested Schema for `settings.googleads_source.credentials`

Optional:

- `access_token` (String)
- `client_id` (String)
- `client_secret` (String)
- `developer_token` (String)
- `refresh_token` (String)


<a id="nestedatt--settings--googleads_source--custom_queries"></a>
### Nested Schema for `settings.googleads_source.custom_queries`

Optional:

- `query` (String)
- `table_name` (String)



<a id="nestedblock--settings--kafka_source"></a>
### Nested Schema for `settings.kafka_source`

Optional:

- `auth` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--auth))
- `connection` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--connection))
- `parser` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--parser))
- `topic_name` (String) Full source topic name

<a id="nestedblock--settings--kafka_source--auth"></a>
### Nested Schema for `settings.kafka_source.auth`

Optional:

- `no_auth` (Block, Optional) No authentication (see [below for nested schema](#nestedblock--settings--kafka_source--auth--no_auth))
- `sasl` (Block, Optional) Authentication with SASL (see [below for nested schema](#nestedblock--settings--kafka_source--auth--sasl))

<a id="nestedblock--settings--kafka_source--auth--no_auth"></a>
### Nested Schema for `settings.kafka_source.auth.no_auth`


<a id="nestedblock--settings--kafka_source--auth--sasl"></a>
### Nested Schema for `settings.kafka_source.auth.sasl`

Optional:

- `mechanism` (String)
- `password` (String, Sensitive)
- `user` (String)



<a id="nestedblock--settings--kafka_source--connection"></a>
### Nested Schema for `settings.kafka_source.connection`

Optional:

- `cluster_id` (String)
- `on_premise` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--connection--on_premise))

<a id="nestedblock--settings--kafka_source--connection--on_premise"></a>
### Nested Schema for `settings.kafka_source.connection.on_premise`

Optional:

- `broker_urls` (List of String) Kafka broker URLs
- `tls_mode` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--connection--on_premise--tls_mode))

<a id="nestedblock--settings--kafka_source--connection--on_premise--tls_mode"></a>
### Nested Schema for `settings.kafka_source.connection.on_premise.tls_mode`

Optional:

- `ca_certificate` (String) X.509 certificate of the certificate authority which issued the server's certificate, in PEM format. When CA certificate is specified TLS is used to connect to the server




<a id="nestedblock--settings--kafka_source--parser"></a>
### Nested Schema for `settings.kafka_source.parser`

Optional:

- `json` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--parser--json))
- `tskv` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--parser--tskv))

<a id="nestedblock--settings--kafka_source--parser--json"></a>
### Nested Schema for `settings.kafka_source.parser.json`

Optional:

- `add_rest_column` (Boolean)
- `null_keys_allowed` (Boolean)
- `schema` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--parser--json--schema))

<a id="nestedblock--settings--kafka_source--parser--json--schema"></a>
### Nested Schema for `settings.kafka_source.parser.json.schema`

Optional:

- `fields` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--parser--json--schema--fields))
- `json` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--parser--json--schema--json))

<a id="nestedblock--settings--kafka_source--parser--json--schema--fields"></a>
### Nested Schema for `settings.kafka_source.parser.json.schema.fields`

Optional:

- `field` (Block List) (see [below for nested schema](#nestedblock--settings--kafka_source--parser--json--schema--fields--field))

<a id="nestedblock--settings--kafka_source--parser--json--schema--fields--field"></a>
### Nested Schema for `settings.kafka_source.parser.json.schema.fields.field`

Optional:

- `key` (Boolean)
- `name` (String)
- `path` (String)
- `required` (Boolean)
- `type` (String)



<a id="nestedblock--settings--kafka_source--parser--json--schema--json"></a>
### Nested Schema for `settings.kafka_source.parser.json.schema.json`

Optional:

- `fields` (String)




<a id="nestedblock--settings--kafka_source--parser--tskv"></a>
### Nested Schema for `settings.kafka_source.parser.tskv`

Optional:

- `add_rest_column` (Boolean)
- `null_keys_allowed` (Boolean)
- `schema` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--parser--tskv--schema))

<a id="nestedblock--settings--kafka_source--parser--tskv--schema"></a>
### Nested Schema for `settings.kafka_source.parser.tskv.schema`

Optional:

- `fields` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--parser--tskv--schema--fields))
- `json` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_source--parser--tskv--schema--json))

<a id="nestedblock--settings--kafka_source--parser--tskv--schema--fields"></a>
### Nested Schema for `settings.kafka_source.parser.tskv.schema.fields`

Optional:

- `field` (Block List) (see [below for nested schema](#nestedblock--settings--kafka_source--parser--tskv--schema--fields--field))

<a id="nestedblock--settings--kafka_source--parser--tskv--schema--fields--field"></a>
### Nested Schema for `settings.kafka_source.parser.tskv.schema.fields.field`

Optional:

- `key` (Boolean)
- `name` (String)
- `path` (String)
- `required` (Boolean)
- `type` (String)



<a id="nestedblock--settings--kafka_source--parser--tskv--schema--json"></a>
### Nested Schema for `settings.kafka_source.parser.tskv.schema.json`

Optional:

- `fields` (String)






<a id="nestedblock--settings--kafka_target"></a>
### Nested Schema for `settings.kafka_target`

Optional:

- `auth` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_target--auth))
- `connection` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_target--connection))
- `serializer` (Block, Optional) Data serialization format (see [below for nested schema](#nestedblock--settings--kafka_target--serializer))
- `topic_settings` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_target--topic_settings))

<a id="nestedblock--settings--kafka_target--auth"></a>
### Nested Schema for `settings.kafka_target.auth`

Optional:

- `no_auth` (Block, Optional) No authentication (see [below for nested schema](#nestedblock--settings--kafka_target--auth--no_auth))
- `sasl` (Block, Optional) Authentication with SASL (see [below for nested schema](#nestedblock--settings--kafka_target--auth--sasl))

<a id="nestedblock--settings--kafka_target--auth--no_auth"></a>
### Nested Schema for `settings.kafka_target.auth.no_auth`


<a id="nestedblock--settings--kafka_target--auth--sasl"></a>
### Nested Schema for `settings.kafka_target.auth.sasl`

Optional:

- `mechanism` (String)
- `password` (String, Sensitive)
- `user` (String)



<a id="nestedblock--settings--kafka_target--connection"></a>
### Nested Schema for `settings.kafka_target.connection`

Optional:

- `cluster_id` (String)
- `on_premise` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_target--connection--on_premise))

<a id="nestedblock--settings--kafka_target--connection--on_premise"></a>
### Nested Schema for `settings.kafka_target.connection.on_premise`

Optional:

- `broker_urls` (List of String) Kafka broker URLs
- `tls_mode` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_target--connection--on_premise--tls_mode))

<a id="nestedblock--settings--kafka_target--connection--on_premise--tls_mode"></a>
### Nested Schema for `settings.kafka_target.connection.on_premise.tls_mode`

Optional:

- `ca_certificate` (String) X.509 certificate of the certificate authority which issued the server's certificate, in PEM format. When CA certificate is specified TLS is used to connect to the server




<a id="nestedblock--settings--kafka_target--serializer"></a>
### Nested Schema for `settings.kafka_target.serializer`

Optional:

- `auto` (Block, Optional) Select the serialization format automatically (see [below for nested schema](#nestedblock--settings--kafka_target--serializer--auto))
- `debezium` (Block, Optional) Serialize data in json format (see [below for nested schema](#nestedblock--settings--kafka_target--serializer--debezium))
- `json` (Block, Optional) Serialize data in json format (see [below for nested schema](#nestedblock--settings--kafka_target--serializer--json))

<a id="nestedblock--settings--kafka_target--serializer--auto"></a>
### Nested Schema for `settings.kafka_target.serializer.auto`


<a id="nestedblock--settings--kafka_target--serializer--debezium"></a>
### Nested Schema for `settings.kafka_target.serializer.debezium`

Optional:

- `parameter` (Block List) (see [below for nested schema](#nestedblock--settings--kafka_target--serializer--debezium--parameter))

<a id="nestedblock--settings--kafka_target--serializer--debezium--parameter"></a>
### Nested Schema for `settings.kafka_target.serializer.debezium.parameter`

Optional:

- `key` (String)
- `value` (String)



<a id="nestedblock--settings--kafka_target--serializer--json"></a>
### Nested Schema for `settings.kafka_target.serializer.json`



<a id="nestedblock--settings--kafka_target--topic_settings"></a>
### Nested Schema for `settings.kafka_target.topic_settings`

Optional:

- `topic` (Block, Optional) (see [below for nested schema](#nestedblock--settings--kafka_target--topic_settings--topic))
- `topic_prefix` (String) Analogue of the Debezium setting database.server.name. Messages will be sent to topic with name <topic_prefix>.<schema>.<table_name>.

<a id="nestedblock--settings--kafka_target--topic_settings--topic"></a>
### Nested Schema for `settings.kafka_target.topic_settings.topic`

Optional:

- `save_tx_order` (Boolean) Save transactions order. Not to split events queue into separate per-table queues.
- `topic_name` (String) Topic name




<a id="nestedblock--settings--linkedinads_source"></a>
### Nested Schema for `settings.linkedinads_source`

Optional:

- `account_ids` (List of Number) Account IDs separated by space, to pull the data from. Leave empty, if you want to pull the data from all associated accounts
- `credentials` (Block, Optional) Authentication method (see [below for nested schema](#nestedblock--settings--linkedinads_source--credentials))
- `start_date` (String) UTC date in the format YYYY-MM-DD. Any data before this date will not be replicated. Example: 2021-05-17

<a id="nestedblock--settings--linkedinads_source--credentials"></a>
### Nested Schema for `settings.linkedinads_source.credentials`

Optional:

- `access_token` (Block, Optional) (see [below for nested schema](#nestedblock--settings--linkedinads_source--credentials--access_token))
- `oauth` (Block, Optional) (see [below for nested schema](#nestedblock--settings--linkedinads_source--credentials--oauth))

<a id="nestedblock--settings--linkedinads_source--credentials--access_token"></a>
### Nested Schema for `settings.linkedinads_source.credentials.access_token`

Optional:

- `access_token` (String, Sensitive)


<a id="nestedblock--settings--linkedinads_source--credentials--oauth"></a>
### Nested Schema for `settings.linkedinads_source.credentials.oauth`

Optional:

- `client_id` (String, Sensitive) The Client ID of the LinkedIn Ads developer application
- `client_secret` (String, Sensitive) The Client Secret for the LinkedIn Ads developer application
- `refresh_token` (String, Sensitive) The key to refresh the expired access token




<a id="nestedblock--settings--mongo_source"></a>
### Nested Schema for `settings.mongo_source`

Optional:

- `collection` (Block List) (see [below for nested schema](#nestedblock--settings--mongo_source--collection))
- `connection` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mongo_source--connection))
- `excluded_collection` (Block List) (see [below for nested schema](#nestedblock--settings--mongo_source--excluded_collection))
- `secondary_preferred_mode` (Boolean) Read mode for mongo client

<a id="nestedblock--settings--mongo_source--collection"></a>
### Nested Schema for `settings.mongo_source.collection`

Optional:

- `collection_name` (String)
- `database_name` (String)


<a id="nestedblock--settings--mongo_source--connection"></a>
### Nested Schema for `settings.mongo_source.connection`

Optional:

- `auth_source` (String)
- `on_premise` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mongo_source--connection--on_premise))
- `password` (String, Sensitive)
- `user` (String)

<a id="nestedblock--settings--mongo_source--connection--on_premise"></a>
### Nested Schema for `settings.mongo_source.connection.on_premise`

Optional:

- `hosts` (List of String)
- `port` (Number)
- `replica_set` (String)
- `tls_mode` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mongo_source--connection--on_premise--tls_mode))

<a id="nestedblock--settings--mongo_source--connection--on_premise--tls_mode"></a>
### Nested Schema for `settings.mongo_source.connection.on_premise.tls_mode`

Optional:

- `ca_certificate` (String) X.509 certificate of the certificate authority which issued the server's certificate, in PEM format. When CA certificate is specified TLS is used to connect to the server




<a id="nestedblock--settings--mongo_source--excluded_collection"></a>
### Nested Schema for `settings.mongo_source.excluded_collection`

Optional:

- `collection_name` (String)
- `database_name` (String)



<a id="nestedblock--settings--mongo_target"></a>
### Nested Schema for `settings.mongo_target`

Optional:

- `cleanup_policy` (String)
- `connection` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mongo_target--connection))
- `database` (String)

<a id="nestedblock--settings--mongo_target--connection"></a>
### Nested Schema for `settings.mongo_target.connection`

Optional:

- `auth_source` (String)
- `on_premise` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mongo_target--connection--on_premise))
- `password` (String, Sensitive)
- `user` (String)

<a id="nestedblock--settings--mongo_target--connection--on_premise"></a>
### Nested Schema for `settings.mongo_target.connection.on_premise`

Optional:

- `hosts` (List of String)
- `port` (Number)
- `replica_set` (String)
- `tls_mode` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mongo_target--connection--on_premise--tls_mode))

<a id="nestedblock--settings--mongo_target--connection--on_premise--tls_mode"></a>
### Nested Schema for `settings.mongo_target.connection.on_premise.tls_mode`

Optional:

- `ca_certificate` (String) X.509 certificate of the certificate authority which issued the server's certificate, in PEM format. When CA certificate is specified TLS is used to connect to the server





<a id="nestedblock--settings--mysql_source"></a>
### Nested Schema for `settings.mysql_source`

Optional:

- `connection` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mysql_source--connection))
- `database` (String) Database name
- `exclude_tables_regex` (List of String)
- `include_tables_regex` (List of String)
- `object_transfer_settings` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mysql_source--object_transfer_settings))
- `password` (String, Sensitive) Password for database access.
- `service_database` (String) Database name
- `timezone` (String) Is used for parsing timestamps for saving source timezones. Accepts values from IANA timezone database. Default: local timezone.
- `user` (String) User for database access

<a id="nestedblock--settings--mysql_source--connection"></a>
### Nested Schema for `settings.mysql_source.connection`

Optional:

- `on_premise` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mysql_source--connection--on_premise))

<a id="nestedblock--settings--mysql_source--connection--on_premise"></a>
### Nested Schema for `settings.mysql_source.connection.on_premise`

Optional:

- `hosts` (List of String) List of mysql hosts
- `port` (Number) Port of mysql
- `tls_mode` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mysql_source--connection--on_premise--tls_mode))

<a id="nestedblock--settings--mysql_source--connection--on_premise--tls_mode"></a>
### Nested Schema for `settings.mysql_source.connection.on_premise.tls_mode`

Optional:

- `ca_certificate` (String) X.509 certificate of the certificate authority which issued the server's certificate, in PEM format. When CA certificate is specified TLS is used to connect to the server




<a id="nestedblock--settings--mysql_source--object_transfer_settings"></a>
### Nested Schema for `settings.mysql_source.object_transfer_settings`

Optional:

- `routine` (String) CREATE PROCEDURE ... ; CREATE FUNCTION ... ;
- `tables` (String) CREATE TABLE ...
- `trigger` (String) CREATE TRIGGER ...
- `view` (String) CREATE VIEW ...



<a id="nestedblock--settings--mysql_target"></a>
### Nested Schema for `settings.mysql_target`

Optional:

- `cleanup_policy` (String) Cleanup policy for activate, reactivate and reupload processes. Default is truncate.
- `connection` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mysql_target--connection))
- `database` (String) Database name
- `password` (String, Sensitive) Password for database access.
- `service_database` (String) Database schema for service table
- `skip_constraint_checks` (Boolean) Disable constraints checks
- `sql_mode` (String)
- `timezone` (String) Is used for parsing timestamps for saving source timezones. Accepts values from IANA timezone database. Default: local timezone.
- `user` (String) User for database access

<a id="nestedblock--settings--mysql_target--connection"></a>
### Nested Schema for `settings.mysql_target.connection`

Optional:

- `on_premise` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mysql_target--connection--on_premise))

<a id="nestedblock--settings--mysql_target--connection--on_premise"></a>
### Nested Schema for `settings.mysql_target.connection.on_premise`

Optional:

- `hosts` (List of String) List of postgres hosts
- `port` (Number) Port of postgres
- `tls_mode` (Block, Optional) (see [below for nested schema](#nestedblock--settings--mysql_target--connection--on_premise--tls_mode))

<a id="nestedblock--settings--mysql_target--connection--on_premise--tls_mode"></a>
### Nested Schema for `settings.mysql_target.connection.on_premise.tls_mode`

Optional:

- `ca_certificate` (String) X.509 certificate of the certificate authority which issued the server's certificate, in PEM format. When CA certificate is specified TLS is used to connect to the server





<a id="nestedblock--settings--postgres_source"></a>
### Nested Schema for `settings.postgres_source`

Optional:

- `connection` (Block, Optional) (see [below for nested schema](#nestedblock--settings--postgres_source--connection))
- `database` (String) Database name
- `exclude_tables` (List of String)
- `include_tables` (List of String) If none or empty list is presented, all tables are replicated. Full table name with schema. Can contain schema_name.* patterns.
- `object_transfer_settings` (Block, Optional) (see [below for nested schema](#nestedblock--settings--postgres_source--object_transfer_settings))
- `password` (String, Sensitive) Password for database access.
- `service_schema` (String) Database schema for service tables (__consumer_keeper, __data_transfer_mole_finder). Default is public
- `slot_byte_lag_limit` (Number) Maximum lag of replication slot (in bytes); after exceeding this limit replication will be aborted.
- `user` (String) User for database access

<a id="nestedblock--settings--postgres_source--connection"></a>
### Nested Schema for `settings.postgres_source.connection`

Optional:

- `on_premise` (Block, Optional) (see [below for nested schema](#nestedblock--settings--postgres_source--connection--on_premise))

<a id="nestedblock--settings--postgres_source--connection--on_premise"></a>
### Nested Schema for `settings.postgres_source.connection.on_premise`

Optional:

- `hosts` (List of String) List of postgres hosts
- `port` (Number) Port of postgres
- `tls_mode` (Block, Optional) (see [below for nested schema](#nestedblock--settings--postgres_source--connection--on_premise--tls_mode))

<a id="nestedblock--settings--postgres_source--connection--on_premise--tls_mode"></a>
### Nested Schema for `settings.postgres_source.connection.on_premise.tls_mode`

Optional:

- `ca_certificate` (String) X.509 certificate of the certificate authority which issued the server's certificate, in PEM format. When CA certificate is specified TLS is used to connect to the server




<a id="nestedblock--settings--postgres_source--object_transfer_settings"></a>
### Nested Schema for `settings.postgres_source.object_transfer_settings`

Optional:

- `cast` (String) CREATE CAST ...
- `collation` (String) CREATE COLLATION ...
- `constraint` (String) ALTER TABLE ... ADD CONSTRAINT ...
- `default_values` (String) ALTER TABLE ... ALTER COLUMN ... SET DEFAULT ...
- `fk_constraint` (String) ALTER TABLE ... ADD FOREIGN KEY ...
- `function` (String) CREATE FUNCTION ...
- `index` (String) CREATE INDEX ...
- `materialized_view` (String) CREATE MATERIALIZED VIEW ...
- `policy` (String) CREATE POLICY ...
- `primary_key` (String) ALTER TABLE ... ADD PRIMARY KEY ...
- `rule` (String) CREATE RULE ...
- `sequence` (String) CREATE SEQUENCE ...
- `sequence_owned_by` (String) CREATE SEQUENCE ... OWNED BY ...
- `sequence_set` (String)
- `table` (String) CREATE TABLE ...
- `trigger` (String) CREATE TRIGGER ...
- `type` (String) CREATE TYPE ...
- `view` (String) CREATE VIEW ...



<a id="nestedblock--settings--postgres_target"></a>
### Nested Schema for `settings.postgres_target`

Optional:

- `cleanup_policy` (String) Cleanup policy for activate, reactivate and reupload processes. Default is truncate.
- `connection` (Block, Optional) (see [below for nested schema](#nestedblock--settings--postgres_target--connection))
- `database` (String) Database name
- `password` (String, Sensitive) Password for database access.
- `user` (String) User for database access

<a id="nestedblock--settings--postgres_target--connection"></a>
### Nested Schema for `settings.postgres_target.connection`

Optional:

- `on_premise` (Block, Optional) (see [below for nested schema](#nestedblock--settings--postgres_target--connection--on_premise))

<a id="nestedblock--settings--postgres_target--connection--on_premise"></a>
### Nested Schema for `settings.postgres_target.connection.on_premise`

Optional:

- `hosts` (List of String) List of postgres hosts
- `port` (Number) Port of postgres
- `tls_mode` (Block, Optional) (see [below for nested schema](#nestedblock--settings--postgres_target--connection--on_premise--tls_mode))

<a id="nestedblock--settings--postgres_target--connection--on_premise--tls_mode"></a>
### Nested Schema for `settings.postgres_target.connection.on_premise.tls_mode`

Optional:

- `ca_certificate` (String) X.509 certificate of the certificate authority which issued the server's certificate, in PEM format. When CA certificate is specified TLS is used to connect to the server





<a id="nestedblock--settings--s3_source"></a>
### Nested Schema for `settings.s3_source`

Optional:

- `dataset` (String)
- `format` (Block, Optional) (see [below for nested schema](#nestedblock--settings--s3_source--format))
- `path_pattern` (String)
- `provider` (Block, Optional) (see [below for nested schema](#nestedblock--settings--s3_source--provider))
- `schema` (String)

<a id="nestedblock--settings--s3_source--format"></a>
### Nested Schema for `settings.s3_source.format`

Optional:

- `avro` (Block, Optional) (see [below for nested schema](#nestedblock--settings--s3_source--format--avro))
- `csv` (Block, Optional) (see [below for nested schema](#nestedblock--settings--s3_source--format--csv))
- `jsonl` (Block, Optional) (see [below for nested schema](#nestedblock--settings--s3_source--format--jsonl))
- `parquet` (Block, Optional) (see [below for nested schema](#nestedblock--settings--s3_source--format--parquet))

<a id="nestedblock--settings--s3_source--format--avro"></a>
### Nested Schema for `settings.s3_source.format.avro`


<a id="nestedblock--settings--s3_source--format--csv"></a>
### Nested Schema for `settings.s3_source.format.csv`

Optional:

- `additional_reader_options` (String)
- `advanced_options` (String)
- `block_size` (Number)
- `delimiter` (String)
- `double_quote` (Boolean)
- `encoding` (String)
- `escape_char` (String)
- `newlines_in_values` (Boolean)
- `quote_char` (String)


<a id="nestedblock--settings--s3_source--format--jsonl"></a>
### Nested Schema for `settings.s3_source.format.jsonl`

Optional:

- `block_size` (Number)
- `newlines_in_values` (Boolean)
- `unexpected_field_behavior` (String)


<a id="nestedblock--settings--s3_source--format--parquet"></a>
### Nested Schema for `settings.s3_source.format.parquet`

Optional:

- `batch_size` (Number)
- `buffer_size` (Number)
- `columns` (List of String)



<a id="nestedblock--settings--s3_source--provider"></a>
### Nested Schema for `settings.s3_source.provider`

Optional:

- `aws_access_key_id` (String)
- `aws_secret_access_key` (String)
- `bucket` (String)
- `endpoint` (String)
- `path_prefix` (String)
- `use_ssl` (Boolean)
- `verify_ssl_cert` (Boolean)


