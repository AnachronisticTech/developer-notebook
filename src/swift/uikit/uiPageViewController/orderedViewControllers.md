# orderedViewControllers

The `orderedViewControllers: [UIViewController]` variable contains a generated list of the view controllers to be used in a [`UIPageViewController`](../uiPageViewController.md). The view controllers are displayed in the order in which they appear in the list returned by the `orderedViewControllers` variable.

```swift
private(set) var orderedViewControllers: [UIViewController] = {
    func newViewController(_ name: String) -> UIViewController {
      	return UIStoryboard(name: "Main", bundle: nil).instantiateViewController(withIdentifier: "page")
    }
    let viewOrder = ["page1", "page2", "page3"]
    let controllers = viewOrder.map { newViewController($0) }
    return controllers
}()
```

The above example uses a scoped function `newViewController(_:) -> UIViewController` to instantiate a new view controller using the storyboard identifier `page`. `viewOrder.map { newViewController($0) }` assigns a new list of view controllers to the `controllers` variable using the strings in `viewOrder`. Notice, however, that these strings are never passed to the newly instantiated view controllers. The below example shows how to send the data to a view controller, though this is not a necessary requirement of the `UIPageViewController`.

```swift
// Assume pages use a view controller similar to this
class ViewController: UIViewController {
    var title: String = "default value"

    // rest of view controller declaration
}

class PageViewController: UIPageViewController {
    private(set) var orderedViewControllers: [UIViewController] = {
        func newViewController(_ name: String) -> UIViewController {
            return UIStoryboard(name: "Main", bundle: nil).instantiateViewController(withIdentifier: "page")
        }
        let viewOrder = ["page1", "page2", "page3"]
        let controllers = viewOrder.map { newViewController($0) as! ViewController }
        for i in 0 ..< controllers.count {
            controllers[i].page = viewOrder[i]
        }
        return controllers
    }()

    // rest of page view controller declaration
}
```

