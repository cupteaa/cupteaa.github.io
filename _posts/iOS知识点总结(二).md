## UIScrollView
- 需要掌握
  - UIScrollView的常见属性
  - UIScrollView的常用代理方法
  - UIScrollView的缩放
  - UIScrollView和UIPageControl的分页
  - NSTimer的使用

### 基本概念
#### 什么是UIScrollView
- 移动设备的屏幕大小有限,展示的内容也有限
- 当展示的内容超出屏幕大小时,用户就需要用滚动手势来查看屏幕以外的内容
- 普通的UIView不具备滚动功能
- UIScrollView是一个能够滚动的视图控件,可以展示大量的内容

#### UIScrollView的基本使用
- UIScrollView的使用很简单
 - 将需要展示的内容添加到UIScrollView上
 - 设置contentSize属性,告诉UIScrollView的内容范围,即滚动范围

#### UIScrollView无法滚动的可能原因
- 没有设置contentSize
- scrollEnable = NO
- userInteractionEnable = NO 接收不到触摸事件

#### UIScrollView的常见属性
- 表示UIScrollView滚动的位置(内容左上角与UIScrollView左上角的差值)
```objcetivec
@property(nonatomic)CGPoint contentOffset;
```
- 内容尺寸
```objcetivec
@property(nonatomic)CGSize contentSize;
```
- 在UIScrollView四周增加额外的滚动区域,用来避免内容被其他控件挡住
```objcetivec
@property(nonatomic)UIEdgeInsets contentInset
```
- 是否需要弹簧效果
```objcetivec
@property(nonatomic)BOOL bounces;
```
- 是否能滚动
```objcetivec
@property(nonatomic,getter=isScrollEnable)BOOL scrollEnable;
```
- 水平滚动条
```objcetivec
@property(nonatomic)BOOL showsHorizontalScrollIndicator;
```
- 垂直滚动条
```objcetivec
@property(nonatomic)BOOL showsVerticalScrollIndicator;
```

### delegate
#### UIScrollView的delegate
- 很多时候我们想在UIScrollView正在滚动,或者滚动到某个位置,或者停止滚动时做一些特定的操作
- 要完成上述过程,需要监听UIScrollView的整个滚动过程
- 当UIScrollView发生一系列的滚动操作时,会自动通知它的delegate对象,给它的代理发送响应的消息,让代理得知它的滚动情况
- 也就是说要想监听UIScrollView的滚动过程,必须先给UIScrollView设置一个代理对象,然后通过代理得知它的滚动过程
```objcetivec
@property(nonatomic,assign) id<UIScrollViewDelegate> delegate;
```
- 当用户开始拖拽/滚动到具体某个位置/停止拖拽时 发送特定消息到delegate
- 在OC中,发送消息就是调用方法
- 在精确一点就是分别调用以下方法
```objcetivec
scrollViewWillBeginDragging:
scrollViewDicScroll:
scrollViewDidEndDragging:willDecelerate:
```
- 可以看出,要想成为UIScrollView是有条件的,必须实现对应的方法才能监听滚动过程
- 成为代理的条件:遵守UIScrollViewDelegate协议,实现相应的方法

#### UIScrollView和控制器
- 一般情况下,就是设置所在控制器为UIScrollView的delegate
- 方法有两种
 - 通过代码 self.scrollView.delegate = self
 - 通过拖线 右击UIScrollView
- 然后遵守代理协议 UIScrollViewDelegate
- 最后实现相应的方法

#### 内容缩放
- UIScrollView不仅能滚动显示大量内容,而且可以进行内容缩放
- 也就是说,要完成缩放功能的话,只需要将需要缩放的内容添加到UIScrollView中

#### 缩放实现的步骤
- 设置UIScrollView的代理对象
- 设置minimumZoomScale:缩小的最小比例
- 设置maximumZoomScale:放大的最大比例
- 让代理实现下面的方法,返回需要缩放的控件
```objcetivec
 -(UIView *)viewForZoomingInScrollView:(UIScrollView *)scrollView;
```
- 将要缩放调用的代理方法
```objcetivec
 -(void)scrollViewWillBeginZooming:(UIScrollView:)scrollView withView:(UIView *)view;
```
- 正在缩放的时候调用的方法
```objcetivec
 -(void)scrolViewDidZoom:(UIScrollView *)scrollView;
```

### 分页
- 只要设置UIScrollView的pageEnable=YES,UIScrollView会被分割成多个独立的页,里面的内容就能分页展示
- 一般会配合UIPageControl增强分页效果
- UIPageControl的常见属性
```objcetivec
@property(nonatomic)NSInteger numberOfPages;// 一共有多少页
@property(nonatomic)NSInteger currentPage;//当前页码
@property(nonatomic)BOOL hidsForSinglePage;//只有一页时,是否隐藏页码指示器
@property(nonatomic,retain)UIColor *pageIndicatorTintColor;
@property(nonatomic,retain)UIColor *currentPageIndicatorTintColor;
```
#### NSTimer
- 定时器,作用有:在指定的时间/每隔一段时间执行指定的任务
- 调用下面的方法就会开启一个定时任务
```objcetivec
+(NSTimer *)scheduledTimerWithTimeInterval:(NSTimeInterval)ti
		target:(id)aTarget
    	selector:(SEL)selector
        userInfo:(id)userInfo
        repeats:(BOOL)yesOrNo;
```
- 通过invalidate方法可以停止定时器的工作,一旦被停止就不能再次执行任务了,只能再创建一个新的定时器 -(void)invalidate;
```objcetivec
NSTimer *timer = [NSTimer timerWithTimeInterval:2 target:self selector:@selector(self) userInfo:nil repeats:YES];
[[NSRunLoop mianRunLoop] addTimer:timer forMode:NSRunLoopCommonModes];
```




























### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate
### delegate

