# Changelog

## 0.2.0 — 2026-10-20

### Added

- **Filter**: Hide requests from the list by method, host, URL regex, status, content type and kind. Each condition can be set to Include or Exclude, and the toolbar shows how many requests are hidden.
- **Don't store hidden requests**: An option in the filter that drops hidden requests at capture time instead of only hiding them, so they don't use up the 1,000 requests kept per tab.
- **Previous / next**: Step through requests from the detail view without going back to the list. Going back highlights the last request you viewed.
- **DevTools-like status**: The Status column now shows `200 CORS` when the server answered but CORS blocked the page from reading the response, `(failed)` for network errors and `(canceled)` for aborted requests. The detail view shows the server's status line and headers for CORS-blocked requests.
- **Preserve log**: A toolbar toggle, on by default. Turn it off to clear the previous page's requests when the tab navigates or reloads, like DevTools.

### Changed

- The capture rules are now part of the filter. Existing rules are kept, with "Don't store hidden requests" turned on so they still drop requests as before.
- The Document requests toggle now shows its state even before capture is turned on for the tab.
- The store name now includes a short description: "ReFetch - Capture & Replay Requests".
