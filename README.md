
<p align="center">
  <img src="promo/recent_left_colorful.png"  style="width: 220px;" width="220" /> 
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="promo/left_scroll_colorful.gif"  style="width: 280px;" width="280" /> 
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="promo/recent_left_with_gap_colorful.png"  style="width: 260px;" width="260" />
</p>

<p align="center">
  <img src="promo/recent_right_colorful.png"  style="width: 220px;" width="220" /> 
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="promo/right_scroll_colorful.gif"  style="width: 280px;" width="280" /> 
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="promo/recent_right_with_gap_colorful.png"  style="width: 260px;" width="260" />
</p>



<p align="center">
    <a href="https://twitter.com/Kiranjasvanee">
        <img src="https://img.shields.io/badge/contact-@kiranjasvanee-blue.svg?style=flat"
             alt="Twitter">
    </a>
    <a href="https://github.com/KiranJasvanee/OnlyPictures/blob/master/LICENSE">
        <img src="https://img.shields.io/badge/license-MIT-blue.svg?style=flat" alt="Codecov" />
    </a>
    <a href="https://cocoapods.org/pods/OnlyPictures">
        <img src="https://img.shields.io/cocoapods/v/OnlyPictures.svg?style=flat"
             alt="Pods Version">
    </a>
    <a href="http://cocoapods.org/pods/OnlyPictures/">
        <img src="https://img.shields.io/cocoapods/p/OnlyPictures.svg?style=flat"
             alt="Platforms">
    </a>
    <a href="https://github.com/KiranJasvanee/OnlyPictures/issues">
        <img src="https://img.shields.io/github/issues/KiranJasvanee/OnlyPictures.svg"
             alt="Issues">
    </a>
    <a href="https://github.com/KiranJasvanee/OnlyPictures">
        <img src="https://img.shields.io/github/forks/KiranJasvanee/OnlyPictures.svg"
             alt="Forks">
    </a>
    <a href="https://github.com/KiranJasvanee/OnlyPictures">
        <img src="https://img.shields.io/github/stars/KiranJasvanee/OnlyPictures.svg"
             alt="Stars">
    </a>
    <a href="https://github.com/KiranJasvanee/OnlyPictures">
        <img src="https://img.shields.io/badge/Language-Swift-yellow.svg"
             alt="Stars">
    </a>
</p>

----------------

### Installation

OnlyPictures is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'OnlyPictures'
```

### Usage

Add `UIView` in your outlet, select it and go to `Properties -> Identity Inspector`,  add `OnlyHorizontalPictures` in `class property`. `OnlyVerticalPictures` about to release soon.

<img src="promo/UIVIew_outlet.png"  style="width: 220px;" width="220" /> &nbsp;&nbsp;&nbsp;&nbsp; `->` &nbsp;&nbsp;&nbsp;&nbsp; <img src="promo/identity_inspector_class_property_assignment.png"  style="width: 220px;" width="220" /> 

Create `instance` of this outlet as below.
```
@IBOutlet weak var onlyPictures: OnlyHorizontalPictures!
```

Use `DataSource` for data assignment & `Delegate` to get indication of action performed in pictures.
```
onlyPictures.dataSource = self
onlyPictures.delegate = self
```

#### DataSource Methods

```
extension ViewController: OnlyPicturesDataSource {

    // ---------------------------------------------------
    // returns the total no of pictures
    
    func numberOfPictures() -> Int {
        return pictures.count
    }
    
    // ---------------------------------------------------
    // returns the no of pictures should be visible in screen. 
    // In above preview, Left & Right formats are example of visible pictures, if you want pictures to be shown without count, remove this function, it's optional.
    
    func visiblePictures() -> Int {
        return 6
    }
    
    // ---------------------------------------------------
    // return the images you want to show.
    
    func pictureViews(index: Int) -> UIImage {
        return pictures[index]
    }
}
```
#### Delegate Methods
```
extension ViewController: OnlyPicturesDelegate {
    
    // ---------------------------------------------------
    // receive an action of selected picture tap index
    
    func pictureView(_ imageView: UIImageView, didSelectAt index: Int) {
        
    }
    
    // ---------------------------------------------------
    // receive an action of tap upon count
    
    func pictureViewCountDidSelect() {
        
    }
    
    // ---------------------------------------------------
    // receive a count, incase you want to do additionally things with it.
    // even if your requirement is to hide count and handle it externally with below fuction, you can hide it using property `isVisibleCount = true`.
    
    func pictureViewCount(value: Int) {
        print("count value: \(value)")
    }
    
    
    // ---------------------------------------------------
    // receive an action, whem tap occures anywhere in OnlyPicture view.
    
