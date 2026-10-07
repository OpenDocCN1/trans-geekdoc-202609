# Cloud Asset Inventory 373

The preceding two queries are for general cloud assets; however, one of the important aspects of asset inventory is to find IAM policies that potentially violate your organization's security policies. Let us look at these now. Replace PROJECT_ID, DATASET_ID, and TABLE_NAME with the appropriate values for your project.

3. To find IAM policies that grant access to Gmail accounts, run the following query. This query is useful to see whether there has been any escalation from your Google Cloud organization to consumer accounts:

```
SELECT name, asset_type, bindings.role
FROM PROJECT_ID.DATASET_ID.TABLE_NAME
JOIN UNNEST (iam_policy.bindings) AS bindings
JOIN UNNEST (bindings.members) AS principals
WHERE principals like %@gmail.com
```

4. To find IAM policies that grant access to users rather than groups (as you know this is an anti-pattern for IAM access control), run the following query:

```
SELECT name, asset_type, bindings.role, members
FROM 'asset-inventory-api.iam_asset_inventory.iam_policy_inventory'
JOIN UNNEST (iam_policy.bindings) AS bindings
JOIN UNNEST (bindings.members) AS members
WHERE members like "@acme.com"order by name
```

5. To find IAM policies containing all service accounts, run the following query. This query is important to find out which service accounts are granted privileged roles:

```
SELECT name, asset_type, bindings.role, members
FROM 'asset-inventory-api.iam_asset_inventory.iam_policy_inventory'
JOIN UNNEST (iam_policy.bindings) AS bindings
JOIN UNNEST (bindings.members) AS members
WHERE members like "serviceAccount%"
order by name
```

6. To find IAM policies that are granted using groups, execute a query like this:

```
SELECT name, asset_type, bindings.role, members
FROM 'asset-inventory-api.iam_asset_inventory.iam_policy_inventory'
JOIN UNNEST (iam_policy.bindings) AS bindings
JOIN UNNEST (bindings.members) AS members
WHERE members like "group%"
order by name
```

Now that we have a solid understanding of how to query assets either using SCC or BigQuery, we will move on to another module of SCC for detecting misconfigurations.