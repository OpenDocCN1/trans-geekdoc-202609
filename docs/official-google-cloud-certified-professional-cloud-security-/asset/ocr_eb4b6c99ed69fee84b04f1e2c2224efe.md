The group:prod@acme.com Google group, on the other hand, is only included if the role binding conditions are met. As a result, it is only in effect until July 1, 2024.

Now let look at how policy inheritance works in Google Cloud.

# # Policy inheritance and resource hierarchy

Policy inheritance describes how policies are applied to resources that are lower in the resource hierarchy. The term effective policy refers to a resource's policies being passed through all its parents, all the way up the resource hierarchy. In that sequence, it is a combination of the following:

+   * The policy set on the resource
* The policies set on all of the resource's ancestry resource levels in the hierarchy

Each role binding (acquired from parent resources) has an impact on the resource's effective policy is assessed separately. If any higher-level role bindings provide access, a specific access request is granted. The access grant scope expands when a new role binding is added to any level of the resource; inherited policy.

To understand policy inheritance, let us consider a scenario where you grant a user, Bob, two different IAM roles at different levels in the resource hierarchy.

To grant Bob a role at the organization level, you set the following policy for your organization:

```
{
  "bindings": [
    {
      "members": [
        "user:bob@acme.com"
      ],
      "role": "roles/storage.objectViewer"
    }
  ],
  "etag": "BwujMjhCsNaY=",
  "version": 1
}
```

This policy grants Bob Storage Object Viewer role (roles/storage.objectViewer). Since you set the policy at the organization level, Bob can use these permissions for all projects and all Cloud Storage objects in the organization.