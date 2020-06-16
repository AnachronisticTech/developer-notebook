# Customising the page dots

Customisation of the page controller dots can be achieved by modifying `UIPageControl.appearance()`.

```swift
let appearance = UIPageControl.appearance()
appearance.pageIndicatorTintColor = UIColor.red.withAlphaComponent(0.6)
appearance.currentPageIndicatorTintColor = .red
appearance.backgroundColor = .yellow
```

[Reference](https://stackoverflow.com/a/55835601)