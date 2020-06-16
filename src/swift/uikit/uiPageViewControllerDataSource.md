# UIPageViewControllerDataSource

The `UIPageViewControllerDataSource` protocol is used to determine which view controller to present to the user. It can be implemented using:

```swift
class PageViewController: UIPageViewController, UIPageViewControllerDataSource {
    // Class definition
  
    // Extension function implementations
}
```

or separated for clarity using extensions:

```swift
class PageViewController: UIPageViewController {
    // Class definition
}

extension PageViewController: UIPageViewControllerDataSource {
    // Extension function implementations
}
```