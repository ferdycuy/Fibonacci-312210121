## Fibonacci
### Nama           : Ferdyana Eka Prasetya
### NIM            : 312210121
### Kelas          :TI.22.A1
### Dosen Pengampu : Donny Maulana S.Kom., M.M.S.I.

### Tugasnya buatlah Method Program java Toast Number, dengan menghasilkan Bilangan Fibonacci!

### - Masukkan Sourch code pada menu activity_fibonacci.xml berikut!
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/limitEditText"
        android:layout_width="160dp"
        android:layout_height="50dp"
        android:layout_marginStart="16dp"
        android:layout_marginTop="4dp"
        android:layout_marginEnd="16dp"
        android:hint="Masukkan batas limit"
        android:onClick="setLimit"
        android:inputType="number"
        android:textAlignment="center"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.895"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/button_toast"
        android:layout_width="160dp"
        android:layout_height="50dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="4dp"
        android:layout_marginEnd="8dp"
        android:background="@color/colorPrimary"
        android:onClick="showToast"
        android:text="@string/toast"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtomSize" />

    <Button
        android:id="@+id/button_count"
        android:layout_width="160dp"
        android:layout_height="50dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="@color/colorPrimary"
        android:onClick="countUp"
        android:text="count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtomSize" />

    <Button
        android:id="@+id/back"
        android:layout_width="160dp"
        android:layout_height="50dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="@color/colorPrimary"
        android:onClick="back1"
        android:text="back"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtomSize" />

    <TextView
        android:id="@+id/show_count"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="#FFFF00"
        android:gravity="center_vertical"
        android:text="@string/count_initial_value"
        android:textAlignment="center"
        android:textColor="@color/colorPrimary"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_toast" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
### - Masukkan Sourch code pada menu strings.xml berikut!
```
<resources>
    <string name="app_name">Tugasenam</string>
    <string name="button_labe_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">1</string>
    <string name="toast_message">Bilangan Fibonacci</string>
    <string name="toast">Toast</string>
    <string name="count">Count</string>
    <string name="_0">0</string>
</resources>
```
### - Masukkan sourch code pada menu colors.xml berikut!
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="color1">#FF0000</color>
    <color name="color2">#00FF00</color>
    <color name="color3">#0000FF</color>
</resources>
```
### - Masukkan sourch code pada menu MainActivity.Java berikut!
```
package com.example.tugasenam;

import android.os.Bundle;
import android.view.View;
import android.widget.TextView;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private TextView showCount;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 0;
    private long limit = 0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_fibonacci);

        showCount = findViewById(R.id.show_count);
    }

    public void showToast(View view) {
        Toast.makeText(this, "Bilangan Fibonacci", Toast.LENGTH_SHORT).show();
    }

    public void countUp(View view) {
        if (count == 0) {
            showCount.setText("0");
        } else if (count == 1) {
            showCount.setText("1");
        } else {
            long fibCurrent = fibNMinus1 + fibNMinus2;
            fibNMinus2 = fibNMinus1;
            fibNMinus1 = fibCurrent;
            // Mengatur warna teks berdasarkan angka Fibonacci
            int colorResId = R.color.color1; // Warna default
            switch (count % 3) {
                case 1:
                    colorResId = R.color.color1; // Warna merah
                    break;
                case 2:
                    colorResId = R.color.color2; // Warna hijau
                    break;
                case 0:
                    colorResId = R.color.color3; // Warna biru
                    break;
            }
            showCount.setTextColor(getResources().getColor(colorResId));
            if (fibCurrent <= limit) {
                showCount.setText(String.valueOf(fibCurrent));
            } else {
                Toast.makeText(this, "batas limit", Toast.LENGTH_SHORT).show();

            }

        }
        count++;
    }
    public void setLimit(View view) {
        TextView limitEditText = findViewById(R.id.limitEditText);
        try {
            limit = Long.parseLong(limitEditText.getText().toString());
            count = 1;
            fibNMinus1 = 1;
            fibNMinus2 = 0;
            showCount.setText(getString(R.string.count_initial_value));
        } catch (NumberFormatException e) {
            Toast.makeText(this, "", Toast.LENGTH_SHORT).show();
        }
    }
    public void back1(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        showCount.setText(getString(R.string.count_initial_value));
    }
}


```
## Berikut hasil run nya



https://github.com/ferdycuy/Fibonacci-312210121/assets/115714443/466598f7-bc14-422e-a1c8-a19e9f0d062f





