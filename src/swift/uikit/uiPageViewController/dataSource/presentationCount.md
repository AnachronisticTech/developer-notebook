# presentationCount

To show page dots in a `UIPageViewController` the `presentationCount(for:) -> Int` function informs the controller data source as to how many pages there are, and how many dots should be shown.

```swift
extension PageViewController: UIPageViewControllerDataSource {
  	func presentationCount(for pvc: UIPageViewController) -> Int {
        return orderedViewControllers.count
    }
}
```

