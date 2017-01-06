# InstagramLikeColorTransitionAndroid

##### 1. Create some gradient color drawables inside drawable Folder.
color1.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
<gradient
    android:startColor="#c44e4e"
    android:endColor="#dcb9b9"
    android:angle="0"/>
</shape>

```


color2.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <gradient
        android:startColor="#680b0b"
        android:endColor="#c6b147"
        android:angle="45"/>
</shape>
```
color3.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <gradient
        android:startColor="#57caa8"
        android:endColor="#44c74b"
        android:angle="90"/>
</shape>
````

color4.xml

````xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <gradient
        android:startColor="#7141e2"
        android:endColor="#d46cb3"
        android:angle="135"/>
</shape>
````
    
##### Create animation list using the above created gradient colors, animation_list.xml, inside drawable folder
    <?xml version="1.0" encoding="utf-8"?>
    <animation-list xmlns:android="http://schemas.android.com/apk/res/android">
        <item
            android:drawable="@drawable/color1"
            android:duration="10000" />
        <item
            android:drawable="@drawable/color2"
            android:duration="10000" />
        <item
            android:drawable="@drawable/color3"
            android:duration="10000" />
        <item
            android:drawable="@drawable/color4"
            android:duration="10000" />
    </animation-list>
    
3. Apply the animation_list created above as a background to the top view of your activity layout.
    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical"
        android:background="@drawable/animation_list"
        android:id="@+id/container">
        
        <!-- Child Views -->
        
    </LinearLayout>
    
4. Inside your activity use AnimationDrawable to apply the transition.
    LinearLayout container = (LinearLayout) findViewById(R.id.container);
    
    AnimationDrawable anim = (AnimationDrawable) container.getBackground();
    anim.setEnterFadeDuration(6000);
    anim.setExitFadeDuration(2000);
    
5. Starting animation:- start the animation on onResume.
    @Override
    protected void onResume() {
        super.onResume();
        if (anim != null && !anim.isRunning())
            anim.start();
    }
      
6. Stopping animation:- stop the animation on onPause.
    @Override
    protected void onPause() {
        super.onPause();
        if (anim != null && anim.isRunning())
            anim.stop();
    }