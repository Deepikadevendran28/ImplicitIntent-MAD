# Ex.No:3a Develop program to create a text field and a button “Navigate”. When you enter “www.gmail.com” and press navigate button it should open google page using Implicit Intents.


## AIM:

To create a navigate button using Implicit Intent to display the gmail page using Android Studio.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

1.Start onCreate() and load activity_main.xml using setContentView().
2.Find the EditText (id: editText) and Button (id: btn) using findViewById().
3.Attach an OnClickListener to the button.
4.On click, read the text using getText().toString().trim().
5.If the text is empty, show a Toast and stop.
6.If the URL does not start with http:// or https://, prepend https://.
7.Create an implicit intent: new Intent(Intent.ACTION_VIEW, Uri.parse(url)).
8.Call startActivity(intent), handling ActivityNotFoundException if no browser exists.
9.The browser opens and displays the requested page.

## PROGRAM:
```
/*
Program to print the text “Implicitintent”.
Developed by: Deepika D
Registeration Number :212225040059
*/



activity_main.xml


<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
 
    <EditText
        android:id="@+id/editText"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="24dp"
        android:layout_marginEnd="24dp"
        android:hint="@string/url_hint"
        android:inputType="textUri"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.4" />
 
    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="24dp"
        android:text="@string/navigate"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/editText" />
 
</androidx.constraintlayout.widget.ConstraintLayout>


res/values/strings.xml


<resources>
    <string name="app_name">ImplicitIntent</string>
    <string name="url_hint">Enter URL (e.g. www.gmail.com)</string>
    <string name="navigate">Navigate</string>
</resources>

MainActivity.java

package com.example.implicitintent;
 
import android.content.ActivityNotFoundException;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
 
import androidx.appcompat.app.AppCompatActivity;
 
public class MainActivity extends AppCompatActivity {
 
    EditText editText;
    Button btn;
 
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
 
        editText = findViewById(R.id.editText);
        btn = findViewById(R.id.btn);
 
        btn.setOnClickListener(view -> {
            String url = editText.getText().toString().trim();
 
            if (url.isEmpty()) {
                Toast.makeText(this, "Please enter a URL", Toast.LENGTH_SHORT).show();
                return;
            }
 
            if (!url.startsWith("http://") && !url.startsWith("https://")) {
                url = "https://" + url;
            }
 
            Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(url));
            try {
                startActivity(intent);
            } catch (ActivityNotFoundException e) {
                Toast.makeText(this, "No browser found", Toast.LENGTH_SHORT).show();
            }
        });
    }
}


AndroidManifest.xml (add inside <manifest>, outside <application>)


<queries>
    <intent>
        <action android:name="android.intent.action.VIEW" />
        <data android:scheme="https" />
    </intent>
</queries>


```

## OUTPUT

<img width="1535" height="862" alt="image" src="https://github.com/user-attachments/assets/0be87144-6518-4acd-87cb-86833461e446" />


Navigating to Gmail


<img width="1535" height="862" alt="image" src="https://github.com/user-attachments/assets/0e8d22de-8aba-4e2c-884f-bd92f5d753e3" />






## RESULT
Thus a Simple Android Application create a navigate button using Implicit Intent to display the gmail page using Android Studio is developed and executed successfully.


