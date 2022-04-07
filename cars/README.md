# Visualization experiments on Car Sales Data

## Steps
-  [Data](./cars3.csv) is loaded into TCRM (Tableau CRM) 
```

# Login (sandbox)
sfdx force:auth:web:login -r https://test.salesforce.com 

# Login (prod)
sfdx force:auth:web:login -r https://login.salesforce.com 


# Load into dataset
sfdx mohanc:ea:dataset:load -u mohan.chinnappan.n_ea2@gmail.com -d cars3.csv

```

-  Create Dashboard based on the created dataset **cars3**
```
sfdx mohanc:ea:dataset:list  -u mohan.chinnappan.n_ea2@gmail.com

Id,Version,Name,Label
0Fb3h000000gTdUCAU,0Fc3h000007WJTeCAO,cars3,cars3


```

## Dashboard 

- [Dashboard json](./dashboard/Cars3DB.json)


## Adding to Home page
- ![adding dashboard to home page](./demos/cars3db-home-page.webm.gif)

-----


## Finding the highest selling Cars (benchmark) from the manufacturers
- ![benchmark candidates](./demos/cars3-db-0.png)
- ![benchmark candidates](./demos/cars3-db-1.png)

- ![benchmark candidates](./demos/)

## Dashboard demos

- ![Dashboard demo](./demos/cars3-db-2.webm.gif)


- ![Dashboard demo 2](./demos/cars3-db.webm.gif)
