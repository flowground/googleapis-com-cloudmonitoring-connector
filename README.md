# ![LOGO](logo.png) Cloud Monitoring **flow**ground Connector

## Description

A generated **flow**ground connector for the Cloud Monitoring API (version v2beta2).

Generated from: https://api.apis.guru/v2/specs/googleapis.com/cloudmonitoring/v2beta2/swagger.json<br/>
Generated at: 2019-05-23T12:13:06+03:00

## API Description

Accesses Google Cloud Monitoring data.

## Authorization

Supported authorization schemes:
- OAuth2

For OAuth 2.0 you need to specify OAuth Client credentials as environment variables in the connector repository:
* `OAUTH_CLIENT_ID` - your OAuth client id
* `OAUTH_CLIENT_SECRET` - your OAuth client secret

## Actions

### List metric descriptors that match the query. If the query is not set, then all of the metric descriptors will be returned. Large responses will be paginated, use the nextPageToken returned in the response to request subsequent pages of results by setting the pageToken query parameter to the value of the nextPageToken.

*Tags:* `metricDescriptors`

#### Input Parameters
* `project` - _required_ - The project id. The value can be the numeric project ID or string-based project name.
* `count` - _optional_ - Maximum number of metric descriptors per page. Used for pagination. If not specified, count = 100.
* `pageToken` - _optional_ - The pagination token, which is used to page through large result sets. Set this value to the value of the nextPageToken to retrieve the next page of results.
* `query` - _optional_ - The query used to search against existing metrics. Separate keywords with a space; the service joins all keywords with AND, meaning that all keywords must match for a metric to be returned. If this field is omitted, all metrics are returned. If an empty string is passed with this field, no metrics are returned.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters. Overrides userIp if both are provided.
* `userIp` - _optional_ - IP address of the site where the request originates. Use this if you want to enforce per-user limits.

### Create a new metric.

*Tags:* `metricDescriptors`

#### Input Parameters
* `project` - _required_ - The project id. The value can be the numeric project ID or string-based project name.
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters. Overrides userIp if both are provided.
* `userIp` - _optional_ - IP address of the site where the request originates. Use this if you want to enforce per-user limits.

### Delete an existing metric.

*Tags:* `metricDescriptors`

#### Input Parameters
* `project` - _required_ - The project ID to which the metric belongs.
* `metric` - _required_ - Name of the metric.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters. Overrides userIp if both are provided.
* `userIp` - _optional_ - IP address of the site where the request originates. Use this if you want to enforce per-user limits.

### List the data points of the time series that match the metric and labels values and that have data points in the interval. Large responses are paginated; use the nextPageToken returned in the response to request subsequent pages of results by setting the pageToken query parameter to the value of the nextPageToken.

*Tags:* `timeseries`

#### Input Parameters
* `project` - _required_ - The project ID to which this time series belongs. The value can be the numeric project ID or string-based project name.
* `metric` - _required_ - Metric names are protocol-free URLs as listed in the Supported Metrics page. For example, compute.googleapis.com/instance/disk/read_ops_count.
* `youngest` - _required_ - End of the time interval (inclusive), which is expressed as an RFC 3339 timestamp.
* `aggregator` - _optional_ - The aggregation function that will reduce the data points in each window to a single point. This parameter is only valid for non-cumulative metrics with a value type of INT64 or DOUBLE.
    Possible values: max, mean, min, sum.
* `count` - _optional_ - Maximum number of data points per page, which is used for pagination of results.
* `labels` - _optional_ - A collection of labels for the matching time series, which are represented as:  
- key==value: key equals the value 
- key=~value: key regex matches the value 
- key!=value: key does not equal the value 
- key!~value: key regex does not match the value  For example, to list all of the time series descriptors for the region us-central1, you could specify:
label=cloud.googleapis.com%2Flocation=~us-central1.*
* `oldest` - _optional_ - Start of the time interval (exclusive), which is expressed as an RFC 3339 timestamp. If neither oldest nor timespan is specified, the default time interval will be (youngest - 4 hours, youngest]
* `pageToken` - _optional_ - The pagination token, which is used to page through large result sets. Set this value to the value of the nextPageToken to retrieve the next page of results.
* `timespan` - _optional_ - Length of the time interval to query, which is an alternative way to declare the interval: (youngest - timespan, youngest]. The timespan and oldest parameters should not be used together. Units:  
- s: second 
- m: minute 
- h: hour 
- d: day 
- w: week  Examples: 2s, 3m, 4w. Only one unit is allowed, for example: 2w3d is not allowed; you should use 17d instead.

