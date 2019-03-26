# Leaky bucket implementation ported from nginx

## Theory

### Presentations

[label]: https://img.shields.io/badge/language%20-Russian%20-red.svg?style=flat-square?

Presentation on continuous time counters in python: [continuous-time-counters.ipynb](doc/ru/continuous-time-counters.ipynb) ![][label]

Presentation on rate limitting in NGINX: [nginx-burst-rate-limits.ipynb](doc/ru/nginx-burst-rate-limits.ipynb) ![][label]

## Usage

### Set up limits

```
zone = Zone('zone_name', rate_limit)
limit1 = Limit(zone, burst, nodelay)
```

### Default zones

TODO

### Decorators

```
@limit_calls(zone, burst, nodelay)
def some_function():
    """Usage with non-awatables"""
    return 0


@limit_calls(zone, burst, nodelay)
async def some_other_function():
    """Usage with awatables"""
    return await asincio.sleep(1)
```

## Manual mode

(Not implemented yet)

Transform a table with calls:

```
    (timestamp, requester_id, requested_object)
```

Into

```
   (timestamp, requester_id, access_granted, delay, excess)
```

## Synchronous mode

TODO
