# ReFetch Privacy Policy

**Last updated: 2026-10-24**

ReFetch ("the extension") is a browser extension that records, inspects and replays fetch, XMLHttpRequest and EventSource requests made by web pages in your browser.

## Data we do not collect

ReFetch does not collect, transmit, sell or share any personal or usage data. The extension has no servers, no accounts, no analytics and no advertising. It does not send any data to the developer or to any third party.

## Data processed locally

When you turn recording on, ReFetch records the requests your tabs make. A record can include the URL, method, request and response headers, request and response bodies (truncated to 1 MiB), and timing information. These records may contain sensitive content such as cookies or authorization tokens, because they reflect what the page sends and receives.

- Recorded data is stored only in your browser: in local extension storage (`storage.local`), and, for the original bytes of uploaded request bodies kept so a replay can resend them exactly, in the extension's IndexedDB (up to 100 MiB per body, 1 GiB in total).
- Recording is off by default. A single switch turns it on for all tabs, and it turns off again when the browser restarts.
- Records from all tabs are kept in one log, capped at the latest 3,000 records in total. The log is cleared at the start of each new browser session or when you press Clear (with This tab only on, Clear removes only the current tab's records). Records are kept when a page navigates or reloads and when a tab is closed.
- If you allow the extension in incognito/private windows, requests made there are recorded into the same log and are kept after the private window closes, until you press Clear or the browser restarts.
- Filter settings are stored in local extension storage as well, and can make ReFetch drop matching requests instead of storing them.
- You can stop recording at any time. Uninstalling the extension removes all recorded data.

## Settings sync

Your preferences (display mode, document-recording option, This tab only option, list columns and Raw / Pretty body view) are stored in `storage.sync`. If you are signed in to your browser with sync enabled, the browser vendor syncs these preferences between your devices under its own privacy policy. Recorded requests are never stored in `storage.sync`.

## Replayed requests

When you choose to replay a request, ReFetch sends it from the page you recorded it on, to the destination you selected or edited. Replays are made only on your explicit action. ReFetch does not send replays to any server of its own. A request you write with New request is sent the same way, from the current tab's page.

If that page is no longer available, you can choose "Send from extension". ReFetch then sends the request as you edited it directly from the extension to the site in that request, with the headers shown in the editor (including `Cookie`); a request without a `Cookie` header is sent with the browser's normal cookies. This happens only when you choose it, and nothing is sent to the developer or to any third party.

## Copying and exporting

"Copy as" puts a request you select, including headers such as `Cookie`, on your clipboard, and "Export HAR" saves the requests in the list, including cookies, to a file on your computer. Both happen only when you choose them, and ReFetch does not send the copied text or the file anywhere. Treat them as sensitive.

## Permissions

- **Host access (`<all_urls>`)**: to record and replay requests on whichever site you choose to inspect, and to send a request from the extension when you choose "Send from extension".
- **`webRequest`**: to read the actual request and response headers, including headers added by the browser.
- **`declarativeNetRequestWithHostAccess`**: to apply header edits that `fetch` cannot set during a replay, using a short-lived rule scoped to the tab and exact URL, and, for "Send from extension", a short-lived rule limited to requests not tied to any tab, for that exact URL and method, removed once the response headers arrive.
- **`storage` and `unlimitedStorage`**: to keep settings and recorded requests locally.
- **`sidePanel`**: to show the extension in the browser's side panel.

## Remote code

ReFetch does not load or execute remotely hosted code.

## Changes

If this policy changes, the updated version will be published at this URL with a new date.

## Contact

Please open an issue at https://github.com/yo-ong/refetch-doc/issues.
