---
url: https://www.youtube.com/watch?v=M2LMd_ZGzDU
publish: true
tags:
  - android
  - compose
  - article
---
# [Youtube : Is THIS the Future of Jetpack Compose UI?]([Is THIS the Future of Jetpack Compose UI?](https://www.youtube.com/watch?v=M2LMd_ZGzDU))

> ["Remote Compose is framework to create UI for remote surfaces"](https://developer.android.com/jetpack/androidx/releases/compose-remote)

Remote Compose is an android official support for [[Server Side Rendering]] for Jetpack Compose. It's in very early stages, but it's an official API that can replace various server-side rendering libraries.

### So, how does it work?

It's pretty much the same as making a composable on the client side, except with some different APIs and functions. But the declarative style of Compose is the same.

```kotlin
fun getRemoteComposeUi() : ByteArray {
	val context = RemoteComposeContext(
		...
	) {
		root {
			column(
				modifier = RecordingModifier()
					.fillMaxSize(),
			) {
				...
			}
		}
	}
}
```

### Where this could be useful

Server-side rendering allows the application to change the UI from the server. A simple change like the color of a button can be done without redistributing APKs. Also, from the UX perspective, it's going to be much easier to do [[A/B Test]] in a native Android application.

With the official Compose support from the Android team, animation can be implemented in a Compose-way without complicated workarounds. Also, this opened the possibility of hoisting the state even to the server.

### Drawbacks/TradeOff

Because Remote Compose is server-side rendering, it shares its downsides. It's highly dependent on the network and has performance overhead compared to the original Compose.

### Personal Thoughts

I am not very familiar with server-side rendering concepts yet, so it is hard to imagine real use cases immediately.  Still, it's interesting to see the Android team experimenting with new directions. I am curious how this would interact with existing Compose state management in the future.