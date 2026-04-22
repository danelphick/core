Add a FoxESS device to the local Home Assistant instance.

Arguments: `$ARGUMENTS` — expects two named parameters `apiKey=<value> deviceSN=<value>`. Parse them from the argument string.

## Step 1 — Ensure Home Assistant is running

Check if HA is already up:
```bash
curl -s -o /dev/null -w "%{http_code}" http://localhost:8123/
```

If the response is not `200`, start it in the background:
```bash
cd ~/github/home-assistant/core && hass -c config &
```
Then poll until it responds 200 (retry every 5 seconds, up to 60 seconds).

## Step 2 — Open Home Assistant in the browser via Playwright

Navigate to `http://localhost:8123`.

Take a screenshot to check the current state. If the page is the login screen (`/auth/authorize`):
- Fill username field with `dan`
- Fill password field with `wpevh572357+`
- Submit the form
- Wait for navigation to `/home/overview` or `/config/dashboard`

## Step 3 — Navigate to Add Integration

Navigate to `http://localhost:8123/config/integrations/add`.

Wait for the integration search dialog to appear (it may take a moment to load).

## Step 4 — Search for FoxESS

Take a snapshot to find the search input field. Type `FoxESS` into the search box. Wait briefly for results to appear, then take another snapshot and click the FoxESS result.

## Step 5 — Fill the config flow form

A dialog will appear with the FoxESS setup form. Take a snapshot to get the field refs. Fill in:
- `apiKey` field → the apiKey value parsed from arguments
- `deviceSN` field → the deviceSN value parsed from arguments
- Leave the `name` field at its default

Click Submit/Next to proceed.

## Step 6 — Confirm result

Take a screenshot. Report whether the device was added successfully or if an error was shown (e.g. invalid API key, device not found).
