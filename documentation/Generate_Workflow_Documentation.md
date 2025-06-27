# Workflow Documentation - Generate Workflow Documentation

## Workflow Overview

<table>
  <tr><th>ID</th><td>d6e73735-4650-4f8a-b441-d64ed12e8b51</td></tr>
  <tr><th>Description</th><td>This is used to generate documentation for a workflow to Resources.</td></tr>
  <tr><th>Path</th><td>Library - Custom/Orchestrator/Workflows</td></tr>
  <tr><th>Category</th><td>Workflows</td></tr>
  <tr><th>Version</th><td><code>0.2.0</code></td></tr>
  <tr><th>Author</th><td>System Generated</td></tr>
  <tr><th>Date</th><td>Fri Jun 27 2025 03:43:31 GMT-0000 (GMT)</td></tr>
</table>

## Diagram

[<img src="./Generate_Workflow_Documentation.svg">](./Generate_Workflow_Documentation.svg)

## Inputs

<table>
<tr><th>Name</th><th>Type</th><th>Description</th><th>Value</th></tr>
<tr><td>workflow</td><td>Workflow</td><td>Workflow</td><td>-</td></tr>
<tr><td>type</td><td>string</td><td>-</td><td>-</td></tr>
<tr><td>horizontal</td><td>boolean</td><td>If you want the schema image to be horizontal</td><td>-</td></tr>
<tr><td>asTable</td><td>boolean</td><td>-</td><td>-</td></tr>
</table>

## Outputs

<table>
<tr><th>Name</th><th>Type</th><th>Description</th><th>Value</th></tr>
<tr><td>workflowDocumenation</td><td>ResourceElement</td><td>-</td><td>-</td></tr>
</table>

## Attributes (Variables)

| Name | Type | Description | Value |
|:-----|:-----|:-------------|:-------|
| errCode | `string` | - |  |


## Usuages

| Name | Type | Location |
|:-----|:-----|:---------|
| com.broadcom.pso.vro.documentation - 8a7484ad96d72cb60196ea5bfbe70139 | `Package` | PACKAGE |
| Generate Workflow Category Documentation - 381b57fc-f8ef-4ce5-8a1a-d044c364172c | `Workflow` | SCHEMA - item3 |
| Generate All Workflow Documentation - b1fbd847-f670-4cd1-a757-074e42f3cfe2 | `Workflow` | SCHEMA - item4 |


## Dependencies

| Name | Type | Location |
|:-----|:-----|:---------|
| com.broadcom.pso.vro.rest.documentation/generateWorkflowDocumentationToResources | `ScriptModule` | SCHEMA - item1 |


## Workflow Steps

<h3><a name='item1'>Generate Workflow Documentation To Resources [Main path]</a></h3>
<table>
<tr><th>Name</th><td>item1</td></tr>
<tr><th>Display Name</th><td>Generate Workflow Documentation To Resources</td></tr>
<tr><th>Type</th><td>task</td></tr>
<tr><th>Description</th><td>Add a note to the workflow schema.</td></tr>
<tr><th>Script Module</th><td>com.broadcom.pso.vro.rest.documentation/generateWorkflowDocumentationToResources</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>workflow</td><td><code>Workflow</code></td><td>Workflow</td><td>workflow</td></tr>
<tr><td>type</td><td><code>string</code></td><td>HTML or Markdown</td><td>type</td></tr>
<tr><td>horizontal</td><td><code>boolean</code></td><td>If you want the schema image to be horizontal</td><td>horizontal</td></tr>
<tr><td>asTable</td><td><code>boolean</code></td><td>Render as a table (true) or sectioned layout (false)</td><td>asTable</td></tr></table></td></tr>
<tr><th>Output Bindings</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr><tr><td>actionResult</td><td><code>ResourceElement</code></td><td></td><td>workflowDocumenation</td></tr></table></td></tr>
<tr><th>Script</th><td class='script'>

```javascript
//Auto generated script, cannot be modified !
actionResult = System.getModule("com.broadcom.pso.vro.rest.documentation").generateWorkflowDocumentationToResources(workflow,type,horizontal,asTable);

```

</td></tr>
<tr><th>Used Actions</th><td><table><tr><th>Name</th><td>generateWorkflowDocumentationToResources</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.documentation</td></tr>
<tr><th>ID</th><td>dd68a9d5-3c52-4593-b1e9-01dce27727ce</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>This is used to Generate the documentation to a resource element</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>workflow</td><td><code>Workflow</code></td><td>Workflow</td></tr>
<tr><td>type</td><td><code>string</code></td><td>HTML or Markdown</td></tr>
<tr><td>horizontal</td><td><code>boolean</code></td><td>If you want the schema image to be horizontal</td></tr>
<tr><td>asTable</td><td><code>boolean</code></td><td>Render as a table (true) or sectioned layout (false)</td></tr></table></td></tr>
<tr><th>Output</th><td>ResourceElement</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Generate the documenation
var documentation = System.getModule("com.broadcom.pso.vro.rest.documentation").generateWorkflowDocumentation(
    workflow.id,
    type,
    null,
    horizontal,
    asTable
);

// Use Workflow Version for Documentation Version
var version = workflow.version;

// Setup the file name
var fileName = workflow.name.replace(/ /g, '_') + '.' + (type.toLocaleLowerCase() == 'markdown' ? 'md' : 'html');
var svgName = workflow.name.replace(/ /g, '_') + '.svg';

// Create the resource
var resourceElement = System.getModule("com.broadcom.pso.vro.resource").getOrCreateResourceElement(
    'Documentation/Workflow/' + workflow.workflowCategory.path,
    fileName
);

// Update type and version to be tracked in git
System.getModule("com.broadcom.pso.vro.resource").updateResourceElementByMimeAttachement(
    resourceElement,
    documentation,
    'text/html'
);
System.getModule("com.broadcom.pso.vro.rest.resource").updateResource(
    System.getObjectId(resourceElement),
    resourceElement.name,
    resourceElement.description,
    System.getObjectId(resourceElement.getResourceElementCategory()),
    version
);

// Generate the Schema image and save as a resource
if (type == 'markdown') {
    var svgFile = System.getModule("com.broadcom.pso.vro.rest.workflow").generateWorkflowSchema(
        workflow.id,
        horizontal
    );

    var svgResourceElement = System.getModule("com.broadcom.pso.vro.resource").getOrCreateResourceElement(
        'Documentation/Workflow/' + workflow.workflowCategory.path,
        svgName
    );
    System.getModule("com.broadcom.pso.vro.resource").updateResourceElementByMimeAttachement(
        svgResourceElement,
        svgFile,
        'image/svg+xml'
    );
    System.getModule("com.broadcom.pso.vro.rest.resource").updateResource(
        System.getObjectId(svgResourceElement),
        svgResourceElement.name,
        svgResourceElement.description,
        System.getObjectId(svgResourceElement.getResourceElementCategory()),
        version
    );
}

return resourceElement
```

</td></tr>
</table><br><table><tr><th>Name</th><td>generateWorkflowDocumentation</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.documentation</td></tr>
<tr><th>ID</th><td>01b36113-3fe1-4ce6-9d51-a06dd0e852d4</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>workflowId</td><td><code>string</code></td><td>Workflow ID</td></tr>
<tr><td>type</td><td><code>string</code></td><td>Output type: "html" or "markdown"</td></tr>
<tr><td>author</td><td><code>string</code></td><td>(Optional) Author</td></tr>
<tr><td>horizontal</td><td><code>boolean</code></td><td>If you want the schema image to be horizontal</td></tr>
<tr><td>asTable</td><td><code>boolean</code></td><td>Render as a table (true) or sectioned layout (false)</td></tr></table></td></tr>
<tr><th>Output</th><td>string</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript

var workflow = Server.getWorkflowWithId(workflowId);
if (!workflow) {
    throw "Workflow not found with the provided ID: " + workflowId;
}

var workflowObject = System.getModule("com.broadcom.pso.vro.rest.workflow").getWorkflowContent(workflowId);
workflowObject = System.getModule("com.broadcom.pso.vro.rest.documentation.util").enrichWorkflowItems(workflowObject, workflow.items);

var renderedSteps = [];
var workflowLinks = [];
var visited = {};

walk(workflowObject['root-name'], "Main", type);

if (workflowObject['error-handler']) {
    workflowObject['error-handler'].forEach(function (e) {
        walk(e.name, 'Error Handler', type);
    });
}

var renderCtx = {
    workflow: workflow,
    usages: System.getModule("com.broadcom.pso.vro.rest.workflow").getWorkflowUsages(workflowId),
    dependencies: System.getModule("com.broadcom.pso.vro.rest.workflow").getWorkflowDependencies(workflowId),
    author: author,
    type: type,
    steps: renderedSteps.join('\n'),
    navLinks: workflowLinks.join('\n'),
    diagram: ((type === 'markdown')
        ? ""
        : System.getModule("com.broadcom.pso.vro.rest.workflow").generateWorkflowSchema(workflowId, horizontal)
    )
};

var html = (type === "markdown")
    ? System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderMarkdownDoc(renderCtx)
    : System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderHtmlDoc(renderCtx);

System.log("Generated documentation for workflow: " + workflow.name);
return html;


//*************************FUNCTIONS*************************

function walk(itemName, pathLabel, formatType) {
    if (visited[itemName]) return;
    visited[itemName] = true;
    var item = findItemByName(itemName, workflowObject);
    if (!item) return;

    var html = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderWorkflowStep(item, pathLabel, formatType, asTable);
    renderedSteps.push(html.section);
    workflowLinks.push(html.link);

    // Branching logic
    var type = item.type;
    if (type === 'condition' || type === 'custom-condition' || type === 'decision-activity') {
        if (item['out-name']) walk(item['out-name'], "True (" + item['display-name'] + ")", formatType);
        if (item['alt-out-name']) walk(item['alt-out-name'], "False (" + item['display-name'] + ")", formatType);
    } else if (type === 'switch') {
        (item.condition || []).forEach(function (c) {
            walk(c.label, c.value || pathLabel, formatType);
        });
    } else {
        if (item['out-name']) walk(item['out-name'], pathLabel, formatType);
        if (item['catch-name']) walk(item['catch-name'], "Catch", formatType);
    }
}

function findItemByName(name, apiData) {
    var items = apiData["workflow-item"];
    if (!items || !(items instanceof Array)) return null;
    for (var i = 0; i < items.length; i++) {
        if (items[i].name === name) return items[i];
    }
    return null;
}
```

