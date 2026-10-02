# Meals App Flutter

A multi-screen mobile application built with Flutter and Dart for exploring recipes, categories, cooking steps, and managing dietary preferences and favorite meals. The application demonstrates multi-screen navigation, category-based browsing, tab bar controllers, side drawers, dynamic state filtering, and custom page transitions.

Targeted and optimized strictly for **Android** and **iOS**.

---

## Features

- **Category Browsing**: Visual grid of food categories with custom colors, gradients, and touch animations.
- **Meals Exploration**: Filtered list of recipes belonging to selected categories with prep time, complexity, and affordability indicators.
- **Detailed Recipe Screen**: Complete meal instructions, ingredient checklists, and step-by-step preparation guidelines.
- **Favorite Meals Management**: Add and remove meals from a personal Favorites list with immediate UI synchronization.
- **Dietary Filters & Preferences**: Filter recipes dynamically based on dietary restrictions:
  - Gluten-Free
  - Lactose-Free
  - Vegetarian
  - Vegan
- **Multi-Screen Navigation**:
  - **Tabs Bar Navigation**: Bottom navigation bar to toggle smoothly between Categories and Favorites.
  - **Side Drawer**: Slide-out navigation drawer for switching between Meals and Filter settings.
- **Interactive Feedback**: Snackbars, hero animations, and smooth transitions between screens.
- **Theming & Typography**: Cohesive Material Design system with custom color schemes and typography from Google Fonts.

---

## Key Learnings & Flutter Concepts Mastered

Throughout this project, several critical Flutter and Dart concepts are studied, practiced, and integrated into production-ready code:

### 1. Multi-Screen Navigation & Routing
- **`Navigator.push` & `Navigator.pop`**:
  - Managing the navigation stack for pushing recipe lists, meal details, and returning results.
  - Using `MaterialPageRoute` for platform-authentic slide and fade transitions.
- **Passing Data Between Screens**:
  - Passing models and identifiers via widget constructors.
  - Returning data back to previous screens using `Navigator.of(context).pop(data)`.

### 2. Tab Bar & Drawer Navigation Architectures
- **`DefaultTabController` & Bottom Navigation Bar**:
  - Setting up persistent tab navigation for high-level screen switching.
  - Managing active screen index and dynamic `AppBar` titles based on the active tab.
- **Side Drawer Navigation (`Drawer`)**:
  - Implementing accessible side drawers with custom headers and `ListTile` options.
  - Replacing or pushing routes efficiently without bloating the navigation history stack.

### 3. State Management & Filtering
- **Lifting State Up & Callbacks**:
  - Managing global favorites and filter toggles at the root level and passing callbacks down the widget tree.
- **Dynamic List Filtering**:
  - Applying functional list filters (`where` and predicate functions) to filter meals based on user toggles.
- **State Preservation**:
  - Preserving user filter choices across screen transitions and navigation drawer switches.

### 4. Interactive UI & Custom Layouts
- **`GridView` & Sliver Protocols**:
  - Building responsive grids using `SliverGridDelegateWithFixedCrossAxisCount` with aspect ratios and spacing.
- **`InkWell` vs `GestureDetector`**:
  - Providing Material ripple splash feedback on touch interactions using `InkWell`.
- **Card-Based Media Representations**:
  - Layering meal thumbnail images, gradient overlays, and meta labels using `Stack` and `Positioned`.

---

## Technical Architecture & Design Decisions

### 1. Navigation Architecture
- **Hierarchical Stack**: Root `TabsScreen` holds persistent bottom navigation, while nested details screens are pushed onto the stack for clean back-button history.
- **Modal Drawer Actions**: The drawer triggers navigation replacements (`Navigator.of(context).pushReplacement`) to prevent infinite navigation loops between settings and main screens.

### 2. State & Data Flow
- **Immutable Data Models**: Models (`Meal`, `Category`) defined with immutable fields and `enum` types for complexity, affordability, and dietary flags.
- **Single Source of Truth**: Active filters and favorite meals list are centralized to guarantee consistent updates across all screens.

### 3. Theming & Design Language
- **Color Palettes**: Harmonious dark/light scheme generated via `ColorScheme.fromSeed` with deep contrast for media and card readability.
- **Google Fonts**: Custom typography integration for clean editorial presentation of recipe instructions and headers.

---

## Project Structure

```text
lib/
|-- main.dart                           # Entry point & theme configuration
|-- data/
|   `-- dummy_data.dart                 # Category & meal dummy data sets
|-- models/
|   |-- category.dart                   # Category data model
|   `-- meal.dart                       # Meal model with enums (Complexity, Affordability)
|-- screens/
|   |-- categories.dart                 # Categories grid screen
|   |-- filters.dart                    # Dietary preferences filter screen
|   |-- meal_details.dart               # Detailed ingredients & recipe steps
|   |-- meals.dart                      # Filtered meals list screen
|   `-- tabs.dart                       # Main navigation scaffold (Bottom tabs & Drawer)
`-- widgets/
    |-- category_grid_item.dart         # Gradient card for category items
    |-- main_drawer.dart                # Slide-out drawer menu
    |-- meal_item.dart                  # Meal card item with image & metadata
    `-- meal_item_trait.dart            # Icon + label metadata badge
```

---

## Getting Started

### Prerequisites
- Flutter SDK (v3.16.0 or higher recommended)
- Android Studio / Xcode for emulators or physical device deployment

### Dependencies
Defined in `pubspec.yaml`:
- `google_fonts`: Dynamic typography
- `transparent_image`: Smooth image fade-in placeholders

### Running the App
1. Clone the repository:
   ```bash
   git clone https://github.com/AdeelSaifee/meals_flutter_app.git
   cd meals_flutter_app
   ```

2. Fetch dependencies:
   ```bash
   flutter pub get
   ```

3. Run static code analysis:
   ```bash
   flutter analyze
   ```

4. Launch the application:
   ```bash
   flutter run
   ```
