# Expo Linking: Android Background Deep Link Issue

This repository demonstrates an uncommon bug with Expo's `Linking` API on Android.  When the app is launched from a deep link while already running in the background, the `Linking.addEventListener` callback may not be triggered.  This issue does *not* occur when the app is completely closed; only when it's already running in the background.

## Bug Description

The `Linking.addEventListener` function is expected to fire whenever a URL is received, regardless of the app's state.  However, in this specific scenario (app in background), it inconsistently fails to trigger, causing deep link handling to break.

## Reproduction Steps

1. Run the `bug.js` example on an Android device or emulator.
2. Send a deep link to the app while it's running in the background (minimized but still running).
3. Observe that the console log within `Linking.addEventListener` does not always print the received URL.
4. For comparison, completely close the app and repeat step 2.  The event listener should consistently fire in this case.

## Solution

The solution involves using a more robust approach to handle deep links. The `bugSolution.js` file provides a working solution that uses additional state management and background notification handling to ensure reliable deep link processing. This improved implementation provides a more resilient approach to deep link handling regardless of the app's state.