</td></tr>
</table><br><table><tr><th>Name</th><td>getWorkflowContent</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.workflow</td></tr>
<tr><th>ID</th><td>11f43dd2-ee16-462c-80ce-df01e1ff7251</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>workflowId</td><td><code>string</code></td><td>Workflow ID</td></tr>
<tr><td>query</td><td><code>string</code></td><td>(Optional) Additional Parameters</td></tr>
<tr><td>apiVersion</td><td><code>string</code></td><td>(Optional) Override the default API Version</td></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Use API Version if passed, else set API Version
apiVersion = apiVersion ? apiVersion : '2021-07-15'

// Build API Call
var path = '/api/workflows/' + workflowId + '/content/';
var query = encodeURI('?apiVersion=' + apiVersion + (query ? '&' + query : ''))
var url = path + query

// Execute API call and return results
return System.getModule("com.broadcom.pso.vro.rest.methods").get(url);
```

</td></tr>
</table><br><table><tr><th>Name</th><td>get</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.methods</td></tr>
<tr><th>ID</th><td>da340f7f-7476-4199-a61d-39118da3df9b</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>url</td><td><code>string</code></td><td>URL</td></tr>
<tr><td>headers</td><td><code>Properties</code></td><td>(Optional) Headers</td></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Set method
var method = 'GET';

// If headers is supplied, use headers else generate an empty property
headers = headers ? headers : new Properties();

// Return the Results
return System.getModule("com.broadcom.pso.vro.rest.methods").restOperation(method, url, null, headers);
```

</td></tr>
</table><br><table><tr><th>Name</th><td>restOperation</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.methods</td></tr>
<tr><th>ID</th><td>fe2b6be2-7f09-4877-b915-cee0c5c714c4</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>method</td><td><code>string</code></td><td>Method</td></tr>
<tr><td>url</td><td><code>string</code></td><td>URL</td></tr>
<tr><td>content</td><td><code>string</code></td><td>Content</td></tr>
<tr><td>headers</td><td><code>Properties</code></td><td>(Optional) Headers</td></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
try {
    // Get vRO URL and token
    var connectionDetails = System.getModule("com.broadcom.pso.vro.rest.methods").getConnection();
    var vroUrl = connectionDetails.get("vcoUrl");
    var token = connectionDetails.get("token");

    if (!vroUrl || !token) {
        throw "Missing vRO URL or token from connectionDetails.";
    }

    // Create transient REST host
    var restHost = RESTHostManager.createHost("DynamicVroHost");
    var transientHost = RESTHostManager.createTransientHostFrom(restHost);
    transientHost.url = vroUrl;

    // Build request
    var request = transientHost.createRequest(method, url, content);
    request.contentType = "application/json";
    request.setHeader("Accept", "application/json");
    request.setHeader("ContentType", "application/json");
    request.setHeader("Authorization", "Bearer " + token);
    
    // If there is headers, add headers
    if (System.getObjectType(headers) == 'Properties') {
        for (i in headers) {
            request.setHeader(i, headers[i])
        }
    }

    System.log("Executing request to: " + transientHost.url + url);

    // Execute request
    var result = request.execute();

    System.debug(
        "\nURL: " + transientHost.url + url +
        "\nMethod: " + method +
        "\nStatus: " + result.statusCode +
        "\nResponse: " + result.contentAsString
    );

    if (result.statusCode >= 400) {
        throw "Request failed: " + method + " " + url + " — status: " + result.statusCode + " — content: " + result.contentAsString;
    }

    // Handle empty response
    if (result.contentLength === 0 || !result.contentAsString) {
        return new Properties();
    }

    // Attempt to parse JSON
    var parsed;
    try {
        parsed = JSON.parse(result.contentAsString);
    } catch (e) {
        System.log("Non-JSON response. Returning raw content.");
        return {
            headers: result.getAllHeaders(),
            content: result.contentAsString
        };
    }

    // Return based on parsed type
    if (parsed instanceof Array) {
        return {
            content: parsed
        };
    } else if (parsed instanceof Object) {
        return parsed;
    } else {
        return {
            content: parsed
        };
    }

} catch (e) {
    throw "Unable to execute REST request: " + e;
}
```

</td></tr>
</table><br><table><tr><th>Name</th><td>getConnection</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.methods</td></tr>
<tr><th>ID</th><td>ec721a53-6b8d-4a78-8459-b185c29b1a10</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Initiate CacheManager
var DynamicTypesCacheManager = new (System.getModule("com.broadcom.pso.vro.dynamicTypesCacheManager").DynamicTypesCacheManager());

// Get User
var user = Server.getRunningUser();

// See if the connection is cached
var connectionDetails = DynamicTypesCacheManager.get(user);

// If no cache, get connection details
if (!connectionDetails) {
    var connectionDetails = System.getModule("com.broadcom.pso.vro.rest.methods").getLocalConnectionDetails();

    // Cache for 30 minutes
    DynamicTypesCacheManager.put(user, connectionDetails, .5);
}

return connectionDetails
```

</td></tr>
</table><br><table><tr><th>Name</th><td>DynamicTypesCacheManager</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.dynamicTypesCacheManager</td></tr>
<tr><th>ID</th><td>c2afab18-ae2a-4246-9710-97c64c935fee</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>Constructor function for a cache manager utilizing DynamicTypesManager with expiration.</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr></table></td></tr>
<tr><th>Output</th><td>Any</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
/**
 * @function DynamicTypesCacheManager
 * @description Constructor function for a cache manager utilizing DynamicTypesManager with expiration.
 * @return {DynamicTypesCacheManager} An instance of DynamicTypesCacheManager.
 */
function DynamicTypesCacheManager() {
    // No instance-specific properties needed for this implementation,
    // as it primarily wraps static calls to DynamicTypesManager.
    // However, this structure allows for future instance-specific state if required.
}

/**
 * Puts an item into the cache with a calculated expiration time.
 * @param {string} key The key under which to store the value.
 * @param {Object} value The object to be cached.
 * @param {number} hours The number of hours until the cached item expires. Must be non-negative.
 * @returns {boolean} True if the item was successfully put in cache, false otherwise.
 */
DynamicTypesCacheManager.prototype.put = function(key, value, hours) {
    if (!key || typeof key !== 'string') {
        System.error("Cache key must be a non-empty string.");
        return false;
    }
    if (typeof hours !== 'number' || hours < 0) { 
        System.error("Hours must be a non-negative number.");
        return false;
    }

    try {
        var now = new Date();
        var expiryTimeMs = now.getTime() + (hours * 60 * 60 * 1000); 

        var cachedItem = {
            value: value,
            expiry: expiryTimeMs,
            putTime: now.getTime() // Optional: timestamp when item was put in cache
        };

        DynamicTypesManager.putInCache(key, cachedItem);
        System.log("Successfully put item with key '" + key + "' into cache for " + hours + " hours. Expires: " + new Date(expiryTimeMs).toISOString());
        return true;
    } catch (e) {
        System.error("Error putting item in cache for key '" + key + "': " + e);
        return false;
    }
};

/**
 * Retrieves an item from the cache. Checks for expiration and removes the item if expired.
 * @param {string} key The key of the item to retrieve.
 * @returns {Object | null} The cached object if found and not expired, otherwise null.
 */
DynamicTypesCacheManager.prototype.get = function(key) {
    if (!key || typeof key !== 'string') {
        System.error("Cache key must be a non-empty string.");
        return null;
    }

    try {
        var cachedItem = DynamicTypesManager.getFromCache(key);

        if (cachedItem === null || typeof cachedItem === 'undefined') {
            System.log("Item with key '" + key + "' not found in cache.");
            return null;
        }

        if (typeof cachedItem.expiry !== 'number' || typeof cachedItem.value === 'undefined') {
            System.warn("Cached item for key '" + key + "' has an unexpected structure or is a raw value. Returning it as is and not applying expiration logic.");
            return (typeof cachedItem.value !== 'undefined') ? cachedItem.value : cachedItem;
        }

        var now = new Date().getTime(); 
        var isExpired = now > cachedItem.expiry;

        if (isExpired) {
            System.log("Item with key '" + key + "' found but is expired. Removing from cache.");
            DynamicTypesManager.removeFromCache(key);
            return null;
        } else {
            System.log("Item with key '" + key + "' found and is valid. Expires in: " + ((cachedItem.expiry - now) / 1000 / 60).toFixed(2) + " minutes.");
            return cachedItem.value;
        }
    } catch (e) {
        System.error("Error getting item from cache for key '" + key + "': " + e);
        return null;
    }
};

/**
 * Removes an item from the cache, regardless of its expiration status.
 * @param {string} key The key of the item to remove.
 * @returns {boolean} True if the item was successfully removed, false otherwise.
 */
DynamicTypesCacheManager.prototype.remove = function(key) {
    if (!key || typeof key !== 'string') {
        System.error("Cache key must be a non-empty string.");
        return false;
    }
    try {
        var success = DynamicTypesManager.removeFromCache(key);
        if (success) {
            System.log("Successfully removed item with key '" + key + "' from cache.");
        } else {
            System.log("Item with key '" + key + "' was not found in cache to remove.");
        }
        return success;
    } catch (e) {
        System.error("Error removing item from cache for key '" + key + "': " + e);
        return false;
    }
};

/**
 * Retrieves all valid (non-expired) items from the cache as an array of {key: string, value: Object} pairs.
 * Expired items will be removed during this process.
 * @returns {Array<Object>} An array where each object has 'key' and 'value' properties for valid cached items.
 */
DynamicTypesCacheManager.prototype.getAll = function() {
    var allKeys = DynamicTypesManager.getCacheKeys(); 
    var validItemsArray = []; 

    if (!allKeys || allKeys.length === 0) {
        System.log("Cache is empty. No items to retrieve.");
        return validItemsArray;
    }

    System.log("Attempting to retrieve all items from cache. Total keys found: " + allKeys.length);

    for (var i = 0; i < allKeys.length; i++) {
        var key = allKeys[i];
        try {
            // Use the instance's get method to handle expiration check and removal
            var itemValue = this.get(key); 
            if (itemValue !== null) {
                validItemsArray.push({ key: key, value: itemValue }); 
                System.log("Key '" + key + "' is valid and added to results.");
            } else {
                System.log("Key '" + key + "' was either not found or expired and removed.");
            }
        } catch (e) {
            System.error("Error processing key '" + key + "' in getAll: " + e);
        }
    }
    System.log("Finished retrieving all valid items. Count: " + validItemsArray.length);
    return validItemsArray;
};

