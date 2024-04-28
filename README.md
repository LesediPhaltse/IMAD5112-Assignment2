# IMAD5112-assignment-2

Explanation for each attachment

**MainActivity.kt**
This code snippet is for an Android application written in Kotlin. Here's a breakdown of what's happening:

**Package Declaration**:
   - The first line, `package com.example.assignment2`, indicates the package in which this code resides. This is a way to organize your classes in Android projects.

**Imports**:
   - The code imports necessary Android libraries like `android.annotation.SuppressLint`, `android.content.Intent`, `android.os.Bundle`, `android.widget.Button`, `androidx.activity.enableEdgeToEdge`, and `androidx.appcompat.app.AppCompatActivity`.

**Class Definition**:
   - The `MainActivity` class extends `AppCompatActivity`, indicating that it represents an Activity in Android, which is a component of the user interface.

**Override `onCreate` Method**:
   - The `onCreate` method is overridden to specify what should happen when the activity is created (which is when it is first launched).
   - The `@SuppressLint("MissingInflatedId")` annotation suppresses the lint warning about referencing a view before it's properly inflated.

**Enable Edge to Edge Display**:
   - The `enableEdgeToEdge()` method enables edge-to-edge content layout, allowing the content to use the entire screen, including the notches and status bars.

**Set Content View**:
   - The `setContentView(R.layout.activity_main)` sets the layout of this activity to the one defined in `activity_main.xml`.

**Button Interaction**:
   - The code finds a button view with ID `BtnGenerate` from the layout.
   - The `setOnClickListener` method is used to set up a click listener for this button. When the button is clicked, it creates an `Intent` to launch another activity (`MainActivity2`), and then starts that activity with `startActivity(intent)`.

In summary, this code defines an Android activity with a button that, when clicked, launches another activity named `MainActivity2`. The code handles the UI setup and button click event to initiate the transition between activities.

**MainActivity2.kt**

This code snippet represents an Android activity class called `MainActivity2` in Kotlin, which is part of an Android application. Let's break down what happens in this class:

### Class Definition and Properties
- **Class Definition**: `MainActivity2` extends `AppCompatActivity`, meaning it's an Android activity class.
- **Instance Variables**: Three integer variables are declared to represent a pet's health, hunger, and cleanliness, with initial values of `100`, `50`, and `50` respectively.

### onCreate Method
- **Purpose**: This method is executed when the activity is created.
- **Set Content View**: `setContentView(R.layout.activity_main2)` specifies that the layout for this activity is `activity_main2.xml`.
- **UI Components**: The following UI components are referenced from the layout:
  - Buttons (`btnFeed`, `btnClean`, `btnHappy`) for user interactions.
  - EditTexts (`txt_hunger_value`, `txt_clean_value`, `txt_happy`) to display text information about the pet's hunger, cleanliness, and health.
  - An `ImageView` (`pet_image`) to display an image.

### Initial Text Values
- The initial text values for hunger, cleanliness, and health are set using the `setText` method, displaying the values of the corresponding instance variables.

### Button Click Listeners
- **Button Functionality**: 
  - The code assigns `OnClickListener` instances to handle clicks on each button.
  - For each button click, the corresponding values of hunger, cleanliness, and health are updated, and the respective text fields are updated accordingly.
  - Additionally, the `animateImageChange` method is called to animate the `ImageView` and change its image resource.
- **Button Logic**:
  - `btnFeed`: When clicked, decreases hunger by 10, increases health by 10, and then increases hunger by 5 (net change of -5). The displayed hunger and health are updated accordingly. An animation is applied, changing the image to `R.drawable.eat_eating_icon`.
  - `btnClean`: Increases cleanliness by 10 and health by 10, updating the text and animating the image to `R.drawable.dog_cleaning_icon`.
  - `btnHappy`: Increases health by 10, increases hunger by 5, and decreases cleanliness by 5. The corresponding text is updated, and the image changes to `R.drawable.dog_playing_icon`.

### Animation Method
- The `animateImageChange` method creates a fade-in animation using `AlphaAnimation`, with a duration of 500 milliseconds and `fillAfter` set to `true` to maintain the final state of the animation.
- The image resource is changed to `newImageResource`, and the animation is started on `imageView`.

Overall, this code snippet creates an Android activity where users can interact with a virtual pet by feeding, cleaning, or playing with it. Each action updates the pet's status and animates the corresponding image to reflect the change.

**activity_main.xml**

This XML file defines a layout for an Android activity, using a `ConstraintLayout` as the parent view group. Here's a breakdown of the layout and its components:

### ConstraintLayout
- The `ConstraintLayout` is a flexible and powerful layout for positioning and sizing child views in Android. It allows complex layouts to be defined without nesting multiple view groups.
- The root element has:
  - `layout_width` and `layout_height` set to `match_parent`, making it take up the entire screen.
  - A background color of `#E86E80` (a shade of pink/red).
  - `tools:context` set to `.MainActivity`, indicating that this layout is likely for the `MainActivity` class.

