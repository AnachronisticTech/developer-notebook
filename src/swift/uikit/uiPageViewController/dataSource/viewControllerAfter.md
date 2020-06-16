# viewControllerAfter

The `pageViewController(pageViewController:, viewControllerAfterViewController:)` function is used to specify the view controller to present when moving forwards through the pages.

```swift
func pageViewController(
  pageViewController: UIPageViewController, 
  viewControllerAfterViewController viewController: UIViewController
) -> UIViewController? {
  guard let viewControllerIndex = orderedViewControllers.indexOf(viewController) else {
    	return nil
  }

  let nextIndex = viewControllerIndex + 1
  let orderedViewControllersCount = orderedViewControllers.count

  // User is on the last view controller and swiped right to loop to the first view controller.
  guard orderedViewControllersCount != nextIndex else {
    	return orderedViewControllers.first
  }

  guard orderedViewControllersCount > nextIndex else {
    	return nil
  }

  return orderedViewControllers[nextIndex]
}
```

To loop back to the first view controller when moving forwards from the last view controller in the sequence, use the modified implementation below.

```swift
func pageViewController(
  _ pageViewController: UIPageViewController, 
  viewControllerAfter viewController: UIViewController
) -> UIViewController? {
  guard let viewControllerIndex = orderedViewControllers.firstIndex(of: viewController) else {
    	return nil
  }

  let nextIndex = viewControllerIndex + 1
  let orderedViewControllersCount = orderedViewControllers.count

  // User is on the last view controller and swiped right to loop to the first view controller.
  guard orderedViewControllersCount != nextIndex else {
    	return orderedViewControllers.first
  }

  guard orderedViewControllersCount > nextIndex else {
    	return nil
  }

  return orderedViewControllers[nextIndex]
}
```