/**
 * Clears all items from the DynamicTypesManager cache.
 * @returns {boolean} True if the cache was successfully cleared, false otherwise.
 */
DynamicTypesCacheManager.prototype.clearCache = function() {
    var allKeys = DynamicTypesManager.getCacheKeys();
    if (!allKeys || allKeys.length === 0) {
        System.log("Cache is already empty. Nothing to clear.");
        return true;
    }

    System.log("Attempting to clear cache. Found " + allKeys.length + " items to remove.");
    try {
        for (var i = 0; i < allKeys.length; i++) {
            var key = allKeys[i];
            this.remove(key);
            System.log("Removed key: '" + key + "'");
        }
        System.log("Cache cleared successfully.");
        return true;
    } catch (e) {
        System.error("Error clearing cache: " + e);
        return false;
    }
};

// Return the constructor function itself
return DynamicTypesCacheManager;
```

</td></tr>
</table><br><table><tr><th>Name</th><td>getLocalConnectionDetails</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.methods</td></tr>
<tr><th>ID</th><td>68d878f0-2e32-4b25-9934-3a8b960a0e29</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>python:3.10</td></tr>
<tr><th>Script</th><td class='script'>

```python
def handler(context, inputs):
    outputs = {}
    outputs['vcoUrl'] = context['vcoUrl']
    outputs['token'] = context['getToken']()
    return outputs
```

</td></tr>
</table><br><table><tr><th>Name</th><td>enrichWorkflowItems</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.documentation.util</td></tr>
<tr><th>ID</th><td>e4f7623c-7048-443f-8826-fd8a4c805cea</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>apiData</td><td><code>Properties</code></td><td>API Data</td></tr>
<tr><td>workflowItems</td><td><code>Array/Any</code></td><td>Workflow Items</td></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Mapping vRO WorkflowItem types to API type strings
var typeMapping = {
    "WorkflowTaskItem": "task",
    "WorkflowEndItem": "end",
    "WorkflowLinkItem": "link",
    "WorkflowCustomConditionItem": "custom-condition",
    "WorkflowGenericConditionItem": "condition",
    "WorkflowSwitchItem": "switch",
    "WorkflowForeachItem": "foreach",
    "WorkflowMultipleCallItem": "multiple",
    "WorkflowItemWaitingTimer": "waiting-timer"
};

// Main loop through each API workflow item
for (var k = 0; k < apiData['workflow-item'].length; k++) {
    var apiItem = apiData['workflow-item'][k];

    // Iterate over vRO workflowItems to find a matching item
    for (var i = 0; i < workflowItems.length; i++) {
        var workflowItem = workflowItems[i];

        // Get the inferred type based on the WorkflowItem's constructor name
        var inferredType = typeMapping[workflowItem.constructor.name];

        // Match on display-name and type to ensure accurate mapping
        if (workflowItem.name === apiItem['display-name'] && inferredType === apiItem.type) {
            // Handle WorkflowSwitchItems, WorkflowCustomConditionItems, and WorkflowGenericConditionItems
            if ((workflowItem.constructor.name === "WorkflowSwitchItem" && apiItem.type === "switch") ||
                ((workflowItem.constructor.name === "WorkflowCustomConditionItem" && apiItem.type === "custom-condition" || workflowItem.constructor.name === "WorkflowGenericConditionItem") && apiItem.type === "condition")) {

                if (workflowItem.constructor.name === "WorkflowSwitchItem") {
                    if (allOutItemsMatch(apiItem.condition, workflowItem.outItems)) {
                        apiItem['item'] = workflowItem; // Assign switch only if outItems match
                    }
                } else {
                    if (conditionMatches(apiItem, workflowItem)) {
                        apiItem['item'] = workflowItem; // Assign condition only if true/false paths match
                    }
                }

            } else {
                // For other item types, assign the vRO WorkflowItem directly
                apiItem['item'] = workflowItem
            }
            break; // Move to the next API item once a match is found
        }
    }
}

return apiData; // Return the enriched API data with added workflow item details

// Helper function to find the display-name for an item based on its unique name (e.g., "item3")
function findDisplayNameByUniqueName(uniqueName, apiData) {
    for (var j = 0; j < apiData['workflow-item'].length; j++) {
        var item = apiData['workflow-item'][j];
        if (item.name === uniqueName) {
            return item['display-name'];
        }
    }
    return null;
}

// Function to check if nextItemTrue and nextItemFalse match API out-name and alt-out-name
function conditionMatches(apiItem, workflowConditionItem) {
    var nextTrueName = workflowConditionItem.nextItemTrue ? workflowConditionItem.nextItemTrue.name : null;
    var nextFalseName = workflowConditionItem.nextItemFalse ? workflowConditionItem.nextItemFalse.name : null;

    var expectedTrueName = findDisplayNameByUniqueName(apiItem['out-name'], apiData);
    var expectedFalseName = findDisplayNameByUniqueName(apiItem['alt-out-name'], apiData);

    return (nextTrueName === expectedTrueName) && (nextFalseName === expectedFalseName);
}

// Function to check if all outItems match the API condition labels for switches
function allOutItemsMatch(apiConditions, workflowOutItems) {
    if (apiConditions.length !== workflowOutItems.length) {
        return false;
    }

    for (var i = 0; i < apiConditions.length; i++) {
        var conditionLabel = apiConditions[i].label;
        var expectedDisplayName = findDisplayNameByUniqueName(conditionLabel, apiData);

        if (expectedDisplayName !== workflowOutItems[i].name) {
            return false; // Exit if any label does not match
        }
    }

    return true; // Return true only if all items match
}
```

</td></tr>
</table><br><table><tr><th>Name</th><td>getWorkflowUsages</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.workflow</td></tr>
<tr><th>ID</th><td>a0055e02-9260-4e84-999e-ca00377c68d6</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>workflowId</td><td><code>string</code></td><td>Workflow ID</td></tr>
<tr><td>query</td><td><code>string</code></td><td>(Optional) Additional Parameters</td></tr>
<tr><td>apiVersion</td><td><code>string</code></td><td>(Optional) Override the default API Version</td></tr></table></td></tr>
<tr><th>Output</th><td>Array/Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Use API Version if passed, else set API Version
apiVersion = apiVersion ? apiVersion : '2021-07-15'

// Build API Call
var path = '/api/workflows/' + workflowId + '/usages';
var query = encodeURI('?apiVersion=' + apiVersion + (query ? '&' + query : ''))
var url = path + query

// Execute API call and return results
var results = System.getModule("com.broadcom.pso.vro.rest.methods").get(url);

// Convert Reference to a single Array object
return System.getModule("com.broadcom.pso.vro.util").convertNestedReferences(results);
```

</td></tr>
</table><br><table><tr><th>Name</th><td>convertNestedReferences</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.util</td></tr>
<tr><th>ID</th><td>6ea2bfae-304a-4fb2-90fa-399fd7829432</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>referenceObject</td><td><code>Properties</code></td><td>API Reference Object</td></tr></table></td></tr>
<tr><th>Output</th><td>Array/Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Convert nested 'references' structure to a flat array of Properties
var result = [];

// Get the 'references' array from the input object
var references = referenceObject['references'];

for (var i = 0; i < references.length; i++) {
    var ref = references[i].reference;
    
    var prop = new Properties();
    for (var key in ref) {
        if (ref.hasOwnProperty(key)) {
            prop.put(key, ref[key]);
        }
    }
    
    result.push(prop);
}

return result;

```

</td></tr>
</table><br><table><tr><th>Name</th><td>getWorkflowDependencies</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.workflow</td></tr>
<tr><th>ID</th><td>022d7341-fea8-40da-bb59-f900d920fa49</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>workflowId</td><td><code>string</code></td><td>Workflow ID</td></tr>
<tr><td>query</td><td><code>string</code></td><td>(Optional) Additional Parameters</td></tr>
<tr><td>apiVersion</td><td><code>string</code></td><td>(Optional) Override the default API Version</td></tr></table></td></tr>
<tr><th>Output</th><td>Array/Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Use API Version if passed, else set API Version
apiVersion = apiVersion ? apiVersion : '2021-07-15'

// Build API Call
var path = '/api/workflows/' + workflowId + '/dependencies';
var query = encodeURI('?apiVersion=' + apiVersion + (query ? '&' + query : ''))
var url = path + query

// Execute API call and return results
var results = System.getModule("com.broadcom.pso.vro.rest.methods").get(url);

// Convert Reference to a single Array object
return System.getModule("com.broadcom.pso.vro.util").convertNestedReferences(results);
```

</td></tr>
</table><br><table><tr><th>Name</th><td>generateWorkflowSchema</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.workflow</td></tr>
<tr><th>ID</th><td>2b3cf51c-4e50-4433-9ed3-483da8f091af</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>This is used to generate the Schema SVG Diagram for a workflow</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>workflowId</td><td><code>string</code></td><td>Workflow ID</td></tr>
<tr><td>horizontal</td><td><code>boolean</code></td><td>If you want the image to be horizontal</td></tr></table></td></tr>
<tr><th>Output</th><td>string</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Get Workflow in GraphViz
var dotGraph = System.getModule("com.broadcom.pso.vro.rest.workflow").generateDotGraphFromWorkflow(workflowId, horizontal);

// Get Icon Json
var icons = System.getModule("com.broadcom.pso.vro.resource").getOrCreateResourceElement('Documentation/Config', 'icon.json').getContentAsMimeAttachment().content;

// Render Dot graph to SVG with Icons
var svg = System.getModule("com.broadcom.pso.graphviz").renderGraphvizDot(dotGraph);
return System.getModule("com.broadcom.pso.graphviz").postProcessGraphSvgWithIcons(svg, icons);
```

