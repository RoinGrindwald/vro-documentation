# Workflow Documentation - Test

## Workflow Overview

<table>
  <tr><th>ID</th><td>df889c3a-8bee-4826-adf1-787f9bc166b2</td></tr>
  <tr><th>Description</th><td>This is a test workflow that has each type of element on the canvas</td></tr>
  <tr><th>Path</th><td>Library - Custom</td></tr>
  <tr><th>Category</th><td>Library - Custom</td></tr>
  <tr><th>Version</th><td><code>0.0.1</code></td></tr>
  <tr><th>Author</th><td>System Generated</td></tr>
  <tr><th>Date</th><td>Fri Jun 27 2025 03:43:22 GMT-0000 (GMT)</td></tr>
</table>

## Diagram

[<img src="./Test.svg">](./Test.svg)

## Inputs

<p>No Inputs defined.</p>

## Outputs

<p>No Outputs defined.</p>

## Attributes (Variables)

| Name | Type | Description | Value |
|:-----|:-----|:-------------|:-------|
| variableString | `string` | - |  |
| query | `string` | - |  |
| vraHost | `VRA:Host` | - | - |
| errCode | `string` | - |  |
| object | `Any` | - |  |
| array | `Array/string` | - | - |
| wfToken | `WorkflowToken` | - | - |
| security_group | `LdapGroup` | - | - |
| security_assignees | `Array/LdapUser` | - | [object Array] |
| security_assignee_groups | `Array/LdapGroup` | - | [object Array] |
| timeout_date | `Date` | - | - |
| newCredential | `Credential` | - | - |
| trigger_ref | `Trigger` | - | - |
| sleepTime | `number` | - | - |
| isExternalEvent | `boolean` | - | false |
| eventName | `string` | - |  |
| endDate | `Date` | - | - |
| success | `boolean` | - | false |
| user | `AD:User` | - | - |
| group | `AD:UserGroup` | - | - |
| counter | `number` | - | - |
| url | `string` | - |  |
| content | `string` | - |  |
| result | `string` | - |  |
| workflowScheduleDate | `Date` | - | - |
| scheduledTask | `Task` | - | - |
| resourceElement | `ResourceElement` | - | Test.md |


## Usuages

| Name | Type | Location |
|:-----|:-----|:---------|
| Test - df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item16 |
| Test - df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item17 |
| Test - df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item18 |
| Test - df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item20 |
| Test - df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item20 |
| Test - df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item36 |


## Dependencies

| Name | Type | Location |
|:-----|:-----|:---------|
| 3808259c-7d5f-4a4f-b10b-eaa1c4a9b756 - 3808259c-7d5f-4a4f-b10b-eaa1c4a9b756 | `ResourceElement` | ATTRIBUTE - resourceElement |
| com.broadcom.pso.vra.host/getHost | `ScriptModule` | SCHEMA - item2 |
| df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item16 |
| df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item17 |
| df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item18 |
| df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item20 |
| df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item20 |
| 57c2229a-c3d9-4fd3-85f0-1539d41514f0 | `Workflow` | SCHEMA - item24 |
| df889c3a-8bee-4826-adf1-787f9bc166b2 | `Workflow` | SCHEMA - item36 |


## Workflow Steps

<h3><a name='item1'>Scriptable task [Main path]</a></h3>
<table>
<tr><th>Name</th><td>item1</td></tr>
<tr><th>Display Name</th><td>Scriptable task</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Simple task with custom script capability.</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>variableString</td><td><code>string</code></td><td></td><td>variableString</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>variableString</td><td><code>string</code></td><td></td><td>variableString</td></tr></table></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Do Nothing
variableString = variableString
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item2'>getHost [Main path]</a></h3>
<table>
<tr><th>Name</th><td>item2</td></tr>
<tr><th>Display Name</th><td>getHost</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Add a note to the workflow schema.</td></tr>
<tr><th>Script Module</th><td>com.broadcom.pso.vra.host/getHost</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>query</td><td><code>string</code></td><td>(Optional) Use only if you have multiple VRA Connections</td><td>query</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>actionResult</td><td><code>VRA:Host</code></td><td></td><td>vraHost</td></tr></table></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto generated script, cannot be modified !
actionResult = System.getModule("com.broadcom.pso.vra.host").getHost(query);

