
# Ex.No:7 Design an application that draws basic graphical primitives on the screen.


## AIM:

To create and design an android application that draws basic graphical primitives on the screen using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “graphical″ and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Draw basic object details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to create and design an android application that draws basic graphical primitives on the screen.
Developed by: SWETHA A
Registeration Number : 212223220114
*/
```

Main_Acitivity.java

```
package com.example.graphicsdemo;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.FrameLayout;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        
        FrameLayout layout = new FrameLayout(this);
        
        ShapeView shapeView = new ShapeView(this);
        layout.addView(shapeView);

        
        setContentView(layout);
    }
}

```

Activity_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/rootLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg_gradient">

    
</FrameLayout>

```

ShapeView.java

```
package com.example.graphicsdemo;

import android.content.Context;
import android.graphics.*;
import android.view.View;
import java.util.Random;

public class ShapeView extends View {

    private Paint shapePaint;
    private Paint textPaint;
    private Random random;
    private int[] colors = {
            Color.parseColor("#FF6F61"),  
            Color.parseColor("#6B5B95"),  
            Color.parseColor("#88B04B"),  
            Color.parseColor("#F7CAC9"),  
            Color.parseColor("#92A8D1"),  
            Color.parseColor("#FFD700"),  
            Color.parseColor("#40E0D0")   
    };

    public ShapeView(Context context) {
        super(context);
        shapePaint = new Paint();
        shapePaint.setAntiAlias(true);

        textPaint = new Paint();
        textPaint.setAntiAlias(true);
        textPaint.setTypeface(Typeface.create(Typeface.SANS_SERIF, Typeface.BOLD));
        textPaint.setTextSize(40);
        textPaint.setTextAlign(Paint.Align.CENTER);

        random = new Random();
    }

    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);

        
        Paint bgPaint = new Paint();
        LinearGradient gradient = new LinearGradient(0, 0, getWidth(), getHeight(),
                Color.parseColor("#FFDEE9"), Color.parseColor("#B5FFFC"),
                Shader.TileMode.MIRROR);
        bgPaint.setShader(gradient);
        canvas.drawRect(0, 0, getWidth(), getHeight(), bgPaint);

        int width = getWidth();
        int height = getHeight();

        
        for (int i = 0; i < 6; i++) {
            int color = colors[random.nextInt(colors.length)];
            shapePaint.setColor(color);
            shapePaint.setStyle(Paint.Style.FILL);

            int x = random.nextInt(width - 300) + 150;
            int y = random.nextInt(height - 400) + 200;
            int size = 150 + random.nextInt(100);
            String shapeName = "";

            
            textPaint.setColor(getContrastColor(color));

            switch (random.nextInt(4)) {
                case 0: 
                    canvas.drawCircle(x, y, size / 2, shapePaint);
                    shapeName = "Circle";
                    canvas.drawText(shapeName, x, y + 10, textPaint);
                    break;

                case 1: 
                    canvas.drawRect(x, y, x + size, y + size, shapePaint);
                    shapeName = "Rectangle";
                    canvas.drawText(shapeName, x + size / 2f, y + size / 2f + 15, textPaint);
                    break;

                case 2: 
                    shapePaint.setStrokeWidth(15);
                    canvas.drawLine(x, y, x + size, y + size, shapePaint);
                    shapeName = "Line";
                    canvas.drawText(shapeName, x + size / 2f, y + size / 2f - 10, textPaint);
                    break;

                case 3: 
                    Path path = new Path();
                    path.moveTo(x, y);
                    path.lineTo(x + size, y);
                    path.lineTo(x + size / 2f, y - size);
                    path.close();
                    canvas.drawPath(path, shapePaint);
                    shapeName = "Triangle";
                    canvas.drawText(shapeName, x + size / 2f, y - size / 3f, textPaint);
                    break;
            }
        }
        
        postInvalidateDelayed(1000);
    }

    
    private int getContrastColor(int color) {
        double y = (299 * Color.red(color) + 587 * Color.green(color) + 114 * Color.blue(color)) / 1000.0;
        return y >= 128 ? Color.BLACK : Color.WHITE;
    }
}

```

bg_gradient.xml

```
<?xml version="1.0" encoding="utf-8"?>
<gradient xmlns:android="http://schemas.android.com/apk/res/android"
    android:startColor="#FFDEE9"
    android:endColor="#B5FFFC"
    android:angle="45"
    android:type="linear" />

```

### OUTPUT

<img width="1919" height="1079" alt="Screenshot 2025-10-30 101109" src="https://github.com/user-attachments/assets/720b97ac-6e26-4457-ad2d-928b0ba88e87" />


### Execution:


https://github.com/user-attachments/assets/37ef7345-6588-4d7b-91c4-c1a5d53b152c



## RESULT
Thus a Simple Android Application to create and design an android application that draws basic graphical primitives on the screen using Android Studio is developed and executed successfully.