</td></tr>
</table><br><table><tr><th>Name</th><td>generateDotGraphFromWorkflow</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.workflow</td></tr>
<tr><th>ID</th><td>7f201ef7-3753-413d-b146-fede586bf369</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>Generates a Graphviz DOT string representing the workflow structure, with styling from a resource element.</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>workflowId</td><td><code>string</code></td><td>Workflow ID</td></tr>
<tr><td>horizontal</td><td><code>boolean</code></td><td>If you want the graph to be horizontal</td></tr></table></td></tr>
<tr><th>Output</th><td>string</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// --- Configuration & Initialization ---
var workflowContent = System.getModule("com.broadcom.pso.vro.rest.workflow").getWorkflowContent(workflowId);

if (!workflowContent) {
    throw new Error("Workflow content not found for ID: " + workflowId);
}

var styleMap;
try {
    var styleResource = System.getModule("com.broadcom.pso.vro.resource").getOrCreateResourceElement('Documentation/Config', 'workflow-style.json');
    if (!styleResource || !styleResource.getContentAsMimeAttachment()) {
        throw new Error("workflow-style.json resource element not found or is empty.");
    }
    styleMap = JSON.parse(styleResource.getContentAsMimeAttachment().content);
} catch (e) {
    System.error("Failed to load or parse workflow-style.json: " + e.message);
    throw new Error("Failed to load workflow styling: " + e.message);
}

var dotGraphLines = [];
var dotEdges = []; // Collect edges separately to append at the end

// --- Graph Header - General Graph, Node, and Edge Defaults ---
dotGraphLines.push('digraph WorkflowGraph {');
dotGraphLines.push('    graph [bgcolor="none", fontname="Calibri", compound="true", nodesep=1, fontcolor="#6a7a81"]; ' + (horizontal ? 'rankdir="LR";' : ''));
dotGraphLines.push('    node [fontname="Calibri", penwidth="2", color="#6a7a81"];');
dotGraphLines.push('    edge [fontname="Calibri", color="#0079ad", penwidth=1.6, arrowsize=.8, headclip="false", minlen=2, fontcolor="#6a7a81"];');

// --- Process Start Node ---
// The original `addSubgraphItem` adds the node, its subgraph, AND its primary outgoing edge.
// We'll rename it to be more descriptive of its role.
processNodeAndPrimaryEdge(
    'workflow_start', // Subgraph name
    'start',          // Node name
    workflowContent["root-name"], // Primary link target
    { type: 'start', position: workflowContent.position, 'display-name': 'Start' }, // Item object (ensure type is set)
    dotGraphLines,
    dotEdges,
    styleMap
);

// --- Process Error Handler Node (if present) ---
if (workflowContent.hasOwnProperty('error-handler') && workflowContent['error-handler'].length > 0) {
    var errorHandlerItem = workflowContent['error-handler'][0];
    if (!errorHandlerItem.type) {
        errorHandlerItem.type = 'error-handler'; // Assign the correct type for consistent processing
    }
    if (!errorHandlerItem['display-name']) {
        errorHandlerItem['display-name'] = "Error Handler"
    }
    processNodeAndPrimaryEdge(
        'error_handler',       // Subgraph name
        'errorHandler',        // Node name
        errorHandlerItem['name'], // Primary link target
        errorHandlerItem,      // Pass the potentially modified item
        dotGraphLines,
        dotEdges,
        styleMap
    );
}

// --- Process all other Workflow Items ---
var items = workflowContent["workflow-item"];
for (var i = 0; i < items.length; i++) {
    var item = items[i];

    // Render the node and its subgraph. Regular workflow items don't have a single 'linkTarget'
    // in the same way start/errorHandler do, so we pass null/undefined for it here.
    processNodeAndPrimaryEdge(
        item.name, // Subgraph name (same as item name for regular items)
        item.name, // Node name
        null,      // No primary link target for general items (edges handled below)
        item,      // The workflow item object
        dotGraphLines,
        dotEdges,
        styleMap
    );

    // Add secondary edges (alt-out, catch, switch) for the current item
    addSecondaryEdgesForItem(item, dotEdges);
}

// --- Append all collected edges ---
for (var j = 0; j < dotEdges.length; j++) {
    dotGraphLines.push(dotEdges[j]);
}

// --- Graph Footer ---
dotGraphLines.push('}');

var finalDotGraph = dotGraphLines.join('\n');
System.debug(finalDotGraph);
return finalDotGraph;


// -----------------------------------------------------------
// --- Helper Functions ---
// -----------------------------------------------------------

/**
 * Determines the unique ID for a node based on its type and properties.
 * @param {Object} item The workflow item object.
 * @returns {string} The computed node ID.
 */
function getNodeId(item) {
    var type = item.type;
    var script = (item.script && item.script.value) ? item.script.value : "";
    var prototypeId = item["prototype-id"] || "";
    var scriptModule = item["script-module"] || "";

    if (type === "end") {
        if (item["end-mode"] !== undefined) {
            if (item["end-mode"] === "0") return "end";
            if (item["end-mode"] === "1") return "exception";
        }
    }
    if (script.indexOf("workflowToLaunch.schedule") !== -1) return "workflow-schedule";
    if (script.indexOf("workflowToLaunch.execute") !== -1) return "workflow-async";
    if (prototypeId) return prototypeId;
    if (scriptModule) return "scripting-element";
    if (type === "start") return "start";
    if (type === "error-handler" || type === "error-item") return "error-handler";

    // Fallback to the general item type
    return type;
}

/**
 * Retrieves the style object for a given workflow item based on its type and end-mode.
 * @param {Object} item The workflow item object.
 * @param {Object} styleMap The loaded style map.
 * @returns {Object} The style object (can be empty if no specific style).
 */
function getItemStyle(item, styleMap) {
    var type = item.type;
    var style;

    if (type === "start") {
        style = styleMap["start"];
    } else if (type === "end" && item["end-mode"] !== undefined) {
        style = styleMap["end"][item["end-mode"]] || styleMap["end"];
    } else if (type === "error-handler" || type === "error-item") {
        style = styleMap["error-handler"];
    } else {
        style = styleMap["default"];
    }
    return style || {}; // Ensure style is always an object
}

/**
 * Formats an object of attributes into a comma-separated string suitable for Node definitions in DOT.
 * Handles HTML-like labels by not quoting them.
 * @param {Object} attributes Object containing key-value pairs.
 * @returns {string} Formatted attribute string.
 */
function formatNodeAttributes(attributes) {
    var props = [];
    for (var key in attributes) {
        if (attributes.hasOwnProperty(key)) {
            var value = attributes[key];
            if (key === "label" && typeof value === "string" && value.trim().charAt(0) === "<") {
                // HTML-like label should not be quoted
                props.push(key + '=' + value);
            } else {
                // All other values should be quoted
                props.push(key + '="' + value + '"');
            }
        }
    }
    return props.join(', ');
}

/**
 * Processes a single workflow item, generating its subgraph, node, and its primary outgoing edge.
 * This function closely mimics the original `addSubgraphItem` behavior.
 *
 * @param {string} subgraphName The name for the cluster subgraph (e.g., 'workflow_start' or item.name).
 * @param {string} nodeName The identifier for the node within the subgraph (e.g., 'start' or item.name).
 * @param {string|null} primaryLinkTarget The name of the target node for the primary outgoing edge (e.g., workflow's root-name for 'start').
 * @param {Object} itemObject The full workflow item object.
 * @param {string[]} outputArray The array to push DOT lines for nodes/subgraphs.
 * @param {string[]} edgeArray The array to push DOT lines for edges.
 * @param {Object} styleMap The loaded style map.
 */
function processNodeAndPrimaryEdge(subgraphName, nodeName, primaryLinkTarget, itemObject, outputArray, edgeArray, styleMap) {
    var nodeId = getNodeId(itemObject);
    var type = itemObject.type; // Use itemObject's type for style lookup
    var label = itemObject["display-name"] || type;
    var tooltip = label;
    var href = "#" + nodeName; // Use nodeName as href target for consistency
    var pos = itemObject.position ? itemObject.position.x + "," + itemObject.position.y : "0,0";

    var style = getItemStyle(itemObject, styleMap); // Get style based on the itemObject

    // --- Subgraph Definition (cluster) - using semicolon-terminated individual attributes ---
    outputArray.push('    subgraph "cluster_' + subgraphName + '" {');

    if (style.subgraph) {
        outputArray.push('        id="' + nodeId + '";'); // Required for icon replacement
        outputArray.push('        href="' + href + '";'); // Link for cluster
        outputArray.push('        tooltip="' + tooltip + '";'); // Tooltip for cluster

        for (var k in style.subgraph) {
            if (style.subgraph.hasOwnProperty(k)) {
                // Avoid duplicating mandatory attributes already pushed by name
                if (k !== "label" && k !== "tooltip" && k !== "href" && k !== "id") {
                    outputArray.push('        ' + k + '="' + style.subgraph[k] + '";');
                }
            }
        }
        // Explicitly handle label from style.subgraph if present, otherwise use default label
        if (style.subgraph.label) {
            outputArray.push('        label="' + style.subgraph.label + '";');
        } else {
            outputArray.push('        label="' + label + '";'); // Default label for subgraph
        }
    } else {
        // If no subgraph style, just ensure mandatory attributes and default label are set
        outputArray.push('        id="' + nodeId + '";');
        outputArray.push('        href="' + href + '";');
        outputArray.push('        tooltip="' + tooltip + '";');
        outputArray.push('        label="' + label + '";');
    }

    // --- Node Definition - using comma-separated attributes in a single block ---
    var nodeAttrs = {};
    if (style.node) {
        for (var k in style.node) {
            if (style.node.hasOwnProperty(k)) {
                nodeAttrs[k] = style.node[k];
            }
        }
    }
    // Always include these mandatory node attributes
    nodeAttrs.id = nodeId; // Required for icon replacement
    nodeAttrs.tooltip = tooltip;
    nodeAttrs.href = href;
    nodeAttrs.pos = pos; // Position from workflow XML

    outputArray.push('        ' + nodeName + ' [' + formatNodeAttributes(nodeAttrs) + '];');
    outputArray.push('    }'); // Close subgraph block

    // --- Primary Edge Addition (mimicking original addSubgraphItem's behavior) ---
    if (primaryLinkTarget) {
        edgeArray.push('    ' + nodeName + ' -> ' + primaryLinkTarget + ' [ltail="cluster_' + subgraphName + '", lhead="cluster_' + primaryLinkTarget + '"];');
    }
}

