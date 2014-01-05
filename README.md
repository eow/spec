EOW Specification
=================

* [Messages](messages)
  * [Orientation](orientation-message)
  * [Attack](attack-message)

Messages
-------

### Orientation Message

```json
{
  "position": {
    "x": 0,
    "y": 0,
  },
  "angle": 0,
  "velocity": 0
}
```

### Attack Message

```json
{
  "power": 0,
  "radius": 0,
  "range": 0
}
```
