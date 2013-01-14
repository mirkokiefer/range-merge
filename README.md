#range-merge
Merges lists of key-values where the key is a range.

If ranges overlap in a conflicting way it returns multiple possible results:

``` js
var merge = require('range-merge')

var map1 = [
  {range: [1, 3], value: 1},
  {range: [6, 8], value: 2}
]
var map2 = [
  {range: [2, 4], value: 5},
  {range: [6, 7], value: 3}
]

var result = merge([map1, map2])
// returns:
{
  conflict: true,
  result: [
    [
      {range: [1, 3], value: 1},
      {range: [4, 4], value: 5},
      {range: [6, 8], value: 2},
    ], [
      {range: [1, 1], value: 1},
      {range: [2, 4], value: 5},
      {range: [6, 7], value: 3},
      {range: [8, 8], value: 2}
    ]
  ]
}
```