/**
 * Adds "secondary" outgoing edges (alt-out, catch, switch conditions) for a given workflow item.
 * This separates concerns from the primary node/subgraph/main-link rendering.
 * @param {Object} itemObject The workflow item object.
 * @param {string[]} edgeArray The array to push DOT lines for edges.
 */
function addSecondaryEdgesForItem(itemObject, edgeArray) {
    var name = itemObject.name; // Source node name
    var type = itemObject.type;
    var currentCluster = 'cluster_' + name; // Source cluster name

    // Regular 'out-name' (non-custom-condition) is handled by processNodeAndPrimaryEdge for general items
    // as the 'primaryLinkTarget' would be null. So we need to handle it here for general items.
    // However, the original code had this logic separate. Let's replicate original carefully:
    if (itemObject["out-name"]) {
        var targetCluster = 'cluster_' + itemObject["out-name"];
        if (type === "custom-condition") {
            // Specific edge for custom-condition's out-name
            edgeArray.push('    ' + name + ' -> ' + itemObject["out-name"] + ' [color="#41800e", ltail="' + currentCluster + '", lhead="' + targetCluster + '"];');
        } else if (type !== "start" && type !== "error-handler") { // Only for regular items, as start/error-handler handled by processNodeAndPrimaryEdge
            edgeArray.push('    ' + name + ' -> ' + itemObject["out-name"] + ' [ltail="' + currentCluster + '", lhead="' + targetCluster + '"];');
        }
    }

    if (itemObject["alt-out-name"]) {
        var targetCluster = 'cluster_' + itemObject["alt-out-name"];
        edgeArray.push('    ' + name + ' -> ' + itemObject["alt-out-name"] + ' [color="#e02100", style=dashed, ltail="' + currentCluster + '", lhead="' + targetCluster + '"];');
    }

    if (itemObject["catch-name"]) {
        var targetCluster = 'cluster_' + itemObject["catch-name"];
        edgeArray.push('    ' + name + ' -> ' + itemObject["catch-name"] + ' [color="#e02100", style=dashed, ltail="' + currentCluster + '", lhead="' + targetCluster + '"];');
    }

    if (type === "switch" && itemObject.condition && itemObject.condition.length > 0) {
        for (var c = 0; c < itemObject.condition.length; c++) {
            var labelTarget = itemObject.condition[c].label;
            if (labelTarget) {
                var targetCluster = 'cluster_' + labelTarget;
                edgeArray.push('    ' + name + ' -> ' + labelTarget + ' [ltail="' + currentCluster + '", lhead="' + targetCluster + '"];');
            }
        }
    }
}

```

</td></tr>
</table><br><table><tr><th>Name</th><td>getOrCreateResourceElement</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.resource</td></tr>
<tr><th>ID</th><td>eaece025-db2a-45ac-9ee2-23e96fbd7a42</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>resourceElementCategoryPath</td><td><code>string</code></td><td>Resource Element Category Path</td></tr>
<tr><td>resourceElementName</td><td><code>string</code></td><td>Resource Element Name</td></tr></table></td></tr>
<tr><th>Output</th><td>ResourceElement</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
var resourceElementCategory = Server.getResourceElementCategoryWithPath(resourceElementCategoryPath);

if (!resourceElementCategory) {
    return Server.createResourceElement(resourceElementCategoryPath, resourceElementName, null)
} else {
    for each( var resourceElement in resourceElementCategory.resourceElements) {
        if (resourceElement.name == resourceElementName) {
            return resourceElement
        }
    }
}

return Server.createResourceElement(resourceElementCategoryPath, resourceElementName, null)
```

</td></tr>
</table><br><table><tr><th>Name</th><td>renderGraphvizDot</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.graphviz</td></tr>
<tr><th>ID</th><td>4c462adc-01ab-479f-ab83-aee4c0c17f1e</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>dotSource</td><td><code>string</code></td><td>Graphviz DOT string</td></tr>
<tr><td>outputFormat</td><td><code>string</code></td><td>svg | dot | json | dot_json | xdot_json</td></tr>
<tr><td>layoutEngine</td><td><code>string</code></td><td>circo | dot | fdp | neato | osage | patchwork | twopi</td></tr></table></td></tr>
<tr><th>Output</th><td>string</td></tr>
<tr><th>Runtime Environment</th><td>documentation | node:20</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
exports.handler = async (context, inputs) => {
    const { graphviz } = require("node-graphviz");

    // Validate inputs
    const dot = inputs.dotSource;
    const outputFormat = inputs.outputFormat || "svg"; // Default to SVG
    const layoutEngine = inputs.layoutEngine || "dot"; // Default to DOT layout

    if (!dot) {
        throw new Error("dotSource input is required.");
    }

    try {
        // Render the DOT graph using the specified format and engine
        const svg = await graphviz.layout(dot, outputFormat, layoutEngine);
        return svg;
    } catch (error) {
        throw new Error("Failed to generate output: " + error.message);
    }
};
```

</td></tr>
</table><br><table><tr><th>Name</th><td>postProcessGraphSvgWithIcons</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.graphviz</td></tr>
<tr><th>ID</th><td>010bdbd0-1728-4ac5-b035-77277bca20c2</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>This is used to replace the nodes rectangle to icons</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>graphvizSvgString</td><td><code>string</code></td><td>Graphviz SVG</td></tr>
<tr><td>svgIconsJson</td><td><code>string</code></td><td>Icons JSON</td></tr></table></td></tr>
<tr><th>Output</th><td>string</td></tr>
<tr><th>Runtime Environment</th><td>documentation | node:20</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
exports.handler = (context, inputs, callback) => {
    const { DOMParser, XMLSerializer } = require('xmldom');
    //console.log('Action inputs: ' + JSON.stringify(inputs));

    const graphvizSvgString = inputs.graphvizSvgString;
    const svgIconsJson = inputs.svgIconsJson;

    if (!graphvizSvgString) {
        return callback(new Error('Input "graphvizSvgString" is required.'), undefined);
    }
    if (!svgIconsJson) {
        return callback(new Error('Input "svgIconsJson" is required.'), undefined);
    }

    try {
        console.log("Starting SVG post-processing using xmldom...");

        // 1. Parse icon.json into a map for easy lookup
        const iconMap = {};
        try {
            const iconsArray = JSON.parse(svgIconsJson);
            for (let i = 0; i < iconsArray.length; i++) {
                const icon = iconsArray[i];
                // Normalize icon name to match potential node IDs
                const iconNameWithoutExt = icon.name.replace(/\.svg$/, '');
                iconMap[iconNameWithoutExt] = icon.svg; // Use 'svg' property as per icon.json snippet
            }
            console.log(`Parsed ${iconsArray.length} SVG icons into map.`);
        } catch (e) {
            console.error(`Failed to parse svgIconsJson: ${e.message}`);
            return callback(e, undefined); // Propagate error
        }

        // 2. Parse the Graphviz SVG string into a DOM document
        const parser = new DOMParser();
        const serializer = new XMLSerializer();
        let svgDoc;
        try {
            svgDoc = parser.parseFromString(graphvizSvgString, "image/svg+xml");
            // xmldom does not expose parser errors in the same way as browser DOMParser.
            // You might need to add specific error checking if parsing failures occur.
            // console.log("Graphviz SVG parsed successfully.");
        } catch (e) {
            console.error(`Error parsing Graphviz SVG: ${e.message}`);
            return callback(e, undefined);
        }

        // 3. Select all <g class="node"> elements
        const allGElements = svgDoc.getElementsByTagName('g');
        const nodeElements = [];
        for (let i = 0; i < allGElements.length; i++) {
            const g = allGElements[i];
            if (g.hasAttribute('class') && g.getAttribute('class').split(' ').includes('node')) {
                nodeElements.push(g);
            }
        }
        console.log(`Found ${nodeElements.length} <g class="node"> elements.`);

        nodeElements.forEach(nodeGElement => {
            const nodeId = nodeGElement.getAttribute('id');
            const iconSvgContent = iconMap[nodeId];

            if (!iconSvgContent) {
                console.log(`No custom icon found for node ID: ${nodeId}. Skipping replacement.`);
                return; // Continue to the next node
            }

            console.log(`Processing node ID: ${nodeId}`);

            // Extract the polygon and its coordinates
            // Note: The polygonElement here is just for extracting points, not for direct manipulation
            const polygonElementForPoints = nodeGElement.getElementsByTagName('polygon')[0];
            if (!polygonElementForPoints) {
                console.warn(`Warning: No polygon found within node <g id="${nodeId}"> for points extraction. Skipping.`);
                return;
            }

            const pointsString = polygonElementForPoints.getAttribute('points');
            if (!pointsString) { // Defensive check for missing points string
                console.warn(`Warning: Polygon for node <g id="${nodeId}"> has no 'points' attribute. Skipping.`);
                return;
            }
            //console.debug(`Debug: Node ${nodeId} polygon pointsString: "${pointsString}"`);

            const points = pointsString.split(' ').flatMap(pair => {
                const [x, y] = pair.split(',').map(parseFloat);
                return [x, y];
            });

            //console.debug(`Debug: Node ${nodeId} parsed points: [${points.join(', ')}]`);

            let minX = Infinity, minY = Infinity;
            let maxX = -Infinity, maxY = -Infinity;

            for (let j = 0; j < points.length; j += 2) {
                // Ensure points are numbers before comparison
                if (isNaN(points[j]) || isNaN(points[j + 1])) {
                    console.error(`Error: Non-numeric point found in polygon for node ID: ${nodeId}. Point: (${points[j]}, ${points[j + 1]}). Skipping this node.`);
                    return; // Skip this node if a point is NaN
                }
                minX = Math.min(minX, points[j]);
                minY = Math.min(minY, points[j + 1]); // This is the correct top-most Y coordinate
                maxX = Math.max(maxX, points[j]);
                maxY = Math.max(maxY, points[j + 1]);
            }

            // Parse the custom icon SVG to get its inner content
            let iconDoc;
            try {
                iconDoc = parser.parseFromString(iconSvgContent, "image/svg+xml");
            } catch (e) {
                console.error(`Error parsing icon SVG for ${nodeId}: ${e.message}`);
                return; // Skip this icon
            }

            const iconRootG = iconDoc.getElementsByTagName('svg')[0]?.getElementsByTagName('g')[0];

            if (!iconRootG) {
                console.warn(`Warning: Could not find root <g> in icon SVG for ${nodeId}. Skipping.`);
                return;
            }

            // REVISED: Directly use minX and minY of the polygon as the icon's translate origin
            const iconOffsetX = minX;
            const iconOffsetY = minY;

            if (isNaN(iconOffsetX) || isNaN(iconOffsetY)) {
                console.error(`Error: Calculated icon offset for node ID: ${nodeId} resulted in NaN. iconOffsetX: ${iconOffsetX}, iconOffsetY: ${iconOffsetY}. Skipping this node.`);
                //console.debug(`Debug: minX: ${minX}, minY: ${minY}`);
                return; // Skip this node as its coordinates are invalid
            }

            let newIconElement = iconRootG.cloneNode(true);

            if (newIconElement.nodeType !== newIconElement.ELEMENT_NODE) {
                console.warn(`Cloned icon element for ${nodeId} is not a valid ELEMENT_NODE. Skipping.`);
                return;
            }
            newIconElement.setAttribute('transform', `translate(${iconOffsetX},${iconOffsetY})`);
            //console.log(`New icon element for ${nodeId} created with transform: translate(${iconOffsetX},${iconOffsetY})`);

            // Robustness step: Serialize and re-parse the newIconElement
            try {
                const tempSvgString = serializer.serializeToString(newIconElement);
                const reParsedIconDoc = parser.parseFromString(tempSvgString, "image/svg+xml");
                const reParsedIconElement = reParsedIconDoc.documentElement;

                if (reParsedIconElement) {
                    newIconElement = reParsedIconElement;
                    //console.debug(`Debug: Successfully re-parsed newIconElement for node ${nodeId}.`);
                } else {
                    console.error(`Error: Re-parsing icon element for node ${nodeId} resulted in null/undefined documentElement. Skipping.`);
                    return;
                }
            } catch (e) {
                console.error(`Error re-parsing newIconElement for node ${nodeId}: ${e.message}. Skipping.`);
                return;
            }

            // --- REVISED DOM MANIPULATION: Handle cases where polygon is direct child or inside <a> ---
            let parentForReplacement = nodeGElement; // Default to nodeGElement as parent
            let existingPolygonToReplace = null;

            // First, try to find an <a> element as the parent for the polygon
            const aElement = nodeGElement.getElementsByTagName('a')[0];

            if (aElement) {
                parentForReplacement = aElement;
                //console.debug(`Debug: Found <a> element for node ${nodeId}. Will use it as parent for replacement.`);
            } else {
                //console.debug(`Debug: No <a> element found for node ${nodeId}. Will look for polygon directly under <g class="node">.`);
            }

            // Find the polygon within the determined parent
            existingPolygonToReplace = parentForReplacement.getElementsByTagName('polygon')[0];

            if (existingPolygonToReplace) {
                try {
                    // Replace the existing polygon with the new icon element
                    parentForReplacement.replaceChild(newIconElement, existingPolygonToReplace);
                    console.log(`Replaced polygon with icon for node: ${nodeId}`);
                } catch (e) {
                    console.error(`Error replacing polygon for node ${nodeId}: ${e.message}. Attempting remove/append as fallback.`);
                    // Fallback to removeChild/appendChild if replaceChild fails
                    try {
                        parentForReplacement.removeChild(existingPolygonToReplace);
                        parentForReplacement.appendChild(newIconElement);
                        console.log(`Successfully replaced polygon with icon using remove/append fallback for node: ${nodeId}`);
                    } catch (eFallback) {
                        console.error(`Error in remove/append fallback for node ${nodeId}: ${eFallback.message}. Skipping this node.`);
                        if (eFallback.stack) console.error(eFallback.stack);
                        return;
                    }
                }
            } else {
                console.warn(`Warning: No polygon found within the determined parent for node <g id="${nodeId}">. Appending icon without replacing existing polygon.`);
                // If no polygon to replace, just append the icon
                try {
                    parentForReplacement.appendChild(newIconElement);
                    console.log(`Appended icon to parent as no polygon was found for node: ${nodeId}`);
                } catch (eAppend) {
                    console.error(`Error appending icon to parent for node ${nodeId}: ${eAppend.message}. Skipping this node.`);
                    if (eAppend.stack) console.error(eAppend.stack);
                    return;
                }
            }
            // ------------------------------------------------------------------------------------------

            // Consider if the text label should also be removed/replaced.
            // For now, only the polygon is handled as per the current request.
            // If the icon should completely replace the node's visual,
            // the text element (usually inside a <g id="a_..."> within <a>)
            // would also need to be removed.

        }); // End of forEach loop

        // 4. Serialize the modified SVG DOM back to a string
        if (!svgDoc || !svgDoc.documentElement) {
            console.error("SVG document is empty or invalid before final serialization.");
            return callback(new Error("Modified SVG document is empty or invalid after processing."), undefined);
        }

        const finalSvgString = serializer.serializeToString(svgDoc);
        console.log("SVG post-processing complete. Returning modified SVG string.");

        // Return the processed SVG string via the callback
        callback(undefined, finalSvgString);

    } catch (e) {
        console.error(`An unexpected error occurred during SVG processing: ${e.message}`);
        // Log the full stack trace for better debugging
        if (e.stack) {
            console.error(e.stack);
        }
        // Return error via callback
        callback(e, undefined);
    }
};
```