If neither oldest nor timespan is specified, the default time interval will be (youngest - 4 hours, youngest].
* `window` - _optional_ - The sampling window. At most one data point will be returned for each window in the requested time interval. This parameter is only valid for non-cumulative metric types. Units:  
- m: minute 
- h: hour 
- d: day 
- w: week  Examples: 3m, 4w. Only one unit is allowed, for example: 2w3d is not allowed; you should use 17d instead.

### Put data points to one or more time series for one or more metrics. If a time series does not exist, a new time series will be created. It is not allowed to write a time series point that is older than the existing youngest point of that time series. Points that are older than the existing youngest point of that time series will be discarded silently. Therefore, users should make sure that points of a time series are written sequentially in the order of their end time.

*Tags:* `timeseries`

#### Input Parameters
* `project` - _required_ - The project ID. The value can be the numeric project ID or string-based project name.
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters. Overrides userIp if both are provided.
* `userIp` - _optional_ - IP address of the site where the request originates. Use this if you want to enforce per-user limits.

### List the descriptors of the time series that match the metric and labels values and that have data points in the interval. Large responses are paginated; use the nextPageToken returned in the response to request subsequent pages of results by setting the pageToken query parameter to the value of the nextPageToken.

*Tags:* `timeseriesDescriptors`

#### Input Parameters
* `project` - _required_ - The project ID to which this time series belongs. The value can be the numeric project ID or string-based project name.
* `metric` - _required_ - Metric names are protocol-free URLs as listed in the Supported Metrics page. For example, compute.googleapis.com/instance/disk/read_ops_count.
* `youngest` - _required_ - End of the time interval (inclusive), which is expressed as an RFC 3339 timestamp.
* `aggregator` - _optional_ - The aggregation function that will reduce the data points in each window to a single point. This parameter is only valid for non-cumulative metrics with a value type of INT64 or DOUBLE.
    Possible values: max, mean, min, sum.
* `count` - _optional_ - Maximum number of time series descriptors per page. Used for pagination. If not specified, count = 100.
* `labels` - _optional_ - A collection of labels for the matching time series, which are represented as:  
- key==value: key equals the value 
- key=~value: key regex matches the value 
- key!=value: key does not equal the value 
- key!~value: key regex does not match the value  For example, to list all of the time series descriptors for the region us-central1, you could specify:
label=cloud.googleapis.com%2Flocation=~us-central1.*
* `oldest` - _optional_ - Start of the time interval (exclusive), which is expressed as an RFC 3339 timestamp. If neither oldest nor timespan is specified, the default time interval will be (youngest - 4 hours, youngest]
* `pageToken` - _optional_ - The pagination token, which is used to page through large result sets. Set this value to the value of the nextPageToken to retrieve the next page of results.
* `timespan` - _optional_ - Length of the time interval to query, which is an alternative way to declare the interval: (youngest - timespan, youngest]. The timespan and oldest parameters should not be used together. Units:  
- s: second 
- m: minute 
- h: hour 
- d: day 
- w: week  Examples: 2s, 3m, 4w. Only one unit is allowed, for example: 2w3d is not allowed; you should use 17d instead.

If neither oldest nor timespan is specified, the default time interval will be (youngest - 4 hours, youngest].
* `window` - _optional_ - The sampling window. At most one data point will be returned for each window in the requested time interval. This parameter is only valid for non-cumulative metric types. Units:  
- m: minute 
- h: hour 
- d: day 
- w: week  Examples: 3m, 4w. Only one unit is allowed, for example: 2w3d is not allowed; you should use 17d instead.

## License

**flow**ground :- Telekom iPaaS / googleapis-com-cloudmonitoring-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
