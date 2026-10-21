**English** | [한국어](README.ko.md)

# ReFetch

ReFetch is a browser extension for Chrome and Firefox that captures the fetch, XHR and EventSource requests of your tabs, shows them as raw HTTP, and lets you edit and resend them from the page that sent them.

- [Install from the Chrome Web Store](https://chromewebstore.google.com/detail/refetch/aobjmhncnmbideoghphkpjpehmbfohfe)
- [Changelog](CHANGELOG.md)
- [Privacy policy](PRIVACY.md)

![Captured requests](screenshots/requests.png)

## Features

- One switch captures all tabs, off by default. Status reads like DevTools: `200 CORS`, `(failed)`, `(canceled)`.
- One log of the latest 3,000 requests from all tabs, kept across page loads and after a tab is closed. Turn on This tab only to list just the current tab's requests.
- Raw request and response, including headers the browser adds such as cookies. Step through requests with previous / next.
- Edit and replay from the page itself, so its cookies and origin carry over. If that page is gone, send the request from the extension instead.
- Include / Exclude filter by method, host, URL, status, content type and kind.
- Optional document request capture, a Tab column showing which tab sent each request, popup or side panel.
- Nothing leaves your browser: no servers, no analytics.

## Getting started

1. Open the page you want to inspect and click the ReFetch icon in the toolbar (or press `Ctrl+Shift+X`, `Command+Shift+X` on macOS).
2. If ReFetch asks for site access, grant it and reload the page.
3. Press the record button (●) to start capturing. Capture is off by default; one click turns it on for all tabs until you turn it off or the browser restarts.
4. Use the page as usual. Requests from all tabs appear in the list as they finish. Turn on **This tab only** to list just the current tab's requests.

## Inspecting requests

- Click a row to see the raw request and response, including headers the browser adds (cookies, etc.). Streaming responses update as data arrives.
- Use the up/down buttons next to **Back** to move to the previous or next request.
- The **Status** column works like DevTools: `200 CORS` means the server answered but CORS blocked the page from reading the response, `(failed)` is a network error and `(canceled)` is an aborted request. Hover over it for details.
- Right-click the list header to show, hide or add columns (including request and response header columns, and the **Tab** column with the ID of the tab that sent each request). Drag a header to reorder it, or its edge to resize it.

![Request detail with previous/next](screenshots/detail.png)

![Detail of a CORS-blocked request](screenshots/cors.png)

## Editing and replaying

1. Open a request and click **Edit**.
2. Change the raw request: method, URL, headers or body.
3. Click **Send**. The request is sent again from the original page, so its cookies and origin still apply. Headers that a page cannot set itself, such as `Cookie` or `User-Agent`, are applied only to that one request.

Replayed requests are highlighted in orange in the list.

If the page that sent the request is gone (its tab was closed, or the frame is now on another origin), ReFetch offers **Send from extension**. The extension then sends the edited request itself. The page's CORS, cookie policy and Origin don't apply, and the headers shown in the editor, `Cookie` included, are sent as is; a request without a `Cookie` line gets the browser's normal cookies. Nothing is sent this way unless you choose it, and these requests are labelled "Sent from extension".

![Editing a raw request](screenshots/edit.png)

## Filtering

Click the funnel icon to open the filter.

- Set conditions on method, host (`*.example.com, localhost:*`), URL regex, status, content type and kind. Each condition can be **Include** or **Exclude**; empty conditions are ignored.
- Requests that don't match are hidden from the list, and the toolbar shows how many are hidden.
- Turn on **Don't store hidden requests** to drop them at capture time instead. They can't be shown again later, but they don't use up the 3,000 requests kept in total.

![Filter](screenshots/filter.png)

## Toolbar

| Button | What it does |
| --- | --- |
| ● Record | Start or stop capturing all tabs |
| Clear | Remove all captured requests, including other tabs' requests, even when This tab only is on |
| This tab only | List only the current tab's requests |
| Globe (Document requests) | Also capture page navigations and redirects |
| Funnel (Filter) | Open the filter |
| Open as panel / Switch to popup | Show ReFetch in the side panel (Firefox: sidebar) or as a popup |

Captured requests stay in your browser until you press Clear or the browser restarts; navigating, reloading or closing a tab doesn't remove them. Incognito/private windows, if you allow the extension there, share the same log. See the [privacy policy](PRIVACY.md) for details.
