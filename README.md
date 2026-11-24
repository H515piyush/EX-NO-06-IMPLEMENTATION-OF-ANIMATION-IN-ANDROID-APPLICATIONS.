# Ex.No: 6 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as calculator and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Design xml files for all operations such as blink, rotate, move, slide, zoom, fade.

Step 6: Display the button operations in MainActivity file.

Step 7: Save and run the application

## PROGRAM:

## Program to display animation operation”.
### Developed by: Piyush Kumar
### Registeration Number :212223220075

## ACTIVITY_MAIN.XML:

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:scaleType="fitCenter"
        app:srcCompat="@drawable/download" />

    <Button
        android:id="@+id/fade"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Fade Animation" />

    <Button
        android:id="@+id/zoom"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Zoom Animation"/>

    <Button
        android:id="@+id/rotate"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Rotate Animation"/>

    <Button
        android:id="@+id/slide"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Slide Animation"/>

    <Button
        android:id="@+id/blink"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Blink Animation"/>

    <Button
        android:id="@+id/move"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Move Animation"/>

</LinearLayout>

```
## MAIN_ACTIVITY.JAVA:

```
package com.example.implementationofanimation;

import android.os.Bundle;
import android.view.animation.Animation;
import android.view.animation.AlphaAnimation;
import android.view.animation.ScaleAnimation;
import android.view.animation.RotateAnimation;
import android.view.animation.TranslateAnimation;
import android.widget.Button;
import android.widget.ImageView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    ImageView imageView;
    Button fade, zoom, rotate, slide, blink, move;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = findViewById(R.id.imageView);
        blink = findViewById(R.id.blink);
        move = findViewById(R.id.move);

        fade = findViewById(R.id.fade);
        zoom = findViewById(R.id.zoom);
        rotate = findViewById(R.id.rotate);
        slide = findViewById(R.id.slide);

        fade.setOnClickListener(v -> {
            Animation anim = new AlphaAnimation(0, 1);
            anim.setDuration(1000);
            imageView.startAnimation(anim);
        });

        zoom.setOnClickListener(v -> {
            Animation anim = new ScaleAnimation(
                    0.5f, 1f, 0.5f, 1f,
                    Animation.RELATIVE_TO_SELF, 0.5f,
                    Animation.RELATIVE_TO_SELF, 0.5f
            );
            anim.setDuration(1000);
            imageView.startAnimation(anim);
        });

        rotate.setOnClickListener(v -> {
            Animation anim = new RotateAnimation(
                    0, 360,
                    Animation.RELATIVE_TO_SELF, 0.5f,
                    Animation.RELATIVE_TO_SELF, 0.5f
            );
            anim.setDuration(1000);
            imageView.startAnimation(anim);
        });

        slide.setOnClickListener(v -> {
            Animation anim = new TranslateAnimation(
                    -300, 0, 0, 0
            );
            anim.setDuration(1000);
            imageView.startAnimation(anim);
        });

        // Blink Animation
        blink.setOnClickListener(v -> {
            AlphaAnimation animation = new AlphaAnimation(1, 0);
            animation.setDuration(500);
            animation.setRepeatMode(Animation.REVERSE);
            animation.setRepeatCount(Animation.INFINITE);
            imageView.startAnimation(animation);
        });

        // Move Animation
        move.setOnClickListener(v -> {
            TranslateAnimation animation =
                    new TranslateAnimation(0, 200, 0, 0);
            animation.setDuration(1000);
            imageView.startAnimation(animation);
        });
    }
}
```
## MOVE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <translate
        android:fromXDelta="0%p"
        android:toXDelta="75%p"
        android:duration="700" />
</set>
```
## SLIDE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <scale android:duration="500"
        android:fromXScale="1.0" android:fromYScale="1.0"
        android:interpolator="@android:anim/linear_interpolator"
        android:toXScale="1.0"
        android:toYScale="0.0" />
</set>
```
## ROTATE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate
        android:duration="6000"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toDegrees="360" />
    <rotate
        android:duration="6000"
        android:fromDegrees="360"
        android:pivotX="50%"
        android:pivotY="50%"
        android:startOffset="5000"
        android:toDegrees="0" />
</set>
```
## FADE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <!-- duration is the time for which animation will work-->
    <alpha
        android:duration="1000"
        android:fromAlpha="0"
        android:toAlpha="1" />
    <alpha
        android:duration="1000"
        android:fromAlpha="1"
        android:startOffset="2000"
        android:toAlpha="0" />
</set>
```
## ZOOM.XML
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <scale xmlns:android="http://schemas.android.com/apk/res/android"
        android:fromXScale="0.5" android:toXScale="3.0"
        android:fromYScale="0.5" android:toYScale="3.0"
        android:duration="1000" android:pivotX="25%"
        android:pivotY="25%" >
    </scale>
    <scale xmlns:android="http://schemas.android.com/apk/res/android"
        android:startOffset="1000" android:fromXScale="3.0"
        android:toXScale="0.5" android:fromYScale="3.0"
        android:toYScale="0.5" android:duration="1000"
        android:pivotX="25%" android:pivotY="25%" >
    </scale>
</set>
```
## BLINK.XML
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <alpha android:fromAlpha="0.0" android:toAlpha="1.0"
        android:interpolator="@android:anim/accelerate_interpolator"
        android:duration="500" android:repeatMode="reverse"
        android:repeatCount="infinite"/>
</set>
```

## OUTPUT
<img width="1917" height="1023" alt="Screenshot 2026-11-24 090346" src="https://github.com/user-attachments/assets/1a6e2ab1-2b40-4032-8c65-1c6c5af89f3a" />


## ROTATE
<img width="1912" height="1023" alt="Screenshot 2026-11-24 090418" src="https://github.com/user-attachments/assets/e81a59fc-2fb5-443b-938b-7dd5ff64e9ee" />


## SLIDE

<img width="1917" height="1012" alt="Screenshot 2026-11-24 090430" src="https://github.com/user-attachments/assets/b269d205-0150-41e7-8593-cadaaade22a1" />



## FADE
<img width="1917" height="1011" alt="Screenshot 2026-11-24 090400" src="https://github.com/user-attachments/assets/36bc4faa-018f-4f1d-8c66-c1265095974a" />


## MOVE
<img width="1917" height="1010" alt="Screenshot 2026-11-24 090506" src="https://github.com/user-attachments/assets/e8e30ec5-8237-4cd5-b66d-88b290528ba6" />



## ZOOM

<img width="1910" height="1012" alt="image" src="https://github.com/user-attachments/assets/18d055a3-b613-44dd-b2e7-a9c7d39b027f" />


## BLINK

<img width="1917" height="950" alt="Screenshot 2026-11-24 090451" src="https://github.com/user-attachments/assets/1d3c7c05-07b0-46f8-b843-aef673925ef1" />

## RESULT
Thus a Simple Android Application to add animations: Move,blink,fade,clockwise,zoom,slide operations using Android Studio is developed and executed successfully.
