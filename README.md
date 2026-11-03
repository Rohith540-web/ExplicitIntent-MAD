# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

1. Start the application.

2. Create the first Activity with an EditText to enter a number.

3. Create a Button to calculate the factorial.

4. Initialize the EditText and Button using findViewById().

5. Set an OnClickListener() for the Button.

6. Get the number entered by the user.

7. Create an Explicit Intent to navigate from MainActivity to SecondActivity.

8. Pass the entered number using putExtra().

9. Start the SecondActivity using startActivity().

10. Retrieve the number in SecondActivity using getIntent().getIntExtra().

11. Calculate the factorial of the given number.

12. Display the factorial result using TextView.

13. Stop


## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by:ROHITH V
Registeration Number :212224220083
*/
```
# MainActivity.java
```
package com.example.exp2_explicit;

import android.os.Bundle;
import android.content.Intent;
import android.widget.Button;
import android.widget.EditText;
import androidx.appcompat.app.AppCompatActivity;


public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        EditText editText = findViewById(R.id.editText);
        Button btn = findViewById(R.id.btn);

        btn.setOnClickListener(v -> {

            int n = Integer.parseInt(editText.getText().toString());

            Intent intent = new Intent(MainActivity.this, MainActivity2.class);

            intent.putExtra("number", n);

            startActivity(intent);
        });
    }
}
```
# MainActivity2.java
```
package com.example.exp2_explicit;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.widget.Button;
import android.widget.TextView;

public class MainActivity2 extends AppCompatActivity {
    TextView tvResult;
    Button btnBack;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        tvResult = findViewById(R.id.tvResult);
        btnBack = findViewById(R.id.btnBack);

        int n = getIntent().getIntExtra("number", 0);
        long fact = 1;
        for (int i = 1; i <= n; i++) {
            fact = fact * i;
        }
        tvResult.setText("Factorial of " + n + " = " + fact);
        btnBack.setOnClickListener(v -> {
            Intent intent = new Intent(
                    MainActivity2.this,
                    MainActivity.class
            );
            startActivity(intent);
            finish();
        });
    }
}
```
# activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/editText"
        android:layout_width="273dp"
        android:layout_height="72dp"
        android:layout_marginTop="268dp"
        android:hint="Enter a number"
        android:inputType="number"
        android:textSize="24sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/btn"
        android:layout_width="242dp"
        android:layout_height="55dp"
        android:text="Calculate Factorial"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editText"
        app:layout_constraintVertical_bias="0.276" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
# activity_main2.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="FACTORIAL RESULT"
        android:textColor="#263477"
        android:textSize="25sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/tvResult"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.56" />

    <TextView
        android:id="@+id/tvResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="308dp"
        android:text="Result"
        android:textColor="#16834A"
        android:textSize="23sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/btnBack"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

    <Button
        android:id="@+id/btnBack"
        android:layout_width="297dp"
        android:layout_height="50dp"
        android:layout_marginBottom="140dp"
        android:backgroundTint="#5146E5"
        android:text="Back to First Activity"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

## OUTPUT

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/43a3e6c5-e35a-46e0-ab65-01dca604c33b" />
<img width="1917" height="1198" alt="image" src="https://github.com/user-attachments/assets/f690a6a7-52de-49dd-b5bb-03f02fb0c4b3" />
<img width="445" height="925" alt="image" src="https://github.com/user-attachments/assets/1e422629-4eae-4070-a7d6-9776190b0562" /><img width="445" height="925" alt="image" src="https://github.com/user-attachments/assets/169e4b4a-69f5-4358-b052-e1e6a3717fe8" />




## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


