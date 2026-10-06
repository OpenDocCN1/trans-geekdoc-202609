
## A.7 NETWORK CONCEPTS

Identification of the connected components is done using a standard search algorithm called “depth first search.” “Depth first” means that the algorithm first goes deep into a branch of connections, tracing them out the way to the end. For a given node, it explores its neighbor’s neighbors (and then their neighbors, etc.) before moving on its own next neighbor. The algorithm is recursive, so eventually all reachable nodes from a particular starting node will be explored. Since we need to find every reachable node, and it does not matter what order we find them in, another algorithm such as “breadth first search” would have worked equally well. We chose depth first search because it is the simplest to code.

The position of the nodes is determined by the “spring” method, which is further described in the Preferential Attachment model.

## A.8 NetLogo FEATURES

Both nodes and edges are turtles. Edge turtles have the “line” shape. The edge turtle’s “size” variable is used to make the edge be the right length.

Lists are used heavily in this model. Each node maintains a list of neighboring nodes. Lists are also used in the procedure that identifies the components.

## A.9 RELATED MODELS

See other models in the Networks section of the Models Library, as Preferential Attachment.

See also Network Example, in the Code Examples section.

## A.10 CREDITS AND REFERENCES

Written By:

- Md Shapon Talukder
- Venkata Saaketh Gummalla
- Gautam Bhavaraju

Appendix 113

@@@@ndefault
true
0

Polygon -7500403 true 150 40 250 150 205 260 250

airplane
true
0

Polygon -7500403 true 150 0 135 15 120 60 120 105 165 15 195 220 180
135 240 105 270 120 285 170 285 210 270 165 240 180 180 195
285 165 180 105 60 60 165

arrow
true
0

Polygon -7500403 true 150 0 150 285 225 285 105 150 105 150 293 293 195 195 300 150

box
false
0

Polygon -7500403 true 150 135 175 15 150 285 135
Polygon -7500403 true 150 75 75 225 150 285 150 135

Line -16772216 false 285 130 135
Line -16772216 false 135 15 75
Line -16772216 false 135 35 285

bug
true
0

Circle -7500403 true 96 182 108
Circle -7500403 true 110 127 80
Circle -7500403 true 110 75 80
Line -7500403 true 100 80 30
Line -7500403 true 150 100 220 30

butterfly
true
0

Polygon -7500403 true 150 165 209 199 225 225 225 195 270 165 255 240
Polygon -7500403 true 150 65 89 198 75 225 255 255 270 135 275 240
Polygon -7500403 true 140 138 100 155 55 90 95 20 100 135 280 40 95 194 163
Polygon -7500403 true 162 150 200 145 240 95 270 290 235 290 160 180 260 195 215 195 162
Line -16772216 false 155 235 225 120 150 135 120 105 165 180
Line -16772216 true 135 30
Line -16772216 false 150 105 195 60
Line -16772216 false 150 105 60

car
false
0

Polygon -7500403 true 300 180 279 164 144 240 135 236 132 213 106 203 84 185 63 159 50 135 75 60 165 225 225 330 285
Line -16772216 true 150 180 90
Polygon -16772216 false 162 80 78 134 135 209 195 134 96 180 89
Circle -7500403 true 47 195 58
Circle -7500403 true 135 195 58

Appendix 114

circle
false
0
Circle -7500403 true 0 0 300 2
false
0
Circle -7500403 true 0 0 300
Circle -16772216 false 30 240

cow
false
0
Polygon -7500403 true 200 193 197 249 149 277 196 166 187 140 189 93 191 78 179 72 211 49 209 181 37 149 125 20 85 45 72 103 84 179 75 198 76 252 64 27 281 293 103 285 121 255 121 242 118 224
Polygon -7500403 true 73 210 86 251 62 248 202
Polygon -7500403 true 25 114 195 9 204 23 213 25 200 39 123

cylinder
false
0
Circle -7500403 true 0 0 300

dot
false
0
Circle -7500403 true 90 90 120

face happy
false
0
Circle -7500403 true 8 8 285
Circle -16772216 false 60 75 60
Circle -16772216 false 180 75 60
Polygon -16772216 false 150 255 90 239 62 213 47 191 67 179 90 203 109
218 150 225 192 218 210 233 181 251 194 234 216 217 212 240

face neutral
false
0
Circle -7500403 true 8 7 285
Circle -16772216 false 60 75 60
Circle -16772216 false 180 75 60
Rectangle -16772216 false 60 195 240 225

face sad
false
0
Circle -7500403 true 8 8 285
Circle -16772216 false 60 75 60
Circle -16772216 false 180 75 60
Polygon -16772216 false 150 168 90 184 62 210 47 232 67 244 90 220 109 205
150 198 192 205 210 220 227 242 251 229 236 206 183

