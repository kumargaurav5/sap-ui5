# SAP UI5

# 1. How to initialize OData model.

<aside>
💡 Step SAP BTP Cockpit.

</aside>

![Screenshot (305).png](SAP%20UI5%204a4184828ec74ed5ae924cb38ff461aa/Screenshot_(305).png)

<aside>
💡 Add in xs-app.json.

</aside>

```json
{
      "source": "^/v2/(.*)$",
      "target": "/v2/$1",
      "authenticationType": "none",
      "destination": "NorthWind"
    }
```

source ⇒ [https://services.odata.org/v2/northwind/northwind.svc/](https://services.odata.org/v2/northwind/northwind.svc/)

target ⇒ /v2/northwind/northwind.svc/

destination ⇒ Name of Destination step up in BTP cockpit.

![Screenshot (299).png](SAP%20UI5%204a4184828ec74ed5ae924cb38ff461aa/Screenshot_(299).png)

<aside>
💡 Add in ui5.yaml

</aside>

```yaml
backend:
          - path: /v2
            url: https://services.odata.org
            destination: NorthWind
```

![Screenshot (300).png](SAP%20UI5%204a4184828ec74ed5ae924cb38ff461aa/Screenshot_(300).png)

<aside>
💡 Add in manifest.json

</aside>

```json
"dataSources": {
            "NorthWindDataSource":{
                "uri": "/v2/northwind/northwind.svc/",
                "type": "OData",
                "settings":{
                    "odataVersion": "2.0"
                }
            }
        }
```

![Screenshot (301).png](SAP%20UI5%204a4184828ec74ed5ae924cb38ff461aa/Screenshot_(301).png)

```json
           "NorthWindModel":{
                "dataSource":"NorthWindDataSource"
            }
```

![Screenshot (302).png](SAP%20UI5%204a4184828ec74ed5ae924cb38ff461aa/Screenshot_(302).png)

<aside>
💡 To check odata is fetched successfully. Check metadata in Network

</aside>

![Screenshot (303).png](SAP%20UI5%204a4184828ec74ed5ae924cb38ff461aa/Screenshot_(303).png)

<aside>
💡 Step up myModel in manifest.json

</aside>

```jsx
           "myModel":{
                "type":"sap.ui.model.json.JSONModel"
            },
```

![Untitled](SAP%20UI5%204a4184828ec74ed5ae924cb38ff461aa/Untitled.png)

# 2. How to retrieve Data from oModel(NorthWindModel) and Display in View.

<aside>
💡 To get Model from Manfiest.Json

</aside>

```jsx
this.myModel=this.getOwnerComponent().getModel("myModel");
```

<aside>
💡 To Stepup Model Property and Name of Model to Pass in View

</aside>

```jsx
 this.getView().setModel(this.myModel,"myModel");
```

```jsx
 this.getView().setModel(this.myModel,"myModel");
```