# presentationIndex

To show page dots in a `UIPageViewController` the `presentationIndex(for:) -> Int` function informs the controller data source as to which page is currently presented.

```swift
extension PageViewController: UIPageViewControllerDataSource {
	func presentationIndex(for pvc: UIPageViewController) -> Int {
  	guard let firstViewController = viewControllers?.first, let firstViewControllerIndex = orderedViewControllers.firstIndex(of: firstViewController) else {
            return 0
        }
        
        return firstViewControllerIndex
    }
}
```


