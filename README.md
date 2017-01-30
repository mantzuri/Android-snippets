# Android-snippets
A list of android snippets

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

##Open URL
```java
String url = "http://www.stackoverflow.com";
Intent i = new Intent(Intent.ACTION_VIEW);
i.setData(Uri.parse(url)); 
startActivity(i); 
```

or in short:
```java
startActivity(new Intent(Intent.ACTION_VIEW, Uri.parse("http://www.stackoverflow.com")));
```

##Add menu button
```java
 @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        MenuInflater inflater = getMenuInflater();
        inflater.inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {

        int id = item.getItemId();

        if (id == R.id.action_settings) {
            Intent intent_in = new Intent(this, SettingsActivity.class);
                startActivity(intent_in);
                //overridePendingTransition(0, 0);
        }

        return super.onOptionsItemSelected(item);
    }
```
and add the up button 

```java
 @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        android.support.v7.app.ActionBar actionBar = getSupportActionBar();
        assert actionBar != null;
        actionBar.setDisplayHomeAsUpEnabled(false);
        ...
        ```