```

</td></tr>
<tr><th>Used Actions</th><td><table><tr><th>Name</th><td>getHost</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vra.host</td></tr>
<tr><th>ID</th><td>eaf88276-8765-4e5b-b2e2-24125a792ff6</td></tr>
<tr><th>Version</th><td><code>0.1.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>query</td><td><code>string</code></td><td>(Optional) Use only if you have multiple VRA Connections</td></tr></table></td></tr>
<tr><th>Output</th><td>VRA:Host</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Search VRA:Host using query
var allVraHost = Server.findAllForType("VRA:Host");

// Return if only 1 connection found
if (allVraHost.length == 1) {
    return allVraHost[0]
} else {
    // Set the query to Default if blank
    if (!query) {
        query = "Default";
    }
    for each(var host in allVraHost) {
        if (host.name.match(query)) {
            var vraHost = host;
            break;
        }
    }
    // Return if found
    if (vraHost) {
        return vraHost
    } else {
        throw "Unable to find vRA Host"
    }
}
```

</td></tr>
</table><br></td></tr>
</table>


---
<h3><a name='item15'>Decision [Main path]</a></h3>
<table>
<tr><th>Name</th><td>item15</td></tr>
<tr><th>Display Name</th><td>Decision</td></tr>
<tr><th>Type</th><td>custom-condition</td></tr>
<tr><th>Description</th><td>Custom decision based on a custom script.</td></tr>
<tr><th>Input Bindings</th><td></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
return true;
```

</td></tr>
<tr><th>Condition True</th><td>item16</td></tr>
<tr><th>Condition False</th><td>item21</td></tr>
</table>


---
<h3><a name='item16'>Test Normal [True (Decision) path]</a></h3>
<table>
<tr><th>Name</th><td>item16</td></tr>
<tr><th>Display Name</th><td>Test Normal</td></tr>
<tr><th>Type</th><td>link</td></tr>
<tr><th>Description</th><td> </td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Linked Workflow</th><td><table>
<tr><th>Name</th><td>Test</td></tr>
<tr><th>Version</th><td><code>0.0.1</code></td></tr>
<tr><th>ID</th><td>df889c3a-8bee-4826-adf1-787f9bc166b2</td></tr>
<tr><th>Description</th><td>This is a test workflow that has each type of element on the canvas</td></tr>
</table></td></tr>
</table>


---
<h3><a name='item17'>Test ForEach [True (Decision) path]</a></h3>
<table>
<tr><th>Name</th><td>item17</td></tr>
<tr><th>Display Name</th><td>Test ForEach</td></tr>
<tr><th>Type</th><td>foreach</td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td></td><td><code>Array/string</code></td><td></td><td>*array</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Linked Workflow</th><td><table>
<tr><th>Name</th><td>Test</td></tr>
<tr><th>Version</th><td><code>0.0.1</code></td></tr>
<tr><th>ID</th><td>df889c3a-8bee-4826-adf1-787f9bc166b2</td></tr>
<tr><th>Description</th><td>This is a test workflow that has each type of element on the canvas</td></tr>
</table></td></tr>
</table>


---
<h3><a name='item18'>Test Async [True (Decision) path]</a></h3>
<table>
<tr><th>Name</th><td>item18</td></tr>
<tr><th>Display Name</th><td>Test Async</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Start an asynchronous workflow.</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td></td></tr>
<tr><th>Output Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>wfToken</td><td><code>WorkflowToken</code></td><td></td><td>wfToken</td></tr></table></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto generated script, cannot be modified !
var workflowToLaunch = Server.getWorkflowWithId("df889c3a-8bee-4826-adf1-787f9bc166b2");
if (workflowToLaunch == null) {
	throw "Workflow not found";
}

var workflowParameters = new Properties();
wfToken = workflowToLaunch.execute(workflowParameters);

```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item36'>Test [True (Decision) path]</a></h3>
<table>
<tr><th>Name</th><td>item36</td></tr>
<tr><th>Display Name</th><td>Test</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Schedule a workflow and create a task.</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>workflowScheduleDate</td><td><code>Date</code></td><td></td><td>workflowScheduleDate</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>scheduledTask</td><td><code>Task</code></td><td></td><td>scheduledTask</td></tr></table></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto generated script, cannot be modified !
var workflowToLaunch = Server.getWorkflowWithId("df889c3a-8bee-4826-adf1-787f9bc166b2");
if (workflowToLaunch == null) {
	throw "Workflow not found";
}

var workflowParameters = new Properties();
scheduledTask = workflowToLaunch.schedule(workflowParameters, workflowScheduleDate);

