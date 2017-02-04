# lcmap-change-worker
worker for initiating change detection jobs, and sending results to the data store

## Install
```bash
  # locally
  $ pip install -e.
```

## Usage
```bash
    # change-worker is available following install with pip
    $ change-worker

    # this runs the same script.  
    # Useful to save the pip install -e. step while working on cw.__main__
    python3 -m cw.__main__
```

```python
# same effect as change-worker
from cw import __main__
__main__.main()
```

## Configuration
landsat-change-worker is configurable with the following environment variables

| Variable | Default | Description |
| --- | --- | --- |
| `LCW_RABBIT_HOST` | localhost | RabbitMQ Host |
| `LCW_RABBIT_PORT` | 5672      | RabbitMQ Port |
| `LCW_RABBIT_QUEUE` | local.lcmap.changes.worker | Queue for LCW to listen for messages |
| `LCW_RABBIT_EXCHANGE` | local.lcmap.changes.worker | Exchange for LCW to publish messages |
| `LCW_RABBIT_RESULT_ROUTING_KEY` | change-detection-result | Routing key used when publishing change detection result messages |
| `LCW_RABBIT_SSL` | False | Enable/Disable SSL.  True/False |

## Developing & Testing
Get the local environment ready for development and testing.
```bash
   $ git clone git@github.com:usgs-eros/lcmap-change-worker
   $ cd lcmap-change-worker
   $ virtualenv -p python3 .venv
   $ . .venv/bin/activate
   $ pip install -e .[test]
   $ pip install -e .[dev]
```

Run tests:
```bash
   # the right way
   $ python setup.py test

   # alternatively
   $ pytest
```
## Deploying
