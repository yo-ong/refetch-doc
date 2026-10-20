# ReFetch Privacy Policy

**Last updated: 2026-10-20**

ReFetch ("the extension") is a browser extension that captures, inspects and replays fetch, XMLHttpRequest and EventSource requests made by web pages in your browser.

## Data we do not collect

ReFetch does not collect, transmit, sell or share any personal or usage data. The extension has no servers, no accounts, no analytics and no advertising. It does not send any data to the developer or to any third party.

## Data processed locally

When you turn capture on for a tab, ReFetch records the requests that tab makes. A record can include the URL, method, request and response headers, request and response bodies (truncated to 1 MiB), and timing information. These records may contain sensitive content such as cookies or authorization tokens, because they reflect what the page sends and receives.

- Captured data is stored only in your browser: in local extension storage (`storage.local`), and, for the original bytes of uploaded request bodies kept so a replay can resend them exactly, in the extension's IndexedDB (up to 100 MiB per body, 1 GiB in total).
- Capture is off by default and must be enabled per tab.
- Captured data is cleared at the start of each new browser session, and each tab is capped at 1,000 records. If you turn off Preserve log, a tab's records are also cleared when it loads a new page.
- Filter settings are stored in local extension storage as well, and can make ReFetch drop matching requests instead of storing them.
- You can stop capture at any time. Uninstalling the extension removes all captured data.

## Settings sync

Your preferences (display mode, document-capture option, preserve-log option and list columns) are stored in `storage.sync`. If you are signed in to your browser with sync enabled, the browser vendor syncs these preferences between your devices under its own privacy policy. Captured requests are never stored in `storage.sync`.

## Replayed requests

When you choose to replay a request, ReFetch sends it from the page you captured it on, to the destination you selected or edited. Replays are made only on your explicit action. ReFetch does not send replays to any server of its own.

## Permissions

- **Host access (`<all_urls>`)**: to capture and replay requests on whichever site you choose to inspect.
- **`webRequest`**: to read the actual request and response headers, including headers added by the browser.
- **`declarativeNetRequestWithHostAccess`**: to apply header edits that `fetch` cannot set during a replay, using a short-lived rule scoped to the tab and exact URL.
- **`storage` and `unlimitedStorage`**: to keep settings and captured requests locally.
- **`sidePanel`**: to show the extension in the browser's side panel.

## Remote code

ReFetch does not load or execute remotely hosted code.

## Changes

If this policy changes, the updated version will be published at this URL with a new date.

## Contact

Please open an issue at https://github.com/yo-ong/refetch-doc/issues.