### TextView
- **Purpose**: Displays a welcome message to the user.
- **Attributes**:
  - `android:layout_width` and `android:layout_height` set to `246dp` and `81dp`, respectively.
  - `android:layout_marginStart` and `android:layout_marginTop` set for positioning.
  - `android:fontFamily` set to `cursive`.
  - `android:text` is set to a string resource `@string/welcom_to_jack_your_tamagotchi_app`.
  - `android:textAlignment` is `center`.
  - `android:textColor` set to `@color/white`.
  - `android:textSize` is `30sp`.
  - Constraint attributes: `app:layout_constraintStart_toStartOf="parent"` and `app:layout_constraintTop_toTopOf="parent"` to align it to the top-left corner of the parent view with specified margins.
  - `tools:ignore` attributes are used to suppress specific lint warnings like overlapping text and text size checks.

### Button
- **Purpose**: A button that initiates an action, labeled "Get started".
- **Attributes**:
  - `android:layout_width` and `android:layout_height` are `wrap_content`.
  - `android:layout_marginStart` and `android:layout_marginTop` to position it relative to other views.
  - `android:text` is set to a string resource `@string/Get_started`.
  - `android:textSize` is `15sp`.
  - Constraint attributes: `app:layout_constraintStart_toStartOf="parent"` and `app:layout_constraintTop_toBottomOf="@+id/imageView2"`, placing it below `imageView2`.
  - The `tools:ignore="MissingConstraints"` indicates ignoring lint warnings about missing constraints.

### ImageView
- **Purpose**: Displays an image in the layout.
- **Attributes**:
  - `android:layout_width` and `android:layout_height` set to `346dp` and `367dp`, respectively.
  - `android:layout_marginStart` and `android:layout_marginTop` to position it.
  - `app:srcCompat="@drawable/picture"` sets the image resource.
  - Constraint attributes: `app:layout_constraintStart_toStartOf="parent"` and `app:layout_constraintTop_toTopOf="parent"`.
  - `tools:ignore="ContentDescription"` suppresses warnings about missing content descriptions (for accessibility).

### Layout Overview
- The `ConstraintLayout` contains three elements:
  1. **TextView**: Positioned at the top, centered horizontally with margins.
  2. **Button**: Positioned below `imageView2`.
  3. **ImageView**: Positioned near the top-left corner with specific margins.

These components create a simple UI where there's a welcome message at the top, an image below it, and a button that starts an action, probably related to the "Get started" functionality.

**activity_main2xml**

This XML file represents a layout for an Android activity using `ConstraintLayout` as the root view group. It defines various UI elements like `ImageView`, `Button`, `TextView`, and `EditText`, with constraints for their positioning and behavior.

### ConstraintLayout
- The `ConstraintLayout` provides a flexible layout structure for arranging UI components. It allows complex positioning and alignment without deep nesting.

### ImageView
- **Purpose**: Displays an image representing a pet.
- **Attributes**:
  - `android:layout_width` and `android:layout_height` set to `358dp` and `335dp`, indicating a relatively large image.
  - Positioned at the top-left corner, using `layout_marginStart` and `layout_marginTop`.
  - `app:srcCompat` set to `@drawable/icon` to display the desired image.
  - `android:contentDescription` provides a description for accessibility, here referring to a `@string/todo` resource.
  - Constraint attributes: `app:layout_constraintStart_toStartOf="parent"` and `app:layout_constraintTop_toTopOf="parent"` ensure the image stays at the top-left.

### Buttons
- There are three buttons, each positioned below the `ImageView` and aligned horizontally.
  1. **Button for Feeding**:
     - `android:text` set to `@string/feed` (likely "Feed").
     - Positioned below the `ImageView`, with a margin for proper spacing.
     - Constraint: `app:layout_constraintStart_toStartOf="parent"` and `app:layout_constraintTop_toBottomOf="@+id/pet_image"`.
  2. **Button for Cleaning**:
     - `android:text` set to `@string/clean`.
     - Positioned to the right of the first button.
     - Constraints: `app:layout_constraintStart_toEndOf="@+id/btnFeed"` and `app:layout_constraintTop_toBottomOf="@+id/pet_image"`.
  3. **Button for Happiness**:
     - `android:text` set to `@string/happy`.
     - Positioned to the right of the second button.
     - Constraints: `app:layout_constraintStart_toEndOf="@+id/btnClean"` and `app:layout_constraintTop_toBottomOf="@+id/pet_image"`.

### TextViews
- There are three `TextView` elements, each representing a specific attribute of the pet (hunger, cleanliness, and happiness).
  - Positioned below the buttons, with specified margins for spacing.
  - Each text view has a `monospace` font and a text size of `19sp`.
  - Constraint: Positioned relative to each other and to the buttons.
  - The text reflects the intended attribute, such as `@string/hungry`, `@string/Clean`, and `@string/Happy`.

### EditTexts
- There are three `EditText` elements, each positioned to the right of the respective `TextView`.
  - **Purpose**: Likely used to show or edit values for the pet's attributes (hunger, cleanliness, happiness).
  - Positioned with margins and constraints relative to `TextView` and the preceding `EditText`.
  - `android:inputType="text"` allows text input.
  - The `tools:ignore` attributes indicate ignoring specific warnings, like missing constraints or missing label associations.

### Summary
This layout sets up a simple interface for a pet-management application, with:
- A large `ImageView` representing the pet.
- Three buttons for user interactions (feeding, cleaning, and happiness).
- Three `TextView` elements indicating pet attributes.
- Three `EditText` elements for displaying or editing attribute values.
