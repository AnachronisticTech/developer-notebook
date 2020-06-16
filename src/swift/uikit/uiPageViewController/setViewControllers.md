# setViewControllers

The `setViewControllers(_:, direction:, animated:, completion:)` function is used to set the view controller to present to the user.

This can be used to set the initial view controller to present when the controller first loads.

```swift
class PageViewController: UIPageViewController {
	  override func viewDidLoad() {
        super.viewDidLoad()
  
        if let firstViewController = orderedViewControllers.first {
            setViewControllers(
                [firstViewController],
                direction: .forward,
                animated: true,
                completion: nil
            )
        }
    }
}
```

