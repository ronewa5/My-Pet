# My-Pet
Assignment2
package com.example.assignment10462567

ActivityMain kt
import android.annotation.SuppressLint
import android.content.Intent
import android.os.Bundle
import android.widget.Button
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat

class MainActivity : AppCompatActivity() {
    @SuppressLint("MissingInflatedId")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
        // Declare the Views
        val next = findViewById<Button>(R.id.btnWoof)
        next.setOnClickListener {
            intent = Intent(this, MainActivity2::class.java  )
            startActivity(intent)
        }
    }
}


ActivityMain2 kt
package com.example.assignment10462567

import android.annotation.SuppressLint
import android.os.Bundle
import android.provider.MediaStore.Images
import android.view.animation.AlphaAnimation
import android.widget.Button
import android.widget.EditText
import android.widget.ImageView
import androidx.appcompat.app.ActionBar
import androidx.appcompat.app.AppCompatActivity

class MainActivity2 : AppCompatActivity() {

    private var petHealth = 100
    private var petHunger = 50
    private var petCleanliness = 50


        @SuppressLint("MissingInflatedId", "SuspiciousIndentation")
        override fun onCreate(savedInstanceState: Bundle?) {
            super.onCreate(savedInstanceState)
            setContentView(R.layout.activity_main2)

            // Get the button and text views
            val btnFeed =findViewById<Button>(R.id.btnFeed)
            val btnClean =findViewById<Button>(R.id.btnClean)
            val btnHappy =findViewById<Button>(R.id.btnHappy)
            val txtHunger =findViewById<EditText>(R.id.txtHunger_value)
            val txtHealth =findViewById<EditText>(R.id.txtHealth_value)
            val txtHappy =findViewById<EditText>(R.id.txtHappy)
            val petImage =findViewById<ImageView>(R.id.petImage)

            // Set the initial text values
            txtHunger.setText(petHunger.toString())
            txtHealth.setText(petHealth.toString())
            txtHappy.setText(petHealth.toString())

            //Handle button clicks
            btnFeed.setOnClickListener {
                petHunger -= 10
                petHealth += 10
                petHunger += 5
            txtHunger.setText(petHunger.toString())
                animateImageChange(petImage, R.drawable.dog_eating_icon)


            btnClean.setText(petCleanliness.toString())
            petCleanliness += 10
            petHealth += 10

                btnClean.setText(petCleanliness)
                animateImageChange(petImage, R.drawable.dog_clean_icon)

            }
            btnClean.setOnClickListener {
            petCleanliness += 10
            petHealth += 10

                txtHealth.setText(petCleanliness.toString())
                animateImageChange(petImage, R.drawable.god_bathing_icon)
            }
            btnHappy.setOnClickListener {
                petHealth += 10
                petHunger += 5
                petCleanliness -= 5
                txtHappy.setText(petHealth.toString())
                animateImageChange(petImage, R.drawable.dog_playing_icon)
            }

        }

        private fun animateImageChange(imageView: ImageView, newImageResource: Int) {
            val animate = AlphaAnimation(0.0f, 1.0f)
            animate.duration = 500
            animate.fillAfter = true
            imageView.startAnimation(animate)
            imageView.setImageResource(newImageResource)
            }

            }










