Consider when to automatically remediate noncompliant resources. Determine if Azure Policy should perform automatic remediation for noncompliant resources. Remediation is especially useful in resource tagging. Azure Policy can apply resource tags, and removed tags can be reapplied. With Azure Policy, you can ensure that all resources in a particular resource group are tagged with a specific tag, such as location so that the region can be identified.

It would be best if you used Azure RBAC and Azure Policy to achieve complete scope control. It would be best to use Azure RBAC and Azure Policy to gain complete scope control.

The Azure Policy evaluates the state of a resource and acts to ensure it remains compliant with the organization’s business rules. Compliance does not depend on who made the change or had permission to make it. The Azure Policy ensures a resource stays compliant by evaluating its state.

Azure RBAC controls who can access Azure resources, what they can do with them, and what areas they can access by focusing on user actions at different scopes. If actions need to be controlled, use Azure RBAC. Even if a user is given access to complete an action, Azure Policy still blocks it, resulting in noncompliant resources.

Table 4.4 illustrates the Azure Policy’s configuration maximum.

| Applies to | Applicable | Max counts |
|---|---|---|
| Scope | Policy definitions | 500 |
| Scope | Initiative definitions | 200 |
| Tenant | Initiative definitions | 2,500 |
| Scope | Policy or initiative assignments | 200 |
| Scope | Exemptions | 1000 |
| Policy definition | Parameters | 20 |
| Initiative definition | Policies | 1000 |
| Initiative definition | Parameters | 300 |
| Policy or initiative assignments | Exclusions (notScopes) | 400 |
| Policy rule | Nested conditionals | 512 |
| Remediation task | Resources | 50,000 |
| Policy definition, initiative, or assignment request body | Bytes | 1,048,576 |