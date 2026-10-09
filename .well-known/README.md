# Android App Links

`assetlinks.json` is what lets a `https://www.chithraguptha.site/app/...` link
open Manvori instead of a browser tab. Android fetches it at install time and
checks the signing certificate of the installed app against the fingerprints
listed here. If it does not match, the link still works — it just opens the
website. That is a fallback, not a failure.

## The fingerprint currently listed

It is the **Android debug keystore**. That is not a mistake today: the app's
release build is still signed with the debug key —
`android/app/build.gradle.kts` has

```kotlin
signingConfig = signingConfigs.getByName("debug")
```

so the debug fingerprint is the fingerprint of every build that exists.

## What has to change before the Play Store

Two things, and neither is optional:

1. **A real release keystore.** Generate one, keep it somewhere it cannot be
   lost — losing it means never updating the app again under the same listing —
   and point the release `signingConfig` at it. Then add its fingerprint here.

2. **Play App Signing.** Google re-signs the uploaded bundle with a key it
   holds, so the certificate on a user's phone is Google's, not yours. Its
   fingerprint is in Play Console under **Setup → App integrity → App signing
   key certificate**, and it must be added here too.

Both fingerprints can sit in the array at once, which is what you want: side
loaded builds verify against yours, Play installs verify against Google's.

## Checking it

```bash
curl -s https://www.chithraguptha.site/.well-known/assetlinks.json | python3 -m json.tool
```

It must be served over https, as `application/json`, with no redirect. GitHub
Pages serves files from `.well-known/` as-is, which is why this sits at the
repository root.

Then, on a device:

```bash
adb shell pm verify-app-links --re-verify com.chithraguptha.manvori
adb shell pm get-app-links com.chithraguptha.manvori
```

`verified` against the domain is the answer you want.
