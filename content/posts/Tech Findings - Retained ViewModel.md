---
tags:
  - android
  - compose
  - article
url: https://medium.com/proandroiddev/viewmodel-is-deprecated-77a4caa9b359
publish: true
---
# [Article : ViewModel is deprecated - *not really](https://medium.com/proandroiddev/viewmodel-is-deprecated-77a4caa9b359)

The author of the article introduces an interesting idea: Replace the ViewModel with the `retain` API. 

> What is `retain` API?
> 
> It retains a value across the configuration changes like the `rememberSaveable`. But the difference is `retain` does not require a value to be serializable. Thus, any kind of object can be retained.

The article starts from the the idea of doing EVERYTHING within Compose environment. Since the ViewModel was originally created before the era of Compose, while it works fine, the ViewModel and Compose are living side by side in different lifecycle.

Before `retain` API, developers did not have much choice but to use the ViewModel. But some developers are looking for other way with this newly introduced API, and the article is introducing one.
## How to replace the ViewModel?

To have a object that aligns with the Compose lifecycle, `retain` life cycle to be exact, extends the `RetainObserver` to get the lifecycle callback.

```kotlin
abstract class RetainedViewModel : RetainObserver {
    val viewModelScope = CoroutineScope(SupervisorJob() + Dispatchers.Main.immediate)
    
    override fun onRetired() {
        clear()
    }

    private fun clear() {
        onCleared()
        viewModelScope.cancel()
    }

    protected open fun onCleared() {
        // override in subclasses for cleanup
    }
}
```

## ViewModel is more complex than you think

That is not all. You have to make viewmodel factory for retained ViewModel to be work with dependency injection, come up with a replacement for `savedStatehandle` to survive process death, and manage values manually on navigation since it will be cleared when the screen goes into back stack.

## So what is retained ViewModel a bad idea?

> [`retain` can also be used to build an in-house "`ViewModel`-like" API.](https://developer.android.com/develop/ui/compose/state-lifespans#retain-viewmodel)

The official document also discusses about this idea. Although you *can* make one to replace the existing ViewModel, but there will be a lot of task ahead of you if you wish to provide same functionality as the ViewModel.

## Personal thoughts

I'd like to use `retain` API where it fits. Generally on the objects that requires survival between configuration changes but cannot be serialized, and large objects that can have performance issues on serializing.