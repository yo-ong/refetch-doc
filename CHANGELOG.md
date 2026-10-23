# Changelog

## 0.4.1 — 2026-10-23

### Changed

- Wording: capturing requests is now called recording (the **Record** button, "Don't record hidden requests") and sending a request again is called replaying. The extension is now named "ReFetch - Record & Replay Requests".
- Faster: with recording off, pages and the network are left almost untouched (no body reads, and the extension only watches network traffic while recording is on). The list, filter and search stay fast with 3,000 requests.
- Large bodies: the detail view shows only the first 100,000 characters of a very large body, with a **Show all** button. Copy as and Edit still use the full body.

### Fixed

- Duration (ms) is now a whole number and closer to the real time. Document requests are measured until the response starts.

## 0.4.0 — 2026-10-22

### Added

- **Search**: A search box above the list shows only requests whose URL, request/response headers or bodies contain the text. It works on top of the filter, and previous/next in the detail view follows the results.
- **Copy as cURL / fetch**: Copy a request from the detail view as a cURL (bash) command with the headers the browser sent, `Cookie` included, or as `fetch` code with the page's own headers.
- **Export HAR**: Save the requests in the list as a HAR 1.2 file you can open in DevTools or other tools. The file includes cookies, so treat it as sensitive.
- **New request**: Write a request from scratch in the editor and send it from the current tab's page.

### Changed

- Clear removes only the current tab's requests when This tab only is on.

## 0.3.0 — 2026-10-21

### Added

- **This tab only**: A toolbar toggle that lists only the current tab's requests.
- **Tab column**: Shows the ID of the tab that sent each request. Hidden by default; turn it on from the column menu.
- **Send from extension**: When the page that sent a request is gone (its tab was closed, or the frame is now on another origin), the editor offers to send the edited request from the extension instead. The page's CORS, cookie policy and Origin don't apply, and the headers shown in the editor, `Cookie` included, are sent as is; deleting the `Cookie` line sends no cookies, and only a request that never had one gets the browser's normal cookies. Nothing is sent this way unless you choose it, and these requests are labelled "Sent from extension".

### Changed

- Capture is now one switch for all tabs instead of per tab. It is still off by default and turns off when the browser restarts.
- Requests from all tabs go into one log that keeps the latest 3,000 requests in total (was 1,000 per tab). Requests stay after their tab is closed and are removed only by Clear or a browser restart.
- Clear empties the whole log, including other tabs' requests, even when This tab only is on.
- Requests from incognito/private windows (if you allow the extension there) share the same log and now stay after the window closes, until Clear or a browser restart.

### Removed

- **Preserve log**: Navigating or reloading a page never clears requests now. Use Clear to start fresh.

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
