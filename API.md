# API Reference

**Classes**

Name|Description
----|-----------
[StackResourceRenamer](#cdk-stack-resource-rename-stackresourcerenamer)|StackResourceRenamer renames stack name and stack's subordinate resources' custom physical names, so that a CDK stack can be used to create multiple stacks in same AWS environment.


**Structs**

Name|Description
----|-----------
[RenameProps](#cdk-stack-resource-rename-renameprops)|Properties to control rename process.


**Interfaces**

Name|Description
----|-----------
[IRenameOperation](#cdk-stack-resource-rename-irenameoperation)|Interface of operation used to rename stack and its resources.



## class StackResourceRenamer  <a id="cdk-stack-resource-rename-stackresourcerenamer"></a>

StackResourceRenamer renames stack name and stack's subordinate resources' custom physical names, so that a CDK stack can be used to create multiple stacks in same AWS environment.

__Implements__: [IAspect](#aws-cdk-core-iaspect)

### Initializer


Construct a new StackResourceRenamer.

```ts
new StackResourceRenamer(renameOper: IRenameOperation, props?: RenameProps)
```

* **renameOper** (<code>[IRenameOperation](#cdk-stack-resource-rename-irenameoperation)</code>)  RenameOperation is used to rename stack name and resources' custom physical names.
* **props** (<code>[RenameProps](#cdk-stack-resource-rename-renameprops)</code>)  Properties are set to customize rename operations.
  * **excludeResourceTypes** (<code>Array<string></code>)  An array of Resource Types whose custom physical names could not be changed. __*Default*__: []
  * **includeResourceTypes** (<code>Array<string></code>)  An array of Resource Types whose physical names could be updated. __*Default*__: []
  * **irregularResourceNames** (<code>Map<string, string></code>)  Mapping of resourceType names to physicalName fields for resources whose physical names donot follow the regular naming conventions: `${resourceType}`+'Name'. __*Default*__: {}


### Methods


#### visit(node) <a id="cdk-stack-resource-rename-stackresourcerenamer-visit"></a>

Implement core.IAspect interface.

```ts
visit(node: IConstruct): void
```

* **node** (<code>[IConstruct](#aws-cdk-core-iconstruct)</code>)  CFN resources to be renamed.




#### protected renameResource(node, resTypeName) <a id="cdk-stack-resource-rename-stackresourcerenamer-renameresource"></a>

Rename a CFN resource or stack.

```ts
protected renameResource(node: IConstruct, resTypeName: string): void
```

* **node** (<code>[IConstruct](#aws-cdk-core-iconstruct)</code>)  CFN resource or stack.
* **resTypeName** (<code>string</code>)  The type name of CFN resource.




#### *static* rename(stack, renameOper, props?) <a id="cdk-stack-resource-rename-stackresourcerenamer-rename"></a>

Static method to rename a stack and all its subordinate resources.

```ts
static rename(stack: IConstruct, renameOper: IRenameOperation, props?: RenameProps): void
```

* **stack** (<code>[IConstruct](#aws-cdk-core-iconstruct)</code>)  The stack (and all its children resources) to be renamed.
* **renameOper** (<code>[IRenameOperation](#cdk-stack-resource-rename-irenameoperation)</code>)  RenameOperation is used to rename stack name and resources' custom physical names.
* **props** (<code>[RenameProps](#cdk-stack-resource-rename-renameprops)</code>)  Properties are set to customize rename operations.
  * **excludeResourceTypes** (<code>Array<string></code>)  An array of Resource Types whose custom physical names could not be changed. __*Default*__: []
  * **includeResourceTypes** (<code>Array<string></code>)  An array of Resource Types whose physical names could be updated. __*Default*__: []
  * **irregularResourceNames** (<code>Map<string, string></code>)  Mapping of resourceType names to physicalName fields for resources whose physical names donot follow the regular naming conventions: `${resourceType}`+'Name'. __*Default*__: {}






## interface IRenameOperation  <a id="cdk-stack-resource-rename-irenameoperation"></a>


Interface of operation used to rename stack and its resources.
### Methods


#### rename(origVal, typeName) <a id="cdk-stack-resource-rename-irenameoperation-rename"></a>

Rename method to rename stack and its resources' custom physical names.

AWS generated physical names are not changed.
The updated stack name or custom resource's name is returned.

```ts
rename(origVal: string, typeName: string): string
```

* **origVal** (<code>string</code>)  The original custom physical name.
* **typeName** (<code>string</code>)  The type name of CFN resource.

__Returns__:
* <code>string</code>



## struct RenameProps  <a id="cdk-stack-resource-rename-renameprops"></a>


Properties to control rename process.



Name | Type | Description 
-----|------|-------------
**excludeResourceTypes**? | <code>Array<string></code> | An array of Resource Types whose custom physical names could not be changed.<br/>__*Default*__: []
**includeResourceTypes**? | <code>Array<string></code> | An array of Resource Types whose physical names could be updated.<br/>__*Default*__: []
**irregularResourceNames**? | <code>Map<string, string></code> | Mapping of resourceType names to physicalName fields for resources whose physical names donot follow the regular naming conventions: `${resourceType}`+'Name'.<br/>__*Default*__: {}


