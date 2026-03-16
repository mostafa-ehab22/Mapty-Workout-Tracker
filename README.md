<h1 align=center>🗺️ Mapty Workout Tracker</h1>
<br>

<div align=center>
    <span>🎯</span>
<a href="https://mostafa-ehab22.github.io/Mapty-Workout-Tracker/" alt="Live Demo">Live Demo</a>
    <span>🎯</span>
</div>

## 🎯 Project Overview
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E.svg?logo=javascript&logoColor=black)
![Leaflet](https://img.shields.io/badge/Leaflet-199900.svg?logo=leaflet&logoColor=white) <br>

Interactive **fitness tracking application** with **geolocation integration** and **interactive mapping**. Features **real-time workout logging**, **persistent data storage**, and **dynamic map visualization** for comprehensive workout management and location-based fitness tracking.

## 🏗️ Architecture & Design

### Core Components

- **🏃‍♂️ Workout Classes `(Running/Cycling)`:**<br>
Object-oriented data models with inheritance for workout-specific calculations.<br>
Handles pace calculation for running and speed calculation for cycling.

- **🗺️ Map Integration `(_loadMap/_renderWorkoutMarker)`:**<br>
Leaflet-powered interactive maps with custom markers and popups.<br>
Dynamic map centering and zoom control with smooth animations.

- **💾 Data Persistence `(_setLocalStorage/_getLocalStorage)`:**<br>
Automatic JSON serialization with localStorage API integration.<br>
Seamless data recovery across browser sessions and page reloads.

- **📍 Geolocation Services `(_getPosition)`:**<br>
Browser-native location detection with error handling and fallbacks.<br>
Automatic map centering on user's current geographical position.

### Tech Stack
- **HTML5** → Semantic markup with modern web standards and accessibility
- **CSS3** → Advanced styling with flexbox, grid, and responsive design
- **JavaScript ES6+** → Object-oriented programming with classes and modern features
- **Leaflet.js** → Interactive map rendering and marker management
- **Geolocation API** → Real-time user positioning and location services
- **Local Storage API** → Client-side data persistence and session management

### Application Architecture Flow
```
Page Load → Geolocation → Map Rendering → Event Binding → User Interaction
├── 📍 Get Position → Navigator.geolocation API
├── 🗺️ Load Map → Leaflet initialization with tile layers
├── 🎯 Bind Events → Form submission and map click handlers
├── 🏃‍♂️ Create Workout → Running/Cycling class instantiation
├── 📊 Calculate Metrics → Pace/speed computation and validation
└── 💾 Store Data → localStorage with JSON serialization
```

### Data Processing Pipeline
```
User Input → Form Validation → Workout Creation → Map Rendering → Data Storage
├── 📝 Form Data → Distance, duration, cadence/elevation collection
├── ✅ Validation → Positive number verification and type checking
├── 🏗️ Object Creation → Running/Cycling class with calculated properties
├── 📍 Map Marker → Leaflet marker with custom popup and styling
└── 💾 Persistence → localStorage update with workout array
```

### Benefits:

- ✅ **Real-time Tracking** - Instant workout logging with geographical context
- ✅ **Persistent Storage** - Data survives browser sessions and page refreshes
- ✅ **Interactive Maps** - Click-to-navigate and visual workout representation
- ✅ **Responsive Design** - Optimized for desktop and mobile experiences

## ⚙️ Features

1. 🗺️ **Interactive Leaflet Maps**  
   High-resolution OpenStreetMap integration with custom styling and zoom controls.

2. 📍 **Automatic Geolocation**  
   Browser-native location detection with graceful error handling and user consent.

3. 🏃‍♂️ **Dual Workout Types**  
   Specialized forms for running (pace, cadence) and cycling (speed, elevation gain).

4. 💾 **Persistent Data Storage**  
   Automatic localStorage integration with JSON serialization for cross-session data.

5. 🎯 **Click-to-Log Interface**  
   Intuitive map-click workflow for instant workout location marking.

6. 📊 **Automatic Calculations**  
   Real-time pace (min/km) for running and speed (km/h) for cycling computations.

7. 📍 **Marker Navigation**  
   Click workout entries to smoothly navigate map to corresponding locations.

8. 🔄 **Session Recovery**  
   Automatic workout restoration on application reload with full functionality.

## 📂 Project Structure
```
Mapty-Workout-Tracker/
│
├── 📄 index.html                         ⬅️ Main application structure
├── 🎨 style.css                          ⬅️ Responsive styling and animations
├── 📜 script.js                          ⬅️ Core application logic and classes
├── 📋 README.md                          ⬅️ Project documentation
├── 🖼️ icon.png                           ⬅️ Application favicon and branding
├── 📊 Mapty-architecture-final.png       ⬅️ System architecture diagram
├── 📈 Mapty-flowchart.png                ⬅️ Application flow visualization
└── 🏗️ Mapty-architecture-part-1.png      ⬅️ Class structure overview
```

## 🔧 Installation & Setup

### Prerequisites
```bash
Modern web browser with ES6+ support
Geolocation API permission
Stable internet connection for map tiles
```

### Installation Steps

```bash
# Clone the repository
git clone https://github.com/mostafa-ehab22/Mapty-Workout-Tracker.git
cd Mapty-Workout-Tracker

# Start local development server (optional)
npx live-server
# OR simply open index.html in your browser
```

### Running the Application
```bash
# Direct browser access
open index.html

# Or with live server for development
live-server --port=8080
```

## 💻 Usage Examples

### Basic Workout Creation Flow
```bash
1. 📍 Allow location access when prompted
2. 🗺️ Map centers on your current position
3. 🎯 Click anywhere on the map to open workout form
4. 📝 Select workout type (Running/Cycling)
5. ✏️ Fill in distance, duration, and specific metrics
6. ✅ Submit form to create workout marker
7. 📊 View calculated pace/speed in workout list
```

### Advanced Usage Scenarios
```bash
# Multiple workout session
- Create running workout: 5km in 25min → Pace: 5.0 min/km
- Create cycling workout: 20km in 45min → Speed: 26.7 km/h
- Click workout entries to navigate map to locations

# Data persistence testing  
- Add several workouts with different types
- Refresh browser → All workouts restored
- Navigate between markers → Smooth map animations
```

## 💻 Code Highlights

### Object-Oriented Workout System
```javascript
class Running extends Workout {
  type = 'running';

  constructor(coords, distance, duration, cadence) {
    super(coords, distance, duration);
    this.cadence = cadence;
    this.calcPace();
    this._setDescription();
  }

  calcPace() {
    // min/km calculation
    this.pace = this.duration / this.distance;
    return this.pace;
  }
}
```

### Advanced Geolocation Integration
```javascript
_getPosition() {
  if (navigator.geolocation)
    navigator.geolocation.getCurrentPosition(
      this._loadMap.bind(this),
      function () {
        alert('Could not get your position');
      }
    );
}
```

### Sophisticated Data Persistence
```javascript
_setLocalStorage() {
  localStorage.setItem('workouts', JSON.stringify(this.#workouts));
}

_getLocalStorage() {
  const data = JSON.parse(localStorage.getItem('workouts'));
  if (!data) return;
  
  this.#workouts = data;
  this.#workouts.forEach(work => {
    this._renderWorkout(work);
  });
}
```

### Interactive Map Navigation
```javascript
_moveToPopup(e) {
  const workoutEl = e.target.closest('.workout');
  if (!workoutEl) return;

  const workout = this.#workouts.find(
    work => work.id === workoutEl.dataset.id
  );

  this.#map.setView(workout.coords, this.#mapZoomLevel, {
    animate: true,
    pan: { duration: 1 }
  });
}
```

## 🎛️ Configuration

### Map Customization Options
```javascript
// Default map settings
#mapZoomLevel = 15;

// Tile layer configuration
L.tileLayer('https://{s}.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png', {
  attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
}).addTo(this.#map);
```

### Workout Form Validation
```javascript
const validInputs = (...inputs) =>
  inputs.every(inp => Number.isFinite(inp));
const allPositive = (...inputs) => 
  inputs.every(inp => inp > 0);
```

## 📱 Browser Compatibility

### Supported Browsers
- ✅ **Chrome 60+** - Full feature support with optimal performance
- ✅ **Firefox 55+** - Complete functionality with ES6+ features  
- ✅ **Safari 12+** - iOS and macOS compatibility with geolocation
- ✅ **Edge 79+** - Chromium-based versions with modern standards

### Required Browser Features
- **Geolocation API** - Essential for location detection
- **Local Storage** - Required for data persistence
- **ES6 Classes** - Core application architecture dependency
- **Fetch API** - Map tile loading and external resource access

## ⚠️ Limitations & Considerations

- **Location Permission**: Requires explicit user consent for geolocation access
- **Internet Dependency**: Map tiles require active internet connection
- **Storage Limits**: localStorage restricted to ~5-10MB per domain
- **Precision Accuracy**: GPS accuracy varies based on device and environment
- **Browser Storage**: Data lost when localStorage is manually cleared

## 🔮 Future Enhancements

### Planned Features
-  **Offline Map Support** - Service worker implementation for tile caching
-  **Advanced Analytics** - Weekly/monthly statistics and progress tracking
-  **Achievement System** - Goal setting and milestone recognition
-  **Data Export** - CSV/JSON export functionality for external analysis
-  **Theme Customization** - Dark mode and personalized color schemes

### Technical Improvements
-  **Testing Suite** - Unit tests with Jest for component validation
-  **PWA Features** - Service worker and manifest for app-like experience
-  **Data Sync** - Cloud storage integration for cross-device synchronization
-  **Route Planning** - Integration with routing APIs for workout paths

## 🤝 Contributing

### How to Contribute
1.  Fork the repository
2.  Create a feature branch (`git checkout -b feature/map-enhancements`)
3.  Commit your changes (`git commit -m 'Add route tracking feature'`)
4.  Push to the branch (`git push origin feature/map-enhancements`)
5.  Open a Pull Request

### Development Areas
-  Enhanced map features and custom tile layers
-  Advanced workout analytics and data visualization
-  Mobile app development with React Native
-  Real-time synchronization and cloud storage
-  Comprehensive testing and performance optimization

## ⚖️ Ethical Usage & Privacy

This application prioritizes **user privacy and data security**. All data remains local to your device:
- ✅ **No Server Communication** - All data stored locally in browser
- ✅ **Location Privacy** - Coordinates never transmitted or shared
- ✅ **User Control** - Complete data ownership with manual reset option
- ✅ **Transparent Processing** - Open source code available for audit

*Your workout data stays private and under your complete control.*

## 📜 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.
