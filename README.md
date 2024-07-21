# Calculator-App
A sophisticated Calculator application, meticulously crafted using Java and XML within the Android Studio framework during my tenure as an App Development Intern at KaiRiz Cyber Technologies, enabling comprehensive arithmetic computations through an intuitive user interface.

### Report on Calculator Application

#### Introduction
The Calculator application is a fundamental project aimed at introducing beginners to Android development and Java programming. This project demonstrates the creation of a basic calculator that allows users to perform arithmetic operations such as addition, subtraction, multiplication, and division. By undertaking this project, learners gain hands-on experience in user interface design, event handling, and basic logic implementation in Android.

#### Objective
The primary objectives of the Calculator application are:
1. To create an intuitive user interface for performing arithmetic operations.
2. To implement logic for handling user input and performing calculations.
3. To display calculation results in real-time.

#### Tools and Technologies
- **Android Studio**: Integrated Development Environment (IDE) for Android development.
- **Java**: Programming language used for implementing the application's logic.
- **XML**: Markup language used for designing the application's layout.

#### Application Layout (activity_main.xml)
The layout of the Calculator application is defined in the `activity_main.xml` file. It uses a `RelativeLayout` as the root element and includes nested `LinearLayout` elements for arranging buttons and display areas.

- **TextView for Result Display**: Displays the result of calculations.
- **LinearLayouts for Buttons**: Organizes buttons for digits (0-9), arithmetic operations (+, -, *, /), clear (C), all clear (AC), dot (.), and equals (=).

```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/result_tv"
        android:text="0"
        android:textSize="64dp"
        android:textAlignment="textEnd"
        android:textColor="@color/black"
        android:layout_margin="16dp" />

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:layout_alignParentBottom="true"
        android:background="#F1F1F1"
        android:paddingVertical="16dp"
        android:id="@+id/buttons_layout">
        <!-- Buttons are organized in multiple LinearLayouts for better alignment -->
    </LinearLayout>
</RelativeLayout>
```

#### Main Activity Logic (MainActivity.java)
The `MainActivity.java` file handles user input and performs calculations. Key components include:

1. **Initialization**: Initializes buttons and sets up click listeners.
2. **Calculation Logic**: Evaluates the input string to produce the result when the equals button is pressed.
3. **Error Handling**: Manages invalid inputs or operations.

```java
package com.example.calculator;

import android.os.Bundle;
import android.view.View;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
import com.google.android.material.button.MaterialButton;

public class MainActivity extends AppCompatActivity {
    private TextView resultTv, solutionTv;
    private String input = "", output;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        resultTv = findViewById(R.id.result_tv);
        solutionTv = findViewById(R.id.solution_tv);

        assignButtonListeners();
    }

    private void assignButtonListeners() {
        // Assign listeners to each button to handle user input
        MaterialButton buttonC = findViewById(R.id.button_c);
        buttonC.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                input = "";
                solutionTv.setText(input);
                resultTv.setText("0");
            }
        });

        // Similarly assign listeners to other buttons...
    }

    private void calculateResult() {
        // Simple evaluation logic to compute the result
        try {
            // Basic implementation of input evaluation (for illustration purposes)
            double result = new ExpressionBuilder(input).build().evaluate();
            output = String.valueOf(result);
            resultTv.setText(output);
        } catch (Exception e) {
            resultTv.setText("Error");
        }
    }
}
```

#### Features
- **User-Friendly Interface**: Provides a clean interface for performing calculations.
- **Basic Arithmetic Operations**: Supports addition, subtraction, multiplication, and division.
- **Clear and All Clear Functions**: Allows users to clear the current input or reset the entire calculation.
- **Real-Time Result Display**: Displays results as the user inputs values and operations.

#### Implementation Details

1. **User Input Handling**
   - Each button appends its corresponding value or operation to the input string.
   - Special buttons like clear (C) and all clear (AC) reset the input string.

2. **Evaluation Logic**
   - The input string is parsed and evaluated using a simple arithmetic parser (e.g., `ExpressionBuilder`).
   - Results are displayed in the result `TextView`.

3. **Error Handling**
   - Basic error handling is implemented to manage invalid inputs (e.g., division by zero).

#### Challenges and Solutions
- **Parsing Input**: Handling different arithmetic operations and ensuring correct precedence was challenging. This was managed by using a third-party library for parsing expressions.
- **User Interface Design**: Designing a responsive and intuitive interface required careful arrangement of buttons and text views.

#### Conclusion
The Calculator application is an excellent project for beginners in Android development and Java programming. It covers essential concepts such as UI design, event handling, and basic logic implementation. By completing this project, learners can build a solid foundation for more complex Android applications.

#### Future Enhancements
- **Scientific Functions**: Adding functions like sine, cosine, and logarithms.
- **Memory Functions**: Implementing memory storage and recall functionalities.
- **Advanced Error Handling**: Improving error handling for more complex scenarios.

This report provides a comprehensive overview of the Calculator application's structure, logic, and features, offering a detailed guide for understanding and building the project.
