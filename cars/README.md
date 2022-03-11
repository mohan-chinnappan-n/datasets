# Visualization experiments on Car Sales Data

## Steps
- [Data](./cars3.csv) is loaded into TCRM (Tableau CRM) 
```

# Login
sfdx force:auth:web:login

# Load into dataset
sfdx mohanc:ea:dataset:load -u mohan.chinnappan.n_ea2@gmail.com -d cars3.csv

```

- [Dashboard json](./dashboard/Cars3DB.json)


## Finding the highest selling Cars (benchmark) from the manufacturers
- ![benchmark candidates](./demos/cars3-db-1.png)

## Dashboard demos

- ![Dashboard demo](./demos/cars3-db-2.webm.gif)
