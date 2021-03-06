# Using JOINS in Recipes

## Login
```
sfdx force:auth:web:login
Successfully authorized mohan.chinnappan.n_ea2@gmail.com with org ID 00D3h000007R1LuEAK



```
## Sweet Grade Load
```
sfdx mohanc:ea:dataset:load -u mohan.chinnappan.n_ea2@gmail.com -d sweet_grade.csv
=== Sampling data
-- Please make sure that first row of your data does not have missing values --
[ [ 'name', 'score' ], [ 'Mango', '4' ] ]
=== Finding the data types based on the sample data ...
[
  {
    fullyQualifiedName: 'sweet_gr.name',
    label: 'name',
    name: 'name',
    isSystemField: false,
    isUniqueId: false,
    isMultiValue: false,
    multiValueSeparator: 'null',
    type: 'Text'
  },
  {
    fullyQualifiedName: 'sweet_gr.score',
    label: 'score',
    name: 'score',
    isSystemField: false,
    isUniqueId: false,
    type: 'Numeric',
    defaultValue: '0',
    precision: 18,
    scale: 0
  }
]
=== Preparing for the loading ...
{ id: '06V3h000000ieqYEAQ', success: true, errors: [] }
-- Maximum Chunck size: 9437184 bytes --
=== Loading part: '1' with chunk size: 72 bytes ...
{ id: '06W3h000000edSEEAY', success: true, errors: [] }
=== Loading Complete.
Going to process...

Done.
Time taken: 10.290 seconds
open https://mohansun-ea-02-dev-ed.my.salesforce.com/analytics/dataManager in a web browser to view this job

```

![Sweet Grade load](img/sweet-grade-load.png)

## Health Grade Load
```
sfdx mohanc:ea:dataset:load -u mohan.chinnappan.n_ea2@gmail.com -d health_grade.csv
=== Sampling data
-- Please make sure that first row of your data does not have missing values --
[ [ 'name', 'score' ], [ 'Mango', '5' ] ]
=== Finding the data types based on the sample data ...
[
  {
    fullyQualifiedName: 'health_g.name',
    label: 'name',
    name: 'name',
    isSystemField: false,
    isUniqueId: false,
    isMultiValue: false,
    multiValueSeparator: 'null',
    type: 'Text'
  },
  {
    fullyQualifiedName: 'health_g.score',
    label: 'score',
    name: 'score',
    isSystemField: false,
    isUniqueId: false,
    type: 'Numeric',
    defaultValue: '0',
    precision: 18,
    scale: 0
  }
]
=== Preparing for the loading ...
{ id: '06V3h000000ieqdEAA', success: true, errors: [] }
-- Maximum Chunck size: 9437184 bytes --
=== Loading part: '1' with chunk size: 96 bytes ...
{ id: '06W3h000000edSJEAY', success: true, errors: [] }
=== Loading Complete.
Going to process...

Done.
Time taken: 40.003 seconds
open https://mohansun-ea-02-dev-ed.my.salesforce.com/analytics/dataManager in a web browser to view this job

```

- ![Health Grade Load](img/heath-grade-load.png)

## Demo showing the JOINs in Recipe
![Demo JOINs Recipe](img/recipe-Joins-1.webm.gif)

## Recipe JSON
- [JOINSTutorial.json](./JOINSTutorial.json)
```json
{
    "version": "54.0",
    "nodes": {
        "LOAD_DATASET0": {
            "action": "load",
            "parameters": {
                "dataset": {
                    "label": "sweet_gr",
                    "name": "sweet_gr",
                    "type": "analyticsDataset"
                },
                "fields": [
                    "name",
                    "score"
                ]
            },
            "sources": []
        },
        "LOAD_DATASET1": {
            "action": "load",
            "parameters": {
                "dataset": {
                    "label": "health_g",
                    "name": "health_g",
                    "type": "analyticsDataset"
                },
                "fields": [
                    "name",
                    "score"
                ]
            },
            "sources": []
        },
        "JOIN0": {
            "action": "join",
            "parameters": {
                "joinType": "INNER",
                "leftKeys": [
                    "name"
                ],
                "rightKeys": [
                    "name"
                ],
                "rightQualifier": "health_g"
            },
            "schema": {
                "fields": [],
                "slice": {
                    "fields": [],
                    "ignoreMissingFields": true,
                    "mode": "DROP"
                }
            },
            "sources": [
                "LOAD_DATASET0",
                "LOAD_DATASET1"
            ]
        },
        "OUTPUT0": {
            "action": "save",
            "parameters": {
                "dataset": {
                    "label": "JOINedOutput",
                    "name": "JOINedOutput",
                    "type": "analyticsDataset"
                },
                "fields": []
            },
            "sources": [
                "JOIN0"
            ]
        }
    },
    "ui": {
        "nodes": {
            "LOAD_DATASET0": {
                "label": "sweet_gr",
                "type": "LOAD_DATASET",
                "top": 112,
                "left": 112,
                "parameters": {
                    "sampleSize": 2000
                }
            },
            "LOAD_DATASET1": {
                "label": "health_g",
                "type": "LOAD_DATASET",
                "top": 252,
                "left": 112,
                "parameters": {
                    "sampleSize": 2000
                }
            },
            "JOIN0": {
                "label": "JOIN",
                "description": "",
                "type": "JOIN",
                "top": 112,
                "left": 252
            },
            "OUTPUT0": {
                "label": "JoinedOutput",
                "description": "",
                "type": "OUTPUT",
                "top": 112,
                "left": 392
            }
        },
        "connectors": [
            {
                "source": "LOAD_DATASET0",
                "target": "JOIN0"
            },
            {
                "source": "LOAD_DATASET1",
                "target": "JOIN0"
            },
            {
                "source": "JOIN0",
                "target": "OUTPUT0"
            }
        ],
        "hiddenColumns": []
    }
}
```