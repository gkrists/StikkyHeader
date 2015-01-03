StikkyHeader
============

This is a very simple library for Android that allows you to stick an header to a ListView and easly apply animation to it

## Code Example

To use the StikkyHeader library, you just need 3 lines:

```java
  StikkyHeaderBuilder.stickTo(mListView)
    .setHeader(R.id.header, containerLayout)
    .minHeightHeaderPixel(250)
    .build();
```
that's all. 

## Header Animator

Using the StikkyHeader you can create easly some nice animations extending the ``HeaderStikkyAnimator`` and using the utility ``AnimatorBuilder`` :

```java
public class IconAnimator extends HeaderStikkyAnimator {

    @Override
    public AnimatorBuilder getAnimatorBuilder() {

        View viewToAnimate = getHeader().findViewById(R.id.icon);
        Point point = new Point(50,100) // translate to the point with coordinate (50,100);
        float scaleX = 0.5f //scale to the 50%
        float scaleY = 0.5f //scale to the 50%
        float fade = 0.2f // 20% fade

        AnimatorBuilder animatorBuilder = AnimatorBuilder.create()
            .applyScale(viewToAnimate, scaleX, scaleY)
            .applyTranslation(viewToAnimate, point)
            .applyFade(viewToAnimate, fade);

        return animatorBuilder;
    }
}
```

and then set the animator to the StikkyHeader:

```java
  StikkyHeaderBuilder.stickTo(mListView)
    .setHeader(R.id.header, containerLayout)
    .minHeightHeaderPixel(250)
    .animator(new IconAnimator())
    .build();
```

## ViewGroup supported

The StikkyHeader supports:
- ListView
- RecyclerView
- ScrollView