</td></tr>
</table><br><table><tr><th>Name</th><td>renderMarkdownDoc</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.documentation.util</td></tr>
<tr><th>ID</th><td>0c584244-6202-4a51-9d6f-5d68cb348523</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>ctx</td><td><code>string</code></td><td>Documentation context (workflow, navLinks, diagram, steps)</td></tr></table></td></tr>
<tr><th>Output</th><td>string</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
var inputHtml = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderNamedList("Inputs", ctx.workflow.inParameters, true);
var outputHtml = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderNamedList("Outputs", ctx.workflow.outParameters, true);
var attrHtml = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderNamedList("Attributes (Variables)", ctx.workflow.attributes, true, true);
var usagesHtml = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderReferenceList("Usages", ctx.usages, true);
var dependenciesHtml = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderReferenceList("Dependencies", ctx.dependencies, true);

var md = "";

md += "# Workflow Documentation - " + ctx.workflow.name + "\n\n";

md += "## Workflow Overview\n\n";
md += "<table>\n";
md += "  <tr><th>ID</th><td>" + ctx.workflow.id + "</td></tr>\n";
md += "  <tr><th>Description</th><td>" + (ctx.workflow.description || "No description available.") + "</td></tr>\n";
md += "  <tr><th>Path</th><td>" + ctx.workflow.workflowCategory.path + "</td></tr>\n";
md += "  <tr><th>Category</th><td>" + ctx.workflow.workflowCategory.name + "</td></tr>\n";
md += "  <tr><th>Version</th><td><code>" + ctx.workflow.version + "</code></td></tr>\n";
md += "  <tr><th>Author</th><td>" + (ctx.author || "System Generated") + "</td></tr>\n";
md += "  <tr><th>Date</th><td>" + new Date().toString() + "</td></tr>\n";
md += "</table>\n\n";

md += "## Diagram\n\n";
md += "[<img src=\"./" + ctx.workflow.name.replace(/ /g, '_') + ".svg\">](./" + ctx.workflow.name.replace(/ /g, '_') + ".svg)\n\n";

md += "## Inputs\n\n";
md += inputHtml + "\n\n";

md += "## Outputs\n\n";
md += outputHtml + "\n\n";

md += "## Attributes (Variables)\n\n";
md += attrHtml + "\n\n";

md += "## Usuages\n\n";
md += usagesHtml + "\n\n";

md += "## Dependencies\n\n";
md += dependenciesHtml + "\n\n";

md += "## Workflow Steps\n\n";
md += ctx.steps + "\n\n";

return md;
```

</td></tr>
</table><br><table><tr><th>Name</th><td>renderNamedList</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.documentation.util</td></tr>
<tr><th>ID</th><td>1e8036d8-4648-46fc-bc2f-db2d86ec3f4a</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>title</td><td><code>string</code></td><td>Title</td></tr>
<tr><td>items</td><td><code>Array</code></td><td>Items</td></tr>
<tr><td>includeValue</td><td><code>boolean</code></td><td>Include Values?</td></tr>
<tr><td>markdown</td><td><code>boolean</code></td><td>Render as markdown?</td></tr></table></td></tr>
<tr><th>Output</th><td>string</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Handle empty list
if (!items || items.length === 0) {
    return markdown
        ? "_No " + title + " defined._\n"
        : "<p>No " + title + " defined.</p>";
}

var output = "";

// Render Markdown table
if (markdown) {
    output += "| Name | Type | Description" + (includeValue ? " | Value" : "") + " |\n";
    output += "|:-----|:-----|:-------------" + (includeValue ? "|:-------" : "") + "|\n";

    for (var i = 0; i < items.length; i++) {
        var row = "| " + (items[i].name || "-") +
            " | `" + (items[i].type || "-") + "`" +
            " | " + (items[i].description || "-");

        if (includeValue) {
            // Format value for display using a helper module
            row += " | " + System.getModule("com.broadcom.pso.vro.util").formatObjectValue(items[i].value);
        }

        row += " |\n";
        output += row;
    }
} else {
    // Render HTML table
    output += "<table>\n";
    output += "<tr><th>Name</th><th>Type</th><th>Description</th>";
    if (includeValue) output += "<th>Value</th>";
    output += "</tr>\n";

    for (var i = 0; i < items.length; i++) {
        output += "<tr><td>" + (items[i].name || "-") + "</td><td>" +
            (items[i].type || "-") + "</td><td>" +
            (items[i].description || "-") + "</td>";

        if (includeValue) {
            // Format value for display using a helper module
            output += "<td>" + System.getModule("com.broadcom.pso.vro.util").formatObjectValue(items[i].value) + "</td>";
        }

        output += "</tr>\n";
    }

    output += "</table>";
}

return output;

```

</td></tr>
</table><br><table><tr><th>Name</th><td>formatObjectValue</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.util</td></tr>
<tr><th>ID</th><td>52457c93-8d24-44c3-86cd-1868beeced34</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>obj</td><td><code>Any</code></td><td>Object</td></tr></table></td></tr>
<tr><th>Output</th><td>string</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
if (obj === null || obj === undefined) return "-";

