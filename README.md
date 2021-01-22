# realtimeTibber

## Usage example:
```python
import tibber
import asyncio
from realtimeTibber import realTimeTibberSensor

APIkey = 'your-tibber-key'
tibber_connection = tibber.Tibber(APIkey)
tibber_connection.sync_update_info()

home = tibber_connection.get_homes()[0]
home.sync_update_info()

# Callback for the real-time data updates
def callback(liveMeasurement):
        print("----")
        print(liveMeasurement)

if home.has_real_time_consumption:
    sensor = realTimeTibberSensor(home)
    sensor.start_rt_subscription(callback)

tibber_connection.sync_close_connection()
```