# iOS Accessibility Guidelines

## Animation

- __Using Animation__ - Use of animation should be reduced or disabled altogether where the [`isReduceMotionEnabled`](https://developer.apple.com/documentation/uikit/uiaccessibility/1615133-isreducemotionenabled) flag is set. Overuse of animation can induce headaches in individuals who are particularly sensitive to motion such as those who suffer from a vestibular disorder.

Affects: [Visual](#Visual)


References: 

- [Reduce screen motion on your iPhone, iPad, or iPod touch](https://support.apple.com/en-gb/HT202655)
- [Understanding Success Criterion 2.3.3: Animation from Interactions](https://www.w3.org/WAI/WCAG21/Understanding/animation-from-interactions.html)

## Buttons
- __Buttons with Images__ As with [`UIImageView`](https://developer.apple.com/documentation/uikit/uiimageview) it is important to ensure that the [`accessibilityLabel`](https://developer.apple.com/documentation/objectivec/nsobject/1615181-accessibilitylabel) property is set to a meaningful string otherwise the image's file name will be read out which can be particularly unhelpful, and moreover confusing, to visually-impaired users attempting to discern the content of the image. If the [`UIButton`](https://developer.apple.com/documentation/uikit/uibutton) is in a XIB or storyboard then [Xiblint](https://github.com/lyft/xiblint) can be used to detect `UIButton` elements where an image has been set and raise a warning if a value for the `accessibilityLabel` property has not been specified.

## Consistency
- __Consistent Placement of Elements__ Consistent placement of elements onscreen reduces cognitive load by helping users predict where to find information in the interface. Inconsistent placement can result in distraction or even confusion when the user finds that an element is not where expected it to be.

Affects: [Cognitive](#Cognitive)

## Images

- __Images Containing Text__ - Images containing text should be avoiding as the text in these images cannot be read out by VoiceOver nor will it respect the user's text size preference. 

Affects: [Visual](#Visual)

- __Images Conveying Meaning__ - Images should not be used as the sole means of conveying information. Solution: Ensure that an accessibility label is set for all images, otherwise VoiceOver will read out the name of the image file. 

Affects: [Visual](#Visual)

Example:

```
let wishlistIconImage = UIImage(named: "wishlist-icon")
let wishlistIcon = UIImageView(image: wishlistIconImage)
wishlistIcon.isAccessibilityEnabled = true
wishlistIcon.accessibilityLabel = "This product is currently in your wishlist"
```

- __Images Without Accessibility Labels__ - It is particularly important to ensure that [`UIImageView`](https://developer.apple.com/documentation/uikit/uiimageview) instances have the [`accessibilityLabel`](https://developer.apple.com/documentation/objectivec/nsobject/1615181-accessibilitylabel) property set to a meaningful string otherwise the image's file name will be read out which can be particularly unhelpful, and moreover confusing, to visually-impaired users attempting to discern the content of the image. If the [`UIImageView`](https://developer.apple.com/documentation/uikit/uiimageview) is in a XIB or storyboard then [Xiblint](https://github.com/lyft/xiblint) can be used to raise a warning if the `accessibilityLabel` property has not been set.

Affects: [Visual](#Visual)

## Interaction
- __Touch Area for Interactive Elements__ - The [iOS Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/ios/visual-design/adaptivity-and-layout/) recommend a minimum tappable area of 44pt x 44pt for all controls. This is because for users with motor or visual impairments accuracy can be more difficult. Accuracy can also be a difficulty for younger users. 
- __Hidden or Inactive Elements__ - These should be hidden from assistive technologies

Affects: [Physical](#Physical), [Visual](#Visual) 

References: 

- [iOS Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/ios/visual-design/adaptivity-and-layout/)

## Navigation
- __Screen Updates__ - Whenever screen content is updated, the user should be notified via VoiceOver by posting an accessibility notification using [`UIAccessibilityPostNotification`](https://developer.apple.com/documentation/uikit/uiaccessibility/1615194-post) as users with a visual impairments may not be aware that the layout has refreshed. This may result in confusion if page elements have changed location or disappeared altogether without warning. Via the [`UIAccessibility.Notification`](https://developer.apple.com/documentation/uikit/uiaccessibility/notification) argument it is possible to indicate whether content was updated as the result of a [page scroll](https://developer.apple.com/documentation/uikit/uiaccessibility/notification/1620190-pagescrolled) or [change in layout](https://developer.apple.com/documentation/uikit/uiaccessibility/notification/1620186-layoutchanged).

Affects: [Visual](#Visual) 


## Text & Color

- __Blur & Transparency__ - Use of blur and transparency should be reduced or disabled altogether where the [`isReduceTransparencyEnabled`](https://developer.apple.com/documentation/uikit/uiaccessibility/1615074-isreducetransparencyenabled) flag is set. For users with low vision conditions, the use of blur and transparency can have a negative impact on the legibility of text and in some cases induce eye strain. Solution: Consider using a faded color in place instead. 

Affects: [Visual](#Visual)

- __Contrast__

Affects: [Visual](#Visual)

- __Use of Color__ - Color should not be used as the sole means of conveying information as users with color blindness may not be able to perceive the difference in color.

Affects: [Visual](#Visual)

# Categories of impairment: 
### Auditory
### Cognitive 
### Physical
### Speech
### Visual

# Software Supporting Accessibility

## Libraries
- [Capable](https://github.com/chrs1885/Capable) - Keep track of accessibility settings and enable users with disabilities to use your app.
- [TypographyKit](https://github.com/rwbutler/TypographyKit) - Consistent & accessible visual styling on iOS with support for Dynamic Type.

## Tools
- [Xiblint](https://github.com/lyft/xiblint) - A tool by [Lyft](https://github.com/lyft) for linting storyboard and XIB files. Able to validate that UIImageViews and UIButtons with images have an accessibility label set.