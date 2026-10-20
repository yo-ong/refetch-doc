**English** | [한국어](README.ko.md)

# ReFetch

ReFetch is a browser extension for Chrome and Firefox that captures the fetch, XHR and EventSource requests of the current tab, shows them as raw HTTP, and lets you edit and resend them from the page itself.

- [Changelog](CHANGELOG.md)
- [Privacy policy](PRIVACY.md)

## Getting started

1. Open the page you want to inspect and click the ReFetch icon in the toolbar (or press `Ctrl+Shift+X`, `Command+Shift+X` on macOS).
2. If ReFetch asks for site access, grant it and reload the page.
3. Press the record button (●) to start capturing this tab. Capture is off by default and is turned on per tab.
4. Use the page as usual. Requests appear in the list as they finish.

## Inspecting requests

- Click a row to see the raw request and response, including headers the browser adds (cookies, etc.). Streaming responses update as data arrives.
- Use the up/down buttons next to **Back** to move to the previous or next request.
- The **Status** column works like DevTools: `200 CORS` means the server answered but CORS blocked the page from reading the response, `(failed)` is a network error and `(canceled)` is an aborted request. Hover over it for details.
- Right-click the list header to show, hide or add columns (including request and response header columns). Drag a header to reorder it, or its edge to resize it.

## Editing and replaying

1. Open a request and click **Edit**.
2. Change the raw request: method, URL, headers or body.
3. Click **Send**. The request is sent again from the original page, so its cookies and origin still apply. Headers that a page cannot set itself, such as `Cookie` or `User-Agent`, are applied only to that one request.

Replayed requests are highlighted in orange in the list.

## Filtering

Click the funnel icon to open the filter.

- Set conditions on method, host (`*.example.com, localhost:*`), URL regex, status, content type and kind. Each condition can be **Include** or **Exclude**; empty conditions are ignored.
- Requests that don't match are hidden from the list, and the toolbar shows how many are hidden.
- Turn on **Don't store hidden requests** to drop them at capture time instead. They can't be shown again later, but they don't use up the 1,000 requests kept per tab.

## Toolbar

| Button | What it does |
| --- | --- |
| ● Record | Start or stop capturing the current tab |
| Clear | Remove the requests captured in this tab |
| Pin (Preserve log) | On by default: keep requests when the page navigates or reloads. Turn it off to start fresh on every page, like DevTools |
| Globe (Document requests) | Also capture page navigations and redirects |
| Funnel (Filter) | Open the filter |
| Open as panel / Switch to popup | Show ReFetch in the side panel (Firefox: sidebar) or as a popup |

Captured requests stay in your browser and are cleared when the browser restarts. See the [privacy policy](PRIVACY.md) for details.
