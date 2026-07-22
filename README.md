# Privacy policy — hosting it and matching the Play Data safety form

`index.html` is a complete, self-contained privacy policy for STRATA. No build step, no
dependencies — drop it on any static host and the URL works.

## Before you publish: one required edit

Open `index.html` and replace **both** occurrences of `REPLACE_WITH_YOUR_EMAIL` with a real
contact address. Google requires a working contact method in the policy, and a reviewer will
click it.

```bash
# from this folder — swap in the address you want to publish
sed -i '' 's/REPLACE_WITH_YOUR_EMAIL/you@example.com/g' index.html
```

Consider whether you want your personal address public. A dedicated alias (e.g.
`strata.app@gmail.com`) is the usual choice, and you will need a support email for the Play
listing anyway.

## Fastest path to a public URL: GitHub Pages (free, permanent, yours)

1. Create a **public** repo on GitHub, e.g. `strata-privacy`.
2. Upload `index.html` to the root (drag-and-drop in the browser works).
3. Repo **Settings → Pages → Build and deployment → Deploy from a branch**, pick
   `main` and `/ (root)`, Save.
4. Wait ~1 minute. Your URL is:
   ```
   https://<your-username>.github.io/strata-privacy/
   ```
5. Open it in a private browser window to confirm it loads **without logging in**. Paste it
   into the Play Console field.

Alternatives if you prefer: **Netlify Drop** (drag the folder onto
[app.netlify.com/drop](https://app.netlify.com/drop), instant URL), **Cloudflare Pages**, or
your own domain if you have one.

### It must be publicly reachable
Google fetches the URL automatically. A link behind a login, a Google Doc set to "restricted",
a Dropbox preview page, or a file that 404s will get the listing **rejected**. Always test in
a private window.

## The Data safety form must match this policy

In the Play Console, **Data safety** is a separate questionnaire from the privacy policy URL,
and Google checks the two against each other. Based on what the app actually does (verified
against the source, not assumed), the answers are:

| Question | Answer |
|---|---|
| Does your app collect or share any of the required user data types? | **No** — nothing is transmitted to the developer. There is no backend, no analytics, no account. |
| Is all user data encrypted in transit? | **Yes** — every request is HTTPS. |
| Do you provide a way for users to request data deletion? | **Yes / not applicable** — all data is on-device and removed by uninstalling. |
| Data types: Location | Accessed on-device for app functionality. **Not collected** by the developer. |
| Data types: Personal info, Photos, Contacts, Files, Messages | **None** — no camera plugin, no contacts, no file access. |
| Advertising or analytics | **None.** |

### The one nuance to be aware of

Google defines "collected" as *transmitted off the device*. STRATA does not send anything to
**you**, the developer — but tapping a point does send those coordinates to Macrostrat and to
the tile servers in order to fetch the data. That is disclosed plainly in **section 3** of the
policy.

Google's guidance generally treats data used only to serve the user's immediate request, not
stored and not reused, as ephemeral processing that does not need to be declared as
"collection." That is exactly what STRATA does. If you would rather be maximally conservative,
you can additionally tick **Location → Approximate/Precise → collected → App functionality**
and mark it *not shared* and *ephemeral*. Over-declaring is safe; under-declaring is what gets
apps pulled.

## Reusing this for the mushroom app

The policy is accurate for STRATA specifically. When Mushroom Map ships, the third-party
table in section 5 changes — GBIF, iNaturalist, Open-Meteo, and the land-cover host would be
added, and Open-Meteo/GBIF receive coordinates the same way Macrostrat does. Update section 5
and the footer attributions before reusing it, and keep a separate URL per app.