if (typeof obj !== "object") return obj.toString();

// Try common readable properties
if (obj.name) return obj.name;
if (obj.id) return obj.id;
if (obj.value) return obj.value;

// Fallback to class type
if (obj.constructor && obj.constructor.name) {
    return "[object " + obj.constructor.name + "]";
}

// Last resort
return "[object]";
```

</td></tr>
</table><br><table><tr><th>Name</th><td>renderReferenceList</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.documentation.util</td></tr>
<tr><th>ID</th><td>b6b4ddc7-5a7e-42a4-a455-d108ae65f6e9</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>Renders a list of reference items as either an HTML or Markdown table. Each row includes a formatted name, type, and location.</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>title</td><td><code>string</code></td><td>Title</td></tr>
<tr><td>items</td><td><code>Array</code></td><td>Items</td></tr>
<tr><td>markdown</td><td><code>boolean</code></td><td>Render as markdown?</td></tr></table></td></tr>
<tr><th>Output</th><td>string</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Return early if the list is empty
if (!items || items.length === 0) {
    return markdown
        ? "_No " + title + " defined._\n"
        : "<p>No " + title + " defined.</p>";
}

var output = "";

// Helper: Format the name and ID into a single label
function formatName(item) {
    var name = item.name || "";
    var id = item.id || "";
    return (name && id) ? name + " - " + id : name || id || "-";
}

// Helper: Format the location string
function formatLocation(item) {
    var area = item.refArea || "";
    var refItem = item.refItem || "";
    return (area && refItem) ? area + " - " + refItem : area || refItem || "-";
}

// Markdown output
if (markdown) {
    output += "| Name | Type | Location |\n";
    output += "|:-----|:-----|:---------|\n";
    for (var i = 0; i < items.length; i++) {
        var row = "| " + formatName(items[i]) +
            " | `" + (items[i].type || "-") + "`" +
            " | " + formatLocation(items[i]) + " |\n";
        output += row;
    }
} else {
    // HTML output
    output += "<table>\n";
    output += "<tr><th>Name</th><th>Type</th><th>Location</th></tr>\n";

    for (var i = 0; i < items.length; i++) {
        output += "<tr><td>" + formatName(items[i]) + "</td><td>" +
            (items[i].type || "-") + "</td><td>" +
            formatLocation(items[i]) + "</td></tr>\n";
    }

    output += "</table>";
}

return output;
```

</td></tr>
</table><br><table><tr><th>Name</th><td>renderHtmlDoc</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.documentation.util</td></tr>
<tr><th>ID</th><td>9ea7feba-c08d-43af-ab6f-766d4a600c93</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>This is used to Generate the Workflow Documentation into a HTML Format</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>ctx</td><td><code>Properties</code></td><td>Documentation context (workflow, navLinks, diagram, steps)</td></tr></table></td></tr>
<tr><th>Output</th><td>string</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
var inputHtml = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderNamedList("Inputs", ctx.workflow.inParameters, false, false);
var outputHtml = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderNamedList("Outputs", ctx.workflow.outParameters, false, false);
var attrHtml = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderNamedList("Attributes (Variables)", ctx.workflow.attributes, true, false);
var usagesHtml = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderReferenceList("Usages", ctx.usages, false);
var dependenciesHtml = System.getModule("com.broadcom.pso.vro.rest.documentation.util").renderReferenceList("Dependencies", ctx.dependencies, false);
var styles = System.getModule("com.broadcom.pso.vro.resource").getOrCreateResourceElement('Documentation/Config', 'styles.css').getContentAsMimeAttachment().content
var html = System.getModule("com.broadcom.pso.vro.resource").getOrCreateResourceElement('Documentation/Config', 'template.html').getContentAsMimeAttachment().content
var highlightJS = System.getModule("com.broadcom.pso.vro.resource").getOrCreateResourceElement('Documentation/Config', 'highlight.min.js').getContentAsMimeAttachment().content
html = html.replace(/{{ workflow_name }}/g, ctx.workflow.name)
    .replace(/{{ styles }}/g, styles)
    .replace(/{{ highlight.js }}/g, highlightJS)
    .replace(/{{ navlinks }}/g, ctx.navLinks)
    .replace(/{{ id }}/g, ctx.workflow.id)
    .replace(/{{ description }}/g, (ctx.workflow.description || "No description available"))
    .replace(/{{ path }}/g, ctx.workflow.workflowCategory.path)
    .replace(/{{ category }}/g, ctx.workflow.workflowCategory.name)
    .replace(/{{ version }}/g, ctx.workflow.version)
    .replace(/{{ author }}/g, (ctx.author || "System Generated"))
    .replace(/{{ date }}/g, new Date().toString())
    .replace(/{{ diagram }}/g, ctx.diagram)
    .replace(/{{ inputs }}/g, inputHtml)
    .replace(/{{ outputs }}/g, outputHtml)
    .replace(/{{ attributes }}/g, attrHtml)
    .replace(/{{ usages }}/g, usagesHtml)
    .replace(/{{ dependencies }}/g, dependenciesHtml)
    .replace(/{{ steps }}/g, ctx.steps)

return html
```

</td></tr>
</table><br><table><tr><th>Name</th><td>renderWorkflowStep</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.documentation.util</td></tr>
<tr><th>ID</th><td>dbbef81f-7f5b-4973-89e9-4b8822269883</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>Renders a workflow step as either an HTML/Markdown table or section layout.</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>item</td><td><code>Properties</code></td><td>Item</td></tr>
<tr><td>path</td><td><code>string</code></td><td>Path</td></tr>
<tr><td>type</td><td><code>string</code></td><td>html or markdown</td></tr>
<tr><td>asTable</td><td><code>boolean</code></td><td>Render as a table (true) or sectioned layout (false)</td></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
var label = item["display-name"] || (item.type == "end" ? "End Workflow" : item.type) || item.name;
var sectionTitle = label + " [" + path + " path]";
var anchor = item.name;

var html = "<h3><a name='" + anchor + "'>" + sectionTitle + "</a></h3>\n";

// Wrapper rendering: table or block style
if (asTable) {
    html += "<table>\n";
    html += row("Name", item.name);
    html += row("Display Name", item["display-name"]);
    html += row("Type", item.type);
    html += row("Description", item.description || "No description");
    if (item["script-module"]) html += row("Script Module", item["script-module"]);
    if (item["prototype-id"]) html += row("Prototype ID", item["prototype-id"]);
    if (item["throw-bind-name"]) html += row("Error Bind", item["throw-bind-name"]);
    if (item['in-binding']) html += row("Input Bindings", renderBindings(item['in-binding']));
    if (item['out-binding']) html += row("Output Bindings", renderBindings(item['out-binding']));
    if (item["runtime"]) html += row("Runtime", item["runtime"]);

    if (item["script"] && item["script"].value) {
        var lang = item.runtime || 'javascript';
        html += row("Script", codeBlock(lang, item["script"].value), true);
    }

    if (item.type === 'condition' || item.type === 'custom-condition') {
        html += row("Condition True", item['out-name']);
        html += row("Condition False", item['alt-out-name']);
    }

    if (item.type === 'switch' && item.condition) {
        html += row("Switch Cases", renderConditionTable(item.condition));
    }

    if ((item.type === 'link' || item.type === 'foreach') && (item['linked-workflow-id'] || item.reference)) {
        html += row("Linked Workflow", renderWorkflowInfo(item));
    }

    if (item.type === 'multiple' && item['workflow-subelements-list']) {
        html += row("Multiple Workflows", renderMultipleSubWorkflows(item));
    }

    if (item.type === 'task' && item.item && item.item.usedActions) {
        html += row("Used Actions", renderActions(item.item.usedActions));
    }

    html += "</table>\n";
} else {
    // Header-based section layout
    html += renderSection("Name", item.name);
    html += renderSection("Display Name", item["display-name"]);
    html += renderSection("Type", item.type);
    html += renderSection("Description", item.description || "No description");
    if (item["script-module"]) html += renderSection("Script Module", item["script-module"]);
    if (item["prototype-id"]) html += renderSection("Prototype ID", item["prototype-id"]);
    if (item["throw-bind-name"]) html += renderSection("Error Bind", item["throw-bind-name"]);
    if (item['in-binding']) html += renderSection("Input Bindings", renderBindings(item['in-binding']));
    if (item['out-binding']) html += renderSection("Output Bindings", renderBindings(item['out-binding']));
    if (item["runtime"]) html += renderSection("Runtime", item["runtime"]);

    if (item["script"] && item["script"].value) {
        var lang = item.runtime || 'javascript';
        html += renderSection("Script", codeBlock(lang, item["script"].value), true);
    }

    if (item.type === 'condition' || item.type === 'custom-condition') {
        html += renderSection("Condition True", item['out-name']);
        html += renderSection("Condition False", item['alt-out-name']);
    }

    if (item.type === 'switch' && item.condition) {
        html += renderSection("Switch Cases", renderConditionTable(item.condition));
    }

    if ((item.type === 'link' || item.type === 'foreach') && (item['linked-workflow-id'] || item.reference)) {
        html += renderSection("Linked Workflow", renderWorkflowInfo(item));
    }

    if (item.type === 'multiple' && item['workflow-subelements-list']) {
        html += renderSection("Multiple Workflows", renderMultipleSubWorkflows(item));
    }

    if (item.type === 'task' && item.item && item.item.usedActions) {
        html += renderSection("Used Actions", renderActions(item.item.usedActions));
    }
}

if (type == 'html') {
    if (asTable) {
        var finalhtml = "<li>\n" + html + "\n</li>"
    } else {
        var finalhtml = "<li class='card'>\n" + html + "\n</li>"
    }
} else {
    var finalhtml = html + "\n\n---"
}

return {
    section: finalhtml,
    link: "<li><a href='#" + anchor + "'>" + sectionTitle + "</a></li>"
};

function row(label, value, isScript) {
    var tdClass = isScript ? " class='script'" : "";
    return "<tr><th>" + label + "</th><td" + tdClass + ">" + value + "</td></tr>\n";
}

function renderSection(label, content, isScript) {
    var divClass = isScript ? " class='script'" : "";
    return "<h4>" + label + "</h4><div" + divClass + ">" + content + "</div>\n";
}

function codeBlock(runtime, script) {
    if (type === 'markdown') {
        return "\n\n```" + mapRuntimeToHighlightLanguage(runtime) + "\n" + script + "\n```\n\n";
    } else {
        return "<pre><code class='language-" + mapRuntimeToHighlightLanguage(runtime) + "'>" + escapeHtml(script) + "</code></pre>";
    }
}

function renderBindings(binding) {
    if (!binding || !binding.bind) return "";
    var rows = binding.bind.map(function (b) {
        return "<tr><td>" + b.name + "</td><td><code>" + b.type + "</code></td><td>" + (b.description || "") + "</td><td>" + b["export-name"] + "</td></tr>";
    }).join("\n");
    return "<table><tr><th>Name</th><th>Type</th><th>Description</th><th>Export Name</th></tr>" + rows + "</table>";
}

function renderConditionTable(conditions) {
    var rows = conditions.map(function (c) {
        return "<tr><td>" + c.value + "</td><td>" + c.label + "</td></tr>";
    }).join("\n");
    return "<table><tr><th>Condition</th><th>Target</th></tr>" + rows + "</table>";
}

function renderWorkflowInfo(item) {
    var linkedId = item.type === 'foreach' ? item.reference.id : item['linked-workflow-id'];
    var wf = Server.getWorkflowWithId(linkedId);
    if (!wf) return "Not found";

    var html = "<table>\n";
    html += row("Name", wf.name);
    html += row("Version", "<code>" + wf.version + "</code>");
    html += row("ID", wf.id);
    html += row("Description", wf.description || "No description");
    if (wf.inParameters.length > 0) html += row("Inputs", renderParameterTable(wf.inParameters));
    if (wf.outParameters.length > 0) html += row("Outputs", renderParameterTable(wf.outParameters));
    html += "</table>";
    return html;
}

function renderMultipleSubWorkflows(item) {
    var subEls = item['workflow-subelements-list']['workflow-subelement'];
    return subEls.map(function (wf) {
        return renderWorkflowInfo({ type: 'link', 'linked-workflow-id': wf['linked-workflow-id'] });
    }).join("<br>");
}

function renderParameterTable(params) {
    var rows = params.map(function (p) {
        return "<tr><td>" + p.name + "</td><td><code>" + p.type + "</code></td><td>" + (p.description || "") + "</td></tr>";
    }).join("\n");
    return "<table><tr><th>Name</th><th>Type</th><th>Description</th></tr>" + rows + "</table>";
}

function renderActions(actions) {
    return actions.map(function (action) {
        var html = "<table>";
        html += row("Name", action.name);
        html += row("Module", action.module.name);
        html += row("ID", action.id);
        html += row("Version", "<code>" + action.version + "</code>");
        html += row("Description", action.description || "No description");
        html += row("Inputs", renderParameterTable(action.parameters || []));
        html += row("Output", action.returnType);

        var runtime = 'Javascript';
        var apiAction = System.getModule("com.broadcom.pso.vro.rest.action").getActionByScriptModule(action.id);

        if (apiAction.actionEnvironmentId) {
            var env = System.getModule("com.broadcom.pso.vro.rest.action").getActionEnvironment(apiAction.actionEnvironmentId);
            env.attributes.forEach(function (a) {
                if (a.name === 'runtime') runtime = a.value;
            });
        } else if (apiAction.runtime) {
            runtime = apiAction.runtime;
        }

        var runtimeStr = apiAction.actionEnvironmentName ? apiAction.actionEnvironmentName + " | " + runtime : runtime;
        html += row("Runtime Environment", runtimeStr);
        html += row("Script", codeBlock(runtime, action.script), true);
        html += "</table><br>";
        return html;
    }).join("");
}

function escapeHtml(unsafeString) {
    return unsafeString
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/&/g, "&amp;")
        .replace(/"/g, "&quot;")
        .replace(/'/g, "&#039;");
}

function mapRuntimeToHighlightLanguage(runtimeEnvironment) {
    var lang = runtimeEnvironment.toLowerCase();
    if (lang.indexOf('node') !== -1) return 'javascript';
    if (lang.indexOf('powershell') !== -1 || lang.indexOf('powercli') !== -1) return 'powershell';
    if (lang.indexOf('python') !== -1) return 'python';
    return 'javascript';
}

```