```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item20'>Nested workflows [True (Decision) path]</a></h3>
<table>
<tr><th>Name</th><td>item20</td></tr>
<tr><th>Display Name</th><td>Nested workflows</td></tr>
<tr><th>Type</th><td>multiple</td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Multiple Workflows</th><td><table>
<tr><th>Name</th><td>Test</td></tr>
<tr><th>Version</th><td><code>0.0.1</code></td></tr>
<tr><th>ID</th><td>df889c3a-8bee-4826-adf1-787f9bc166b2</td></tr>
<tr><th>Description</th><td>This is a test workflow that has each type of element on the canvas</td></tr>
</table><br><table>
<tr><th>Name</th><td>Test</td></tr>
<tr><th>Version</th><td><code>0.0.1</code></td></tr>
<tr><th>ID</th><td>df889c3a-8bee-4826-adf1-787f9bc166b2</td></tr>
<tr><th>Description</th><td>This is a test workflow that has each type of element on the canvas</td></tr>
</table></td></tr>
</table>


---
<h3><a name='item0'>End Workflow [True (Decision) path]</a></h3>
<table>
<tr><th>Name</th><td>item0</td></tr>
<tr><th>Display Name</th><td>undefined</td></tr>
<tr><th>Type</th><td>end</td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Input Bindings</th><td></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
</table>


---
<h3><a name='item21'>User interaction [False (Decision) path]</a></h3>
<table>
<tr><th>Name</th><td>item21</td></tr>
<tr><th>Display Name</th><td>User interaction</td></tr>
<tr><th>Type</th><td>input</td></tr>
<tr><th>Description</th><td>Use this element to set up a user interaction.</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>security.group</td><td><code>LdapGroup</code></td><td>Any user member of this group will be authorized to fill in this form.</td><td>security_group</td></tr>
<tr><td>security.assignees</td><td><code>Array/LdapUser</code></td><td>Any user from this array of users will be authorized to fill in this form</td><td>security_assignees</td></tr>
<tr><td>security.assignee.groups</td><td><code>Array/LdapGroup</code></td><td>Any user member of any of the groups will be authorized to fill in this form.</td><td>security_assignee_groups</td></tr>
<tr><td>timeout.date</td><td><code>Date</code></td><td>If not null, this input item will wait until date and will continue workflow execution.</td><td>timeout_date</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
</table>


---
<h3><a name='item22'>Change credential [False (Decision) path]</a></h3>
<table>
<tr><th>Name</th><td>item22</td></tr>
<tr><th>Display Name</th><td>Change credential</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Change current execution credential.</td></tr>
<tr><th>Prototype ID</th><td>change-credential</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>newCredential</td><td><code>Credential</code></td><td>New credential</td><td>newCredential</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
if (newCredential != null) {
  if (String(newCredential) !== String(Server.getCredential())) {
    workflow.changeCredential(newCredential) ;
  }
  else {
    System.log("Change credential is same as current user!");
  }
}
else  {
  throw "'newCredential' is NULL";
}

```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item24'>Decision activity [False (Decision) path]</a></h3>
<table>
<tr><th>Name</th><td>item24</td></tr>
<tr><th>Display Name</th><td>Decision activity</td></tr>
<tr><th>Type</th><td>decision-activity</td></tr>
<tr><th>Description</th><td>Decision activity based on a workflow or an action.</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>user</td><td><code>AD:User</code></td><td>AD User you want to add to a group</td><td>user</td></tr>
<tr><td>group</td><td><code>AD:UserGroup</code></td><td>User Group you want the user added to</td><td>group</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Generated by the system, cannot be edited
return (results !== null);
```

</td></tr>
</table>


---
<h3><a name='item25'>Waiting timer [True (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item25</td></tr>
<tr><th>Display Name</th><td>Waiting timer</td></tr>
<tr><th>Type</th><td>waiting-timer</td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>timer.date</td><td><code>Date</code></td><td>This timer item will wait until date and will continue workflow execution.</td><td>timeout_date</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
</table>


---
<h3><a name='item26'>Waiting event [True (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item26</td></tr>
<tr><th>Display Name</th><td>Waiting event</td></tr>
<tr><th>Type</th><td>waiting-event</td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>trigger.ref</td><td><code>Trigger</code></td><td>Trigger waiting for a specific event before continuing workflow run.</td><td>trigger_ref</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
</table>


---
<h3><a name='item27'>Sleep [True (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item27</td></tr>
<tr><th>Display Name</th><td>Sleep</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Sleep a given number of seconds.</td></tr>
<tr><th>Prototype ID</th><td>sleep</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>sleepTime</td><td><code>number</code></td><td>Time to sleep in seconds</td><td>sleepTime</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
if ( sleepTime !== null )  {
	System.sleep(sleepTime * 1000);
}else  {
	throw "'sleepTime' is NULL"; 
}
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item28'>Wait until date [True (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item28</td></tr>
<tr><th>Display Name</th><td>Wait until date</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Wait until date.</td></tr>
<tr><th>Prototype ID</th><td>wait-until-date</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>waitDate</td><td><code>Date</code></td><td>Wait date</td><td>timeout_date</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script 
if (waitDate !== null) { 
	System.waitUntil(waitDate,1000);
}
else  { 
	throw "'waitDate' is NULL"; 
}

```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item29'>Wait for custom event [True (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item29</td></tr>
<tr><th>Display Name</th><td>Wait for custom event</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Wait for custom event.</td></tr>
<tr><th>Prototype ID</th><td>wait-custom-event</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>isExternalEvent</td><td><code>boolean</code></td><td>External custom event</td><td>isExternalEvent</td></tr>
<tr><td>eventName</td><td><code>string</code></td><td>Custom event name</td><td>eventName</td></tr>
<tr><td>endDate</td><td><code>Date</code></td><td>Expiration date</td><td>endDate</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>success</td><td><code>boolean</code></td><td>Return true if the custom event was received before 'endDate' is reached.</td><td>success</td></tr></table></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Auto-generated script
var eventType = isExternalEvent ? 'external' : 'internal';
var eventCustom = null;
if (eventName != null) {
	eventCustom = System.waitCustomEventUntil(eventType,eventName,endDate);
}
success = (eventCustom != null) ;
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item30'>Send custom event [True (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item30</td></tr>
<tr><th>Display Name</th><td>Send custom event</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Send a custom event.</td></tr>
<tr><th>Prototype ID</th><td>send-custom-event</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>eventName</td><td><code>string</code></td><td>Custom event name</td><td>eventName</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Auto-generated script
if (eventName != null) {
	System.sendCustomEvent(eventName);
} else  {
	throw "'eventName' is NULL";
}

