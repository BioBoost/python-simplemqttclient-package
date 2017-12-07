# Simple MQTT Client Package

Python library for a Simple MQTT Client

## Example

```python
from time import sleep
import sys
from simplemqttclient import SimpleMqttClient

def message_handler(client, userdata, msg):
    print("Received: " + msg.payload.decode('utf-8'))

mqttClient = SimpleMqttClient("shazooble")
mqttClient.subscribe("some/other/random/topic", message_handler)

mqttClient.start()

try:
  while True:
    mqttClient.publish("some/random/topic", "Hello World")
    sleep(10)
except KeyboardInterrupt:       # Catch CTRL-C
  mqttClient.stop()
  print ("Bye Bye")
  sys.exit()
```

## Development

Installing the package:

```shell
pip3 install .
```

Force re-installing package:

```shell
pip3 install --upgrade --no-deps --force-reinstall .
```

Removing the package:

```shell
pip3 uninstall simplemqttclient
```

Checking installed packages:

```shell
pip3 freeze
```
