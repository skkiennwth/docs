---
title: "CRUD Variable for REST Services"
id: ""
sidebar_label: "CRUD Variable"
---
---

For every service imported into the app, APIs exposed by the service can be accessed. To create a CRUD variable, you need to drag-and-drop a widget to invoke the service and store the results of that invocation. The Variable operations are restricted by the offerings of the underlying service.

A comprehensive list of these APIs can be found from the [API Designer](/learn/assets/API_Access.png) after the import of the service. 

:::note
Since the service needs to be invoked to fetch the data, the widgets bound to these variables will display values only at run-time, not in Studio mode.
:::

### Supported Widgets

**Web**: DataTable, Form

**Mobile**: List with Form

## Variable Creation

Drag and drop a widget on the canvas. For example, in the following image, a Datatable widget is used. CRUD variable supports 

![datatable crud variable](/learn/assets/datatable-crud-variable.png)

- **Retrieve Data From**: Services is selected by default.
- **Select a Service type**: To use CRUD variable, select **All** from the dropdown.
- **Select a Service**: Select the entity from the drop-down which lists the services available in your application. 
- **Variable Creation**: Once you select the service and table/Entity for the service, a default variable will be created. See the Variable Name field populated by default which will be holding the dataset of the service. You can change the Variable name.
- Select **Form As Dialog** or **Form Below**, and Click **Next**.
- Select pagination, click **Next**.
- Configure table columns. These fields can also be configured using **Advanced Settings** from the **Properties** panel.
- Select template. 
- Configure Form fields. These fields can also be configured using **Advanced Settings** from the **Properties** panel.
- Click **Done**.

For more information to create Datatable, see [Create a Datatable](/learn/app-development/widgets/datalive/datatable/data-table-basic-usage).

### Edit Variable from Variable Dialog

![variable creation](/learn/assets/var_sel.png)

![crud variable properties](/learn/assets/crud-var-properties.png)

- **Name**: You can modify Name.
- **Owner**: The scope of the Variable. Page is the default option. You can choose Application to make it available across the app.

## Properties

| **Property** | **Description** |
| --- | --- |
| **Behavior** ||
| Update data on input change | If checked, the component will be triggered automatically on the change of input data (as mentioned in the data tab) for the variable. |
| Request data on page load | If checked, 'Page' variable will be triggered on page load while 'Application' variable will be triggered on application load. |
| In Flight Behavior | This property determines the behavior when a call is fired through the variable with the previous call still pending. Variable queues all these calls, waits for the previous call completion and then based on the value of the `inFlightBehavior` property, decides what to do with all the queued calls:<br> <br>- doNotExecute - all the queued calls will be discarded, <br>- executeAll - all the calls will be triggered one by one, or <br>- executeLast - only the last call is triggered and the rest are discarded, this is the default behavior|
| **Spinner** |
| Spinner Context | This property specifies on which UI widget the spinner should show. Leave empty if no spinner required. |
| Spinner Message | The message to be displayed below the spinner. Leave empty if no message is required below the spinner. Note: If multiple variables are fired then the spinner messages will be displayed as a list below a single spinner. |

## Events

During the life cycle of a Variable, a set of events are emitted by the Variable, thus giving you the option to control the behavior of the Variable such as input data validations, data processing, success/error handling, and more. 

- OnBeforeUpdate
- OnResult
- OnError
- OnBeforeDatasetReady
- OnCanUpdate
- OnSuccess

To learn how to implement Events, see [Events Documentation](/learn/app-development/variables/events).

## Methods

Few Methods are exposed for Variables which can be used for achieving more control and accessing extra functionality. Listed here are the same.

## `invoke()`

This method updates the Variable’s dataSet with new data by making a call to the target service.

#### Parameters

**options** (object) - It can have fields as operation. String which can take one of the values list, create, update or delete. If no value is provided then list will be taken as the default

- `inputFields` (key-value pair of inputData)  
- **success** (callback)
- **error** (callback)
- **Return Value** none

#### Example

```
var sv = Page.Variables.[variable_name];
    sv.invoke({
	“operation”: “list”,
       "inputFields": {
       "fname": "Steve",
       "lname": "Rogers"
       }
      }, function(data) {
        // Success Callback
        console.log("success", data);
     }, function(error) {
        // Error Callback
        console.log("error", error)
    });
```