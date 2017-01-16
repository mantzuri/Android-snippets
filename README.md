# Android-snippets
A small for favorite android snippets

## Create GIF like animation
* Copy images to drawable
* Create .xml file in drewable folder. For example: `anim.xml`
```java
<?xml version="1.0" encoding="utf-8"?>
<animation-list xmlns:android="http://schemas.android.com/apk/res/android"
    android:oneshot="false">

    <item android:drawable="@drawable/img3" android:duration="1000" />
    <item android:drawable="@drawable/img2" android:duration="1000" />
    <item android:drawable="@drawable/img1" android:duration="1000" />

</animation-list>
```
* Import the needed libraries
```java
   import android.widget.ImageView;
   import android.graphics.drawable.AnimationDrawable;
```

* In `On Create` add the following code: 

```java
        final ImageView animImageView = (ImageView) findViewById(R.id.iv_animation);
        animImageView.setBackgroundResource(R.drawable.anim);
        animImageView.post(new Runnable() {
            @Override
            public void run() {
                AnimationDrawable frameAnimation =
                        (AnimationDrawable) animImageView.getBackground();
                frameAnimation.start();
            }
        });
```
* Add the image to the XML file
```java
   <ImageView
     android:id="@+id/iv_animation"
     style="@style/ThemeOverlay.FirebaseIcon"
     android:layout_width="wrap_content"
     android:layout_height="wrap_content"
     android:contentDescription="Animation" />
     ```
