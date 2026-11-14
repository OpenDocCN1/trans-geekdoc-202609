# 5.9. Creating the Policy-Map to apply the Class-Maps

| Command | Description |
|---|---|
| Router(config)# policy-map type inspect policy-map-name | Creates a Policy-Map and defines these options. |
| Router(config-pmap)# class type inspect class-map-name | Associates this with one (or more) Class-Map(s). |
| Router(config-pmap-c)# {drop | inspect | pass } | Defines the action to be performed. |

# 5.10. Defining the zone pairs

| Command | Description |
|---|---|
| Router(config)# zone-pair security zone-pair-name source { source-zonename | self | default } destination { destination-zone-name | self | default } | Creates a pair of zones that allows the application of a unidirectional “Policy-Map” between both zones. |

# 5.11. Applying the policy maps to the zone pairs

| Command | Description |
|---|---|
| Router(config-sec-zone-pair)# service-policy type inspect policymap-name | Applies the Policy-Map strategy to the zone pair. |

# 5.12. Assigning interfaces to zones

| Command | Description |
|---|---|
| Router(config)# interface type number
Router(config-if)# zone-member security zone-name | Associates an interface with a specific security zone. |