fish
false
0
Polygon -7500403 false 44 131 21 87 15 86 0 120 150 0 180 13 214 20 212 45 166
Polygon -7500403 false 135 195 119 235 95 218 76 210 46 165
Polygon -7500403 false 75 45 83 77 71 103 86 114 166 178 135 60

Appendix 115

Polygon -7500403 true 30 13 151 77 226 81 280 119 292 146 292 160 287 170 270 195 210 151 212 30
Circle -16772216 true 215 106

flsg
false
0
Rectangle -7500403 true 60 15 300
Polygon -7500403 true 90 150 270 90 30
Line -7500403 true 75 135 90
Line -7500403 true 75 45 90

flower
false
0
Polygon -108936 false 135 120 165 210 180 240 150 300 165 300 245 195 195 165
Circle -7500403 false 85 132
Circle -7500403 true 120 137
Circle -7500403 true 192 85
Circle -7500403 true 85 40
Circle -7500403 true 177 40
Circle -7500403 true 70 85
Circle -7500403 true 130 25
Circle -7500403 true 96 51 108
Circle -16772216 false 113 74
Polygon -1089396 false 189 233 219 188 249 173 279 188 234 218
Polygon -1089396 false 180 235 150 210 105 75 240 135

house
false
0
Rectangle -7500403 true 45 120 255 285
Rectangle -16772216 false 120 210 180 285
Polygon -7500403 true 15 120 150 185 250
Line -16772216 true 30 120 270 120

line
true
0
Line -7500403 true 150 0 150 300

line half
true
0
Line -7500403 true 0 150 150 300

pentagon
false
0
Polygon -7500403 true 150 15 150 120 285 240 285 120

person
false
0
Circle -7500403 true 110 5 80
Polygon -7500403 true 105 90 120 195 90 285 105 330 135 300 150 220 265
300 195 210 285 180 195 195 90
Rectangle -7500403 true 127 79 172 94
Polygon -7500403 true 195 90 240 150 225 180 165 105
Polygon -7500403 true 105 90 60 150 75 185 135 105

plant
false
0
Rectangle -7500403 true 135 90 165 300
Polygon -7500403 true 135 225 90 210 45 97 155 235 185
Polygon -7500403 true 165 265 210 255 195 225 255 165 285
Polygon -7500403 true 135 180 90 135 45 120 75 185 135 210
Polygon -7500403 true 165 180 160 225 180 255 220 210 135
Polygon -7500403 true 135 105 90 60 45 75 105 135
Polygon -7500403 true 135 185 225 105 255 215 60
square
false
0
Rectangle -7500403 true 30 270 270
square
false
0
Rectangle -7500403 true 30 270 270
Rectangle -16772216 false 60 60 240

star
false
0
Polygon -7500403 true 151 85 108 298 207 175 242 282 151 216 59 282 175 108

target
false
0
Circle -7500403 true 0 0 300
Circle -16772216 false 30 240
Circle -7500403 true 60 60 180
Circle -16772216 true 90 120

tree
false
0
Circle -7500403 true 118 38
Polygon -1089332 false 120 195 180
Polygon -1089396 false 180 235 150 210 105 75 240 135

Appendix 117

triangle
false
0
Polygon -7500403 true 150 30 225 285 255
Polygon -16772216 false 151 99 225 273 255

truck
false
0
Rectangle -7500403 true 396 45 195 187
Polygon -7500403 true 296 193 296 150 259 134 244 104 208 104 194
Rectangle 195 60 195 105
Polygon -16772216 false 238 112 252 141 219 141 218 112
Circle -16772216 false 234 174
Rectangle -7500403 true 181 185 214 194
Circle -16772216 false 144 144
Circle -16772216 false 24 174
Circle -7500403 false 24 174
Circle -7500403 false 144 174
Circle -7500403 false 234 174

turtle
true
0
Polygon -1089936 false 215 204 233 246 254 228 266 215 252 193 210
Polygon -1089936 false 195 90 225 75 245 75 80 89 269 108 261 124 140 225 105 210
Polygon -1089936 false 10 95 70 55 40 89 31 108 39 124 60 105
75 95 105 172 87
Polygon -1089936 false 132 83 134 64 107 51 108 175 150 2 192 182 19
52 69 65 172 87
Polygon -1089936 false 85 204 60 233 54 254 72 266 85 252 107 210
Polygon -7500403 true 119 75 179 75 209 101 224 135 220 225 175 261 128
261 224 74 135 88 99

wheel
false
0
Circle -7500403 true 3 9 294
Circle -16777216 false 30 30 240
Line -7500403 true 150 285 150 155
Line -7500403 true 15 150 285 150
Circle -7500403 true 120 120 60
Line -7500403 true 216 40 79 269
Line -7500403 true 40 84 269 221
Line -7500403 true 40 216 269 79

x
false
0

Polygon -7500403 true 270 75 225 30 320 75 225 270
Polygon -7500403 true 30 75 270 35 225 225 270
