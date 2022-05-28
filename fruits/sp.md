# Security Predicate Simple Example

## Login into the org
```
mchinnappan@mchinnappan-ltm fruits % sfdx force:auth:web:login                                                   
Successfully authorized mohan.chinnappan.n_ea2@gmail.com with org ID 00D3h000007R1LuEAK
```

## Load csv into dataset - yield
```
mchinnappan@mchinnappan-ltm fruits % sfdx mohanc:ea:dataset:load -u mohan.chinnappan.n_ea2@gmail.com -d yield.csv
=== Sampling data
-- Please make sure that first row of your data does not have missing values --
[
  [ 'user_id', 'friut', 'qty' ],
  [ '0053h000002xQ5s', 'Mango', '100' ]
]
=== Finding the data types based on the sample data ...
[
  {
    fullyQualifiedName: 'yield.user_id',
    label: 'user_id',
    name: 'user_id',
    isSystemField: false,
    isUniqueId: false,
    isMultiValue: false,
    multiValueSeparator: 'null',
    type: 'Text'
  },
  {
    fullyQualifiedName: 'yield.friut',
    label: 'friut',
    name: 'friut',
    isSystemField: false,
    isUniqueId: false,
    isMultiValue: false,
    multiValueSeparator: 'null',
    type: 'Text'
  },
  {
    fullyQualifiedName: 'yield.qty',
    label: 'qty',
    name: 'qty',
    isSystemField: false,
    isUniqueId: false,
    type: 'Numeric',
    defaultValue: '0',
    precision: 18,
    scale: 0
  }
]
=== Preparing for the loading ...
{ id: '06V3h000000ieZcEAI', success: true, errors: [] }
-- Maximum Chunck size: 9437184 bytes --
=== Loading part: '1' with chunk size: 168 bytes ...
{ id: '06W3h000000edBDEAY', success: true, errors: [] }
=== Loading Complete.
Going to process...

Done.
Time taken: 20.127 seconds
open https://mohansun-ea-02-dev-ed.my.salesforce.com/analytics/dataManager in a web browser to view this job
```

## Dataset yield


