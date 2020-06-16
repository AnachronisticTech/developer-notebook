# viewControllerBefore

The `pageViewController(pageViewController:, viewControllerBeforeViewController:)` function is used to specify the view controller to present when moving backwards through the pages.

```swift
func pageViewController(
  pageViewController: UIPageViewController, 
  viewControllerBeforeViewController viewController: UIViewController
) -> UIViewController? {
    guard let viewControllerIndex = orderedViewControllers.indexOf(viewController) else {
      	return nil
    }

    let previousIndex = viewControllerIndex - 1

    guard previousIndex >= 0 else {
      	return nil
    }

    guard orderedViewControllers.count > previousIndex else {
      	return nil
    }

    return orderedViewControllers[previousIndex]
}
```

To loop back to the last view controller when moving backwards from the first view controller in the sequence, use the modified implementation below.

```swift
func pageViewController(
  pageViewController: UIPageViewController, 
  viewControllerBeforeViewController viewController: UIViewController
) -> UIViewController? {
    guard let viewControllerIndex = orderedViewControllers.indexOf(viewController) else {
      	return nil
    }

    let previousIndex = viewControllerIndex - 1

    // User is on the first view controller and swiped left to loop to the last view controller.
    guard previousIndex >= 0 else {
      	return orderedViewControllers.last
    }

    guard orderedViewControllers.count > previousIndex else {
      	return nil
    }

    return orderedViewControllers[previousIndex]
}
```