</td></tr>
</table><br><table><tr><th>Name</th><td>getActionByScriptModule</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.action</td></tr>
<tr><th>ID</th><td>0750a240-85ef-4d92-8e95-cf7ace890475</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>scriptModule</td><td><code>string</code></td><td>Script Module (Module/Action)</td></tr>
<tr><td>query</td><td><code>string</code></td><td>(Optional) Additional Parameters</td></tr>
<tr><td>apiVersion</td><td><code>string</code></td><td>(Optional) Override the default API Version</td></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Use API Version if passed, else set API Version
apiVersion = apiVersion ? apiVersion : '2021-07-15'

// Build API Call
var path = '/api/actions/' + scriptModule
var query = encodeURI('?apiVersion=' + apiVersion + (query ? '&' + query : ''))
var url = path + query

// Execute API call and return results
return System.getModule("com.broadcom.pso.vro.rest.methods").get(url);
```

</td></tr>
</table><br><table><tr><th>Name</th><td>getActionEnvironment</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.action</td></tr>
<tr><th>ID</th><td>f86aaabf-bc2e-441e-91eb-24a8ff02fe83</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>environmentId</td><td><code>string</code></td><td>Environment ID</td></tr>
<tr><td>query</td><td><code>string</code></td><td>(Optional) Additional Parameters</td></tr>
<tr><td>apiVersion</td><td><code>string</code></td><td>(Optional) Override the default API Version</td></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Use API Version if passed, else set API Version
apiVersion = apiVersion ? apiVersion : '2021-07-15'

// Build API Call
var path = '/api/catalog/System/ActionEnvironment/' + environmentId
var query = encodeURI('?apiVersion=' + apiVersion + (query ? '&' + query : ''))
var url = path + query

// Execute API call and return results
return System.getModule("com.broadcom.pso.vro.rest.methods").get(url);
```

</td></tr>
</table><br><table><tr><th>Name</th><td>updateResourceElementByMimeAttachement</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.resource</td></tr>
<tr><th>ID</th><td>1fb353fb-d693-4217-a2e3-b905708b05f5</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>resourceElement</td><td><code>ResourceElement</code></td><td>Resource Element</td></tr>
<tr><td>content</td><td><code>Any</code></td><td>Content</td></tr>
<tr><td>mimeType</td><td><code>string</code></td><td>Mime Type</td></tr></table></td></tr>
<tr><th>Output</th><td>void</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
if (!resourceElement) throw "You must supply a Resource Element"

if (!content || !mimeType) throw " You must supply content and mimeType"

var mimeAttachment = new MimeAttachment();
mimeAttachment.content = Server.toStringRepresentation(content).stringValue;
mimeAttachment.mimeType = mimeType;
mimeAttachment.name = resourceElement.name;
resourceElement.setContentFromMimeAttachment(mimeAttachment);
```

</td></tr>
</table><br><table><tr><th>Name</th><td>updateResource</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.resource</td></tr>
<tr><th>ID</th><td>7529eef6-0c4f-4824-a728-0c26349be13a</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>resourceId</td><td><code>string</code></td><td>Resource ID</td></tr>
<tr><td>name</td><td><code>string</code></td><td>Name</td></tr>
<tr><td>description</td><td><code>string</code></td><td>Description</td></tr>
<tr><td>categoryId</td><td><code>string</code></td><td>Category ID</td></tr>
<tr><td>version</td><td><code>string</code></td><td>Version</td></tr>
<tr><td>query</td><td><code>string</code></td><td>(Optional) Additional Parameters</td></tr>
<tr><td>apiVersion</td><td><code>string</code></td><td>(Optional) Override the default API Version</td></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Use API Version if passed, else set API Version
apiVersion = apiVersion ? apiVersion : '2021-07-15'

// Build API Call
var path = '/api/resources/' + resourceId
var query = encodeURI('?apiVersion=' + apiVersion + (query ? '&' + query : ''))
var url = path + query

var content = {
    "id": resourceId,
    "name": name,
    "description": description,
    "category-id": categoryId,
    "version": version
}

// Execute API call and return results
return System.getModule("com.broadcom.pso.vro.rest.methods").put(url, JSON.stringify(content));
```

</td></tr>
</table><br><table><tr><th>Name</th><td>put</td></tr>
<tr><th>Module</th><td>com.broadcom.pso.vro.rest.methods</td></tr>
<tr><th>ID</th><td>e7ed398e-f9d4-4a29-b503-b2f0639d33a7</td></tr>
<tr><th>Version</th><td><code>0.2.0</code></td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Inputs</th><td><table><tr><th>Name</th><th>Type</th><th>Description</th></tr><tr><td>url</td><td><code>string</code></td><td>URL</td></tr>
<tr><td>content</td><td><code>string</code></td><td>Content</td></tr>
<tr><td>headers</td><td><code>Properties</code></td><td>(Optional) Headers</td></tr></table></td></tr>
<tr><th>Output</th><td>Properties</td></tr>
<tr><th>Runtime Environment</th><td>Javascript</td></tr>
<tr><th>Script</th><td class='script'>

```javascript
// Set method
var method = 'PUT';

// If headers is supplied, use headers else generate an empty property
headers = headers ? headers : new Properties();

// Return the Results
return System.getModule("com.broadcom.pso.vro.rest.methods").restOperation(method, url, content, headers);
```

</td></tr>
</table><br></td></tr>
</table>


---
<h3><a name='item0'>End Workflow [Main path]</a></h3>
<table>
<tr><th>Name</th><td>item0</td></tr>
<tr><th>Display Name</th><td>undefined</td></tr>
<tr><th>Type</th><td>end</td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Input Bindings</th><td></td></tr>
</table>


---
<h3><a name='item2'>End Workflow [Error Handler path]</a></h3>
<table>
<tr><th>Name</th><td>item2</td></tr>
<tr><th>Display Name</th><td>undefined</td></tr>
<tr><th>Type</th><td>end</td></tr>
<tr><th>Description</th><td>No description</td></tr>
<tr><th>Error Bind</th><td>errCode</td></tr>
<tr><th>Input Bindings</th><td></td></tr>
</table>


---
