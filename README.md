# mj-azure-iot-pnp-device-python

## Introduction

mj-azure-iot-pnp-device-python is a Python library for quickly implementing Azure IoT Devices with Plug and Play support.
It is easy to implement by tying IoT Plug and Play telemetries, properties and commands to class variables and methods.

See also:
* [What is IoT Plug and Play?](https://docs.microsoft.com/en-us/azure/iot-pnp/overview-iot-plug-and-play?WT.mc_id=IoT-MVP-5002686)
* [Azure IoT Device SDK for Python](https://github.com/Azure/azure-iot-sdk-python/blob/master/azure-iot-device/README.md)

## Install

It's in PyPI, so it's pretty easy.
Just run the following command.

```sh
sudo pip3 install mj-azure-iot-pnp-device
```

## Code snippets

### Import packages and create the client instance

```python
from mj_azure_iot_pnp_device.device import IoTHubDeviceClient as MjClient
import mj_azure_iot_pnp_device.contents as MjCont

pnp_client = MjClient()
```

### Create the read only property

Set the initial value to `value`.

```
pnp_client.maxTempSinceLastReboot = MjCont.ReadOnlyProperty()
pnp_client.maxTempSinceLastReboot.value = 10.96
```

### Create the writable property

(TODO)

### Create the telemetry and send it

Set the initial value to `value` and call `send_telemetry` method.

```python
pnp_client.temperature = MjCont.Telemetry()

pnp_client.temperature.value = current_temp
await pnp_client.send_telemetry("temperature")
```

It is better to use nameof from the [varname package](https://pypi.org/project/varname/).

```python
from varname import nameof
await pnp_client.send_telemetry(nameof(pnp_client.temperature))
```

### Create the command

(TODO)

## Sample code

* [pnp_simple_thermostat](samples/pnp_simple_thermostat)

## License

[MIT License](LICENSE.txt)
