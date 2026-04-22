Stop the running Home Assistant instance that was started by /start-hass.

Run the following command to find and kill the hass process:

```bash
pkill -f "hass -c config" && echo "Home Assistant stopped." || echo "No running Home Assistant instance found."
```

Report whether the process was found and killed, or if no instance was running.
