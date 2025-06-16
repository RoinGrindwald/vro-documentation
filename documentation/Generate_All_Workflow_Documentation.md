# Workflow Documentation - Generate All Workflow Documentation

## Workflow Overview

<table>
  <tr><th>ID</th><td>b1fbd847-f670-4cd1-a757-074e42f3cfe2</td></tr>
  <tr><th>Description</th><td>This is used to generate documentation for all workflows. However, you can exclude the standard Library so that it will document everything outside the library folder.</td></tr>
  <tr><th>Path</th><td>Library - Custom/Orchestrator/Workflows</td></tr>
  <tr><th>Category</th><td>Workflows</td></tr>
  <tr><th>Version</th><td><code>0.0.0</code></td></tr>
  <tr><th>Author</th><td>System Generated</td></tr>
  <tr><th>Date</th><td>Mon Jun 16 2025 05:16:40 GMT-0000 (GMT)</td></tr>
</table>

## Diagram

[<img src="./Generate_All_Workflow_Documentation.svg">](./Generate_All_Workflow_Documentation.svg)

## Inputs

| Name | Type | Description |
|:-----|:-----|:-------------|
| includeLibrary | `boolean` | Set to True if you would like to include the inbuilt library workflows. |
| type | `string` | HTML or Markdown |
| useClarity | `boolean` | If you want to use Clarity UI (HTML Only) |
| horizontal | `boolean` | If you want the schema image to be horizontal |


## Outputs

| Name | Type | Description |
|:-----|:-----|:-------------|
| result | `Array/ResourceElement` | - |


## Attributes (Variables)

| Name | Type | Description | Value |
|:-----|:-----|:-------------|:-------|
| workflows | `Array/Workflow` | Workflows to document | [object Array] |
| errCode | `string` | - |  |


## Usuages

_No Usages defined._


## Dependencies

| Name | Type | Location |
|:-----|:-----|:---------|
| d6e73735-4650-4f8a-b441-d64ed12e8b51 | `Workflow` | SCHEMA - item4 |


## Workflow Steps

<h3><a name='item1'>Step 1 - Get All Workflows (Main path)</a></h3>
<table class='table'>
<tr><th class=''>Name</th><td class=''>item1</td></tr>
<tr><th class=''>Display Name</th><td class=''>Get All Workflows</td></tr>
<tr><th class=''>Type</th><td class=''>task</td></tr>
<tr><th class=''>Description</th><td class=''>Simple task with custom script capability.</td></tr>
<tr><th class=''>Error Bind</th><td class=''>errCode</td></tr>
<tr><th class=''>Script</th><td class='script '>

```javascript
// Get All Workflow Categories
var categories = Server.getAllWorkflowCategories()

// Array to store all workflows
workflows = new Array();

// Loop through categories and get Workflows. Skip Library if includeLibrary is not true
for each(var category in categories) {
    if (category.name == 'Library' && !includeLibrary) {
        System.log("Skipping [" + category.name + "] because includeLibrary was set to [" + includeLibrary + "]")
    } else {
        System.log("Getting Workflows for [" + category.name + "]")
        var catWorkflows = category.allWorkflows

        if (catWorkflows) {
            System.log("Found [" + catWorkflows.length + "]")
            workflows = workflows.concat(catWorkflows);
        }
    }
}

```

</td></tr>
<tr><th class=''>Input Bindings</th><td class=''><table class='table'><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr>
<tr><td>includeLibrary</td><td><code>boolean</code></td><td></td><td>includeLibrary</td></tr>
</table>
</td></tr>
<tr><th class=''>Output Bindings</th><td class=''><table class='table'><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr>
<tr><td>workflows</td><td><code>Array/Workflow</code></td><td></td><td>workflows</td></tr>
</table>
</td></tr>
</table>

<h3><a name='item4'>Step 2 - Generate Workflow Documentation (Main path)</a></h3>
<table class='table'>
<tr><th class=''>Name</th><td class=''>item4</td></tr>
<tr><th class=''>Display Name</th><td class=''>Generate Workflow Documentation</td></tr>
<tr><th class=''>Type</th><td class=''>foreach</td></tr>
<tr><th class=''>Description</th><td class=''>No description</td></tr>
<tr><th class=''>Error Bind</th><td class=''>errCode</td></tr>
<tr><th class=''>Input Bindings</th><td class=''><table class='table'><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr>
<tr><td>workflow</td><td><code>Array/Workflow</code></td><td>Workflow</td><td>*workflows</td></tr>
<tr><td>type</td><td><code>string</code></td><td></td><td>type</td></tr>
<tr><td>useClarity</td><td><code>boolean</code></td><td>If you want to use Clarity UI (HTML Only)</td><td>useClarity</td></tr>
<tr><td>horizontal</td><td><code>boolean</code></td><td>If you want the schema image to be horizontal</td><td>horizontal</td></tr>
</table>
</td></tr>
<tr><th class=''>Output Bindings</th><td class=''><table class='table'><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr>
<tr><td>workflowDocumenation</td><td><code>Array/ResourceElement</code></td><td></td><td>*result</td></tr>
</table>
</td></tr>
<tr><th class=''>Linked Workflow</th><td class=''><table class='table'>
<tr><th>Name</th><td>Generate Workflow Documentation</td></tr>
<tr><th>Version</th><td><code>0.1.1</code></td></tr>
<tr><th>ID</th><td>d6e73735-4650-4f8a-b441-d64ed12e8b51</td></tr>
<tr><th>Description</th><td>This is used to generate documentation for a workflow to Resources.</td></tr>
<tr><th>Inputs</th><td><table class='table'><tr><th>Name</th><th>Type</th><th>Description</th></tr>
<tr><td>workflow</td><td><code>Workflow</code></td><td>Workflow</td></tr>
<tr><td>type</td><td><code>string</code></td><td></td></tr>
<tr><td>useClarity</td><td><code>boolean</code></td><td>If you want to use Clarity UI (HTML Only)</td></tr>
<tr><td>horizontal</td><td><code>boolean</code></td><td>If you want the schema image to be horizontal</td></tr>
</table></td></tr><tr><th>Outputs</th><td><table class='table'><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>workflowDocumenation</td><td><code>ResourceElement</code></td><td></td></tr>
</table></td></tr>
</table>
</td></tr>
</table>

<h3><a name='item0'>Step 3 - item0 (Main path)</a></h3>
<table class='table'>
<tr><th class=''>Name</th><td class=''>item0</td></tr>
<tr><th class=''>Display Name</th><td class=''>undefined</td></tr>
<tr><th class=''>Type</th><td class=''>end</td></tr>
<tr><th class=''>Description</th><td class=''>No description</td></tr>
</table>

<h3><a name='item3'>Step 4 - End workflow (Error Handler path)</a></h3>
<table class='table'>
<tr><th class=''>Name</th><td class=''>item3</td></tr>
<tr><th class=''>Display Name</th><td class=''>End workflow</td></tr>
<tr><th class=''>Type</th><td class=''>end</td></tr>
<tr><th class=''>Description</th><td class=''>No description</td></tr>
<tr><th class=''>Error Bind</th><td class=''>errCode</td></tr>
</table>


