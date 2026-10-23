# UI and live checks

## Screenshots

Without a browser or screenshot tool, report "UI not verified" and list the views a human should check.

- Run the app locally (or in a preview environment) with realistic data.
- One screenshot per changed view and per state that changed (empty, loading, error, full).
- Look at each screenshot yourself before attaching. A screenshot that shows the wrong page, an old build or only part of the change is worse than none.
- For bug fixes: before and after, same scenario, same data. Take "after" first, confirm it shows the fix, then "before".
- Upload to the MR description, under the matching section.

## Browser checks

- Check the browser console and network tab for errors, not only the visible page.
- Test the flow a user follows (click path), not only a direct URL load.

## Live checks after deploy

1. Confirm the running version: image tag or commit of the running pods, compared with the merge commit.
2. Confirm migrations ran (schema version) before the new code serves traffic.
3. Smoke test on an internal team or tenant first, then one customer tenant, then all.
4. Check the live result: call the endpoint and read the body, load the page, find the log line.
5. Report: where it is live, how it was verified, which environments still need a promote.
