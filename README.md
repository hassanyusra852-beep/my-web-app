# my-web-app

Earmark mirrors student coursework from Google Classroom. It displays only coursework returned by the signed-in student's Google Classroom account; it does not generate, infer, or save additional units.

## Run

Serve this folder locally:

```sh
python3 -m http.server 4173
```

Then open <http://localhost:4173>. The site redirects to the Classroom coursework view. OAuth sign-in requires a local or deployed web server; opening the HTML directly from disk is not supported.

## Google Classroom setup

1. Create a Google Cloud project and enable the Google Classroom API.
2. Configure the OAuth consent screen and create an OAuth client ID for a Web application.
3. Add the site's exact origin, such as `http://localhost:4173`, to Authorized JavaScript origins.
4. Open the site, use the settings control to enter the OAuth client ID, and connect the student's Google account.

The app requests read-only course and coursework access. Google Workspace administrators may need to approve the OAuth app or its scopes. The client ID is stored in this browser; access tokens and returned coursework are kept in memory only and are cleared when the page is reloaded or disconnected. A sync failure clears the displayed units instead of retaining stale results.