```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item14'>End Workflow [True (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item14</td></tr>
<tr><th>Display Name</th><td>undefined</td></tr>
<tr><th>Type</th><td>end</td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Input Bindings</th><td></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
</table>


---
<h3><a name='item31'>Switch [False (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item31</td></tr>
<tr><th>Display Name</th><td>Switch</td></tr>
<tr><th>Type</th><td>switch</td></tr>
<tr><th>Description</th><td>Basic switch activity based on a workflow attribute or parameter.</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>vraHost</td><td><code>VRA:Host</code></td><td></td><td>vraHost</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Generated by the system, cannot be edited
if (vraHost !== null) {
  return "item33";
} else if (true) {
  return "item32";
}

```

</td></tr>
<tr><th>Switch Cases</th><td><table><tr><th>Condition</th><th>Target</th></tr><tr><td></td><td>item33</td></tr>
<tr><td></td><td>item32</td></tr></table></td></tr>
</table>


---
<h3><a name='item33'>Decrease counter [False (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item33</td></tr>
<tr><th>Display Name</th><td>Decrease counter</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Decrement a counter by one.</td></tr>
<tr><th>Prototype ID</th><td>decrease-counter</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>counter</td><td><code>number</code></td><td>Item to decrease</td><td>counter</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>counter</td><td><code>number</code></td><td>Decreased item</td><td>counter</td></tr></table></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
counter = counter - 1;
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item34'>HTTP post [False (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item34</td></tr>
<tr><th>Display Name</th><td>HTTP post</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Post content via HTTP.</td></tr>
<tr><th>Prototype ID</th><td>http-post</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>url</td><td><code>string</code></td><td>Target url</td><td>url</td></tr>
<tr><td>content</td><td><code>string</code></td><td>Data to post</td><td>content</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>result</td><td><code>string</code></td><td>Operation result</td><td>result</td></tr></table></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
var urlObject = new URL(url);
result = urlObject.postContent(content);
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item23'>End Workflow [False (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item23</td></tr>
<tr><th>Display Name</th><td>undefined</td></tr>
<tr><th>Type</th><td>end</td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Input Bindings</th><td></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
</table>


---
<h3><a name='item32'>Increase counter [False (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item32</td></tr>
<tr><th>Display Name</th><td>Increase counter</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Increment a counter by one.</td></tr>
<tr><th>Prototype ID</th><td>increase-counter</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>counter</td><td><code>number</code></td><td>Item to increase</td><td>counter</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>counter</td><td><code>number</code></td><td>Increased item</td><td>counter</td></tr></table></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
counter = counter + 1;
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item35'>HTTP get [False (Decision activity) path]</a></h3>
<table>
<tr><th>Name</th><td>item35</td></tr>
<tr><th>Display Name</th><td>HTTP get</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Get content from HTTP.</td></tr>
<tr><th>Prototype ID</th><td>http-get</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>url</td><td><code>string</code></td><td>Target url</td><td>url</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>result</td><td><code>string</code></td><td>Operation result</td><td>result</td></tr></table></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
var urlObject = new URL(url);
result = urlObject.getContent() ;
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item4'>System log [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item4</td></tr>
<tr><th>Display Name</th><td>System log</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Log the input text to the console log with the level "log".</td></tr>
<tr><th>Prototype ID</th><td>system-log</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>text</td><td><code>string</code></td><td>The text to log</td><td>errCode</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
System.log(text);
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item5'>Server log [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item5</td></tr>
<tr><th>Display Name</th><td>Server log</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Log the input text to the server log with the level "log".</td></tr>
<tr><th>Prototype ID</th><td>server-log</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>text</td><td><code>string</code></td><td>The text to log</td><td>errCode</td></tr>
<tr><td>object</td><td><code>Any</code></td><td>The text to log and additional info</td><td>object</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
Server.log(text, object);
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item6'>System and Server log [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item6</td></tr>
<tr><th>Display Name</th><td>System and Server log</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Log the input text to the console and the server log with the level "log".</td></tr>
<tr><th>Prototype ID</th><td>system-server-log</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>text</td><td><code>string</code></td><td>The text to log</td><td>errCode</td></tr>
<tr><td>object</td><td><code>Any</code></td><td>The text to log and additional info</td><td>object</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
System.log(text + "-" + object);
Server.log(text, object);
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item7'>System warning [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item7</td></tr>
<tr><th>Display Name</th><td>System warning</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Log the input text to the console log with the level "warn".</td></tr>
<tr><th>Prototype ID</th><td>system-warning</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>text</td><td><code>string</code></td><td>The text to log</td><td>errCode</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
System.warn(text);
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item13'>Server warning [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item13</td></tr>
<tr><th>Display Name</th><td>Server warning</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Log the input text to the server log with the level "warn".</td></tr>
<tr><th>Prototype ID</th><td>server-warning</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>text</td><td><code>string</code></td><td>The text to log</td><td>errCode</td></tr>
<tr><td>object</td><td><code>Any</code></td><td>The text to log and additional info</td><td>object</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
Server.warn(text, object);
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item9'>System and Server warning [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item9</td></tr>
<tr><th>Display Name</th><td>System and Server warning</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Log the input text to the console and the server log with the level "warn".</td></tr>
<tr><th>Prototype ID</th><td>system-server-warning</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>text</td><td><code>string</code></td><td>The text to log</td><td>errCode</td></tr>
<tr><td>object</td><td><code>Any</code></td><td>The text to log and additional info</td><td>object</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
System.warn(text + "-" + object);
Server.warn(text, object);
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item10'>System error [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item10</td></tr>
<tr><th>Display Name</th><td>System error</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>'Log the input text to the console log with the level "error".'</td></tr>
<tr><th>Prototype ID</th><td>system-error</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>text</td><td><code>string</code></td><td>The text to log</td><td>errCode</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
System.error(text);
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item11'>Server error [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item11</td></tr>
<tr><th>Display Name</th><td>Server error</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Log the input text to the server log with the level "error".</td></tr>
<tr><th>Prototype ID</th><td>server-error</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>text</td><td><code>string</code></td><td>The text to log</td><td>errCode</td></tr>
<tr><td>object</td><td><code>Any</code></td><td>The text to log and additional info</td><td>object</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
Server.error(text, object);
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item12'>System and Server error [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item12</td></tr>
<tr><th>Display Name</th><td>System and Server error</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Log the input text to the console and the server log with the level "error".</td></tr>
<tr><th>Prototype ID</th><td>system-server-error</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>text</td><td><code>string</code></td><td>The text to log</td><td>errCode</td></tr>
<tr><td>object</td><td><code>Any</code></td><td>The text to log and additional info</td><td>object</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto-generated script
System.error(text + "-" + object);
Server.error(text, object);
```

</td></tr>
<tr><th>Used Actions</th><td></td></tr>
</table>


---
<h3><a name='item3'>End workflow [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item3</td></tr>
<tr><th>Display Name</th><td>End workflow</td></tr>
<tr><th>Type</th><td>end</td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td></td></tr>
<tr><th>Output Bindings</th><td></td></tr>
</table>


---