    func pictureViewDidSelect() {
        
    }
}
```

#### Properties

##### .order

- Pictures works based on `LIFO` - Last In First Out, means last added will be shown at top (recent). 
- If your array contains pictures in `ascending`, it will show last picture OR in other words last appended picture at top (recent). 
- If your array contains pictures in `descending`, set `.order property` to `.descending` to show first picture at top (recent). 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  .ascending &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;   .descending

&nbsp;&nbsp;&nbsp; <img src="promo/order_property/ascending.png"  style="width: 160px;" width="180" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  <img src="promo/order_property/descending.png"  style="width: 180px;" width="180" /> 

```
onlyPictures.order = .descending
```

##### .recentAt
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  .left &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;   .right

&nbsp;&nbsp;&nbsp; <img src="promo/recent_left_colorful.png"  style="width: 160px;" width="180" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  <img src="promo/recent_right_colorful.png"  style="width: 180px;" width="180" /> 

```
onlyPictures.recentAt = .left
```


##### .alignment
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   .left &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    .center    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    .right

<img src="promo/alignment_property/left.png"  style="width: 280px;" width="280" /> &nbsp; <img src="promo/alignment_property/center.png"  style="width: 280px;" width="280" /> &nbsp; <img src="promo/alignment_property/right.png"  style="width: 280px;" width="280" />

```
onlyPictures.alignment = .left
```


##### .countPosition
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  .right &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;   .left

&nbsp;&nbsp;&nbsp; <img src="promo/recent_left_colorful.png"  style="width: 160px;" width="180" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  <img src="promo/recent_right_colorful.png"  style="width: 180px;" width="180" /> 

```
onlyPictures.countPosition = .right
```


##### .gap
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.gap = 20 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    .gap = 36     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    .gap = 50 

&nbsp;&nbsp;&nbsp;&nbsp; <img src="promo/gap_property/gap_20.png"  style="width: 120px;" width="120" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="promo/gap_property/gap_36.png"  style="width: 180px;" width="180" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="promo/gap_property/gap_50.png"  style="width: 220px;" width="220" />

```
onlyPictures.gap = 36
```

##### .spacing
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.spacing = 0 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.spacing = 2     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.spacing = 4 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.spacing = 4 with white color 

<img src="promo/spacing_property/spacing_0.png"  style="width: 180px;" width="180" /> &nbsp;&nbsp; <img src="promo/spacing_property/spacing_2.png"  style="width: 200px;" width="200" /> &nbsp;&nbsp; <img src="promo/spacing_property/spacing_4.png"  style="width: 220px;" width="220" /> &nbsp;&nbsp; <img src="promo/spacing_property/spacing_4_with_white.png"  style="width: 220px;" width="220" />

```
onlyPictures.spacing = 2
```

##### .spacingColor
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; .spacingColor = .gray &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; .spacingColor = .white

<img src="promo/spacingColor_property/spacing_4_with_gray.png"  style="width: 220px;" width="220" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="promo/spacingColor_property/spacing_4_with_white.png"  style="width: 220px;" width="220" />

```
onlyPictures.spacingColor = UIColor.white
```

##### .imageInPlaceOfCount

- Set image in place of count. If this property set, count properties won't effect.

<img src="promo/imageInPlaceOfCount_property/imageInPlaceOfCount_1.png"  style="width: 220px;" width="220" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="promo/imageInPlaceOfCount_property/imageInPlaceOfCount_2.png"  style="width: 260px;" width="260" />

```
onlyPictures.imageInPlaceOfCount = UIImage(named:"image_name")
```

#### Properties for count

##### .backgroundColorForCount

<img src="promo/backgroundColorForCount_property/backgroundColorForCount.png"  style="width: 220px;" width="220" /> 

```
onlyPictures.backgroundColorForCount = .orange
```

##### .textColorForCount

<img src="promo/textColorForCount_property/textColorForCount.png"  style="width: 220px;" width="220" /> 

```
onlyPictures.textColorForCount = .red
```

##### .fontForCount

<img src="promo/fontForCount_property/fontForCount.png"  style="width: 220px;" width="220" /> 

```
onlyPictures.fontForCount = UIFont(name: "HelveticaNeue", size: 18)!
```

##### .isHiddenVisibleCount
- To hide count, set `.isHiddenVisibleCount = true`. But you can receive count in a following funtion of `OnlyPicturesDelegate` - `pictureViewCount(value: Int)`. 
```
onlyPictures.isHiddenVisibleCount = true
```

### Author

Kiran Jasvanee, kiran.jasvanee@gmail.com

### License

OnlyPictures is available under the MIT license. See the LICENSE file for more info.
