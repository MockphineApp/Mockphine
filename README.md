# Mockphine Desktop

Mockphine is a local mock API server with passthrough fallback and a live request view.

Without a mock server, teams lose days to unstable environments, missing data, and broken demos. Mockphine gives you a stable local source of truth, with a real-backend escape hatch when you need it.

## Why Mockphine

- Ship UI work without waiting on backend readiness.
- Keep demos reliable even when the real API is down.
- Debug faster with a live request timeline.
- Share exact setups with your team in seconds.

## What you get

- Local mock server with passthrough fallback.
- Endpoint modes: mock, passthrough, or disabled.
- Fallback modes: passthrough to real backend or strict 404.
- Live request view with headers, body, status, and timing.
- Workspace import and export, plus shareable collection packs.
- Built-in packs to get started fast.

## Download and install

1. Download the installer for your OS from the [Mockphine](https://mockphine.com/) website.
2. Install the app.
3. Launch Mockphine.

If your OS blocks the app on first launch, allow it in the system prompt and try again.

## Fast setup

1. Create a server.
2. Choose a port (for example `3000`).
3. Set the real backend URL for passthrough.
4. Pick a fallback mode.
5. Start the server.

Send requests to `http://127.0.0.1:<port>`.

## Create your first endpoint

1. Add an endpoint with method and path.
2. Choose status, headers, and a JSON response body.
3. Pick a mode.
4. Save and send a request.

## Modes

Endpoint modes:

- Mock: return the configured response.
- Passthrough: forward to the real backend.
- Disabled: skip mock and passthrough.

Fallback modes:

- Fallback: unmatched requests passthrough to the real backend.
- Strict: unmatched requests return 404.

## Troubleshooting

- Port in use: stop the other service or pick a different port.
- Passthrough errors: verify the real backend URL and your network.
- No requests showing: make sure the server is started and you are calling the local URL.

## Links
- Webisite: https://mockphine.com/
