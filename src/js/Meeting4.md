# JavaScript Fourth Lecture: APIs, Async Programming, and Modern Features

## What We'll Learn Today

- Working with APIs: Fetching data from the internet
- Asynchronous Programming: Promises and async/await
- Modern JavaScript: ES6+ features and best practices
- Error Handling: Managing errors gracefully
- Building a weather app with real API data

---

## Introduction to APIs

API (Application Programming Interface) allows different applications to communicate with each other. We'll learn how to fetch data from web APIs.

### What is an API?

```javascript
// API is like a waiter in a restaurant
// You (JavaScript) -> Waiter (API) -> Kitchen (Server) -> Data (Food)

// Example: Weather API
// Your app -> Weather API -> Weather Server -> Weather Data

// Common API examples:
// - Weather data (OpenWeatherMap)
// - User information (GitHub API)
// - Random jokes (JokesAPI)
// - Currency rates (ExchangeRate API)
// - Movie information (OMDB API)
```

### Understanding JSON

JSON (JavaScript Object Notation) is the standard format for API data:

```javascript
// JSON looks like JavaScript objects but everything is in strings
let jsonString = `{
    "name": "John Doe",
    "age": 30,
    "city": "New York",
    "hobbies": ["reading", "gaming", "coding"],
    "isStudent": false
}`;

// Converting JSON string to JavaScript object
let userData = JSON.parse(jsonString);
console.log("Name:", userData.name);
console.log("Hobbies:", userData.hobbies);

// Converting JavaScript object to JSON string
let person = {
    name: "Sarah",
    age: 25,
    profession: "Developer"
};

let jsonData = JSON.stringify(person);
console.log("JSON string:", jsonData);

// Real API response example
let weatherResponse = {
    "location": "Cairo",
    "temperature": 28,
    "description": "Sunny",
    "humidity": 65,
    "windSpeed": 12
};

console.log(`Weather in ${weatherResponse.location}:`);
console.log(`Temperature: ${weatherResponse.temperature}°C`);
console.log(`Conditions: ${weatherResponse.description}`);
```

---

## Asynchronous Programming

JavaScript can perform tasks without blocking the main thread. This is crucial for API calls and user experience.

### Understanding Synchronous vs Asynchronous

```javascript
// Synchronous code (blocking)
console.log("Start");
console.log("Middle");
console.log("End");

// Output: Start, Middle, End (in order)

// Asynchronous code (non-blocking)
console.log("Start");

setTimeout(function() {
    console.log("This runs after 2 seconds");
}, 2000);

console.log("End");

// Output: Start, End, "This runs after 2 seconds"
```

### Callbacks

The traditional way to handle asynchronous operations:

```javascript
// Callback example
function fetchUserData(userId, callback) {
    console.log("Fetching user data...");
    
    // Simulate API delay
    setTimeout(function() {
        let userData = {
            id: userId,
            name: "Alice Johnson",
            email: "alice@example.com"
        };
        
        callback(userData);
    }, 1000);
}

function displayUser(user) {
    console.log("User loaded:");
    console.log(`Name: ${user.name}`);
    console.log(`Email: ${user.email}`);
}

// Using the callback
fetchUserData(123, displayUser);

// Callback hell example (avoid this!)
function getUser(userId, callback) {
    setTimeout(() => {
        callback({ id: userId, name: "John" });
    }, 1000);
}

function getPosts(userId, callback) {
    setTimeout(() => {
        callback([{ title: "Post 1" }, { title: "Post 2" }]);
    }, 1000);
}

function getComments(postId, callback) {
    setTimeout(() => {
        callback([{ text: "Great post!" }, { text: "Thanks!" }]);
    }, 1000);
}

// This creates "callback hell" - hard to read and maintain
getUser(1, function(user) {
    getPosts(user.id, function(posts) {
        getComments(posts[0].id, function(comments) {
            console.log("Finally got all data!");
            // Deeply nested callbacks are hard to manage
        });
    });
});
```

### Promises: A Better Way

Promises provide a cleaner way to handle asynchronous operations:

```javascript
// Creating a promise
function fetchWeatherData(city) {
    return new Promise(function(resolve, reject) {
        console.log(`Fetching weather for ${city}...`);
        
        // Simulate API call
        setTimeout(function() {
            if (city === "InvalidCity") {
                reject(new Error("City not found!"));
            } else {
                let weatherData = {
                    city: city,
                    temperature: Math.round(Math.random() * 30 + 10),
                    condition: "Sunny",
                    humidity: Math.round(Math.random() * 50 + 30)
                };
                resolve(weatherData);
            }
        }, 1500);
    });
}

// Using promises with .then() and .catch()
fetchWeatherData("Cairo")
    .then(function(weather) {
        console.log("Weather data received:");
        console.log(`${weather.city}: ${weather.temperature}°C, ${weather.condition}`);
        console.log(`Humidity: ${weather.humidity}%`);
    })
    .catch(function(error) {
        console.error("Error:", error.message);
    });

// Chaining promises
fetchWeatherData("Alexandria")
    .then(function(weather) {
        console.log(`Temperature in ${weather.city}: ${weather.temperature}°C`);
        
        // Return another promise
        return fetchWeatherData("Giza");
    })
    .then(function(weather) {
        console.log(`Temperature in ${weather.city}: ${weather.temperature}°C`);
    })
    .catch(function(error) {
        console.error("Error in chain:", error.message);
    });

// Promise.all - wait for multiple promises
let cities = ["Cairo", "Alexandria", "Giza"];
let weatherPromises = cities.map(city => fetchWeatherData(city));

Promise.all(weatherPromises)
    .then(function(allWeatherData) {
        console.log("All weather data received:");
        allWeatherData.forEach(weather => {
            console.log(`${weather.city}: ${weather.temperature}°C`);
        });
    })
    .catch(function(error) {
        console.error("Error getting all weather data:", error.message);
    });
```

### Async/Await: The Modern Way

Async/await makes asynchronous code look and feel like synchronous code:

```javascript
// Async function declaration
async function getWeatherInfo(city) {
    try {
        console.log(`Getting weather for ${city}...`);
        
        // await waits for the promise to resolve
        let weather = await fetchWeatherData(city);
        
        console.log("Weather information:");
        console.log(`City: ${weather.city}`);
        console.log(`Temperature: ${weather.temperature}°C`);
        console.log(`Condition: ${weather.condition}`);
        
        return weather;
    } catch (error) {
        console.error("Failed to get weather:", error.message);
        throw error; // Re-throw if needed
    }
}

// Using async function
async function weatherReport() {
    try {
        let cairoWeather = await getWeatherInfo("Cairo");
        let alexWeather = await getWeatherInfo("Alexandria");
        
        console.log("Weather Report Complete!");
        console.log(`Cairo: ${cairoWeather.temperature}°C`);
        console.log(`Alexandria: ${alexWeather.temperature}°C`);
        
    } catch (error) {
        console.error("Weather report failed:", error.message);
    }
}

// Run the weather report
weatherReport();

// Parallel async operations
async function getMultipleCitiesWeather() {
    try {
        console.log("Getting weather for multiple cities...");
        
        // Run all API calls in parallel
        let [cairo, alex, giza] = await Promise.all([
            fetchWeatherData("Cairo"),
            fetchWeatherData("Alexandria"),
            fetchWeatherData("Giza")
        ]);
        
        console.log("All weather data:");
        console.log(`Cairo: ${cairo.temperature}°C`);
        console.log(`Alexandria: ${alex.temperature}°C`);
        console.log(`Giza: ${giza.temperature}°C`);
        
    } catch (error) {
        console.error("Error:", error.message);
    }
}

getMultipleCitiesWeather();
```

---

## Working with Real APIs

Let's work with actual web APIs using the Fetch API:

### The Fetch API

```javascript
// Basic fetch example
async function fetchJoke() {
    try {
        console.log("Fetching a random joke...");
        
        // Fetch data from API
        let response = await fetch("https://official-joke-api.appspot.com/random_joke");
        
        // Check if request was successful
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        // Parse JSON response
        let joke = await response.json();
        
        console.log("Here's your joke:");
        console.log(`${joke.setup}`);
        console.log(`${joke.punchline} 😄`);
        
        return joke;
    } catch (error) {
        console.error("Failed to fetch joke:", error.message);
    }
}

// Get multiple jokes
async function getMultipleJokes(count = 3) {
    try {
        console.log(`Fetching ${count} jokes...`);
        
        let jokes = [];
        for (let i = 0; i < count; i++) {
            let response = await fetch("https://official-joke-api.appspot.com/random_joke");
            let joke = await response.json();
            jokes.push(joke);
        }
        
        console.log("Your jokes:");
        jokes.forEach((joke, index) => {
            console.log(`\n${index + 1}. ${joke.setup}`);
            console.log(`   ${joke.punchline} 😄`);
        });
        
        return jokes;
    } catch (error) {
        console.error("Error fetching jokes:", error.message);
    }
}

// Using the functions
fetchJoke();
getMultipleJokes(5);
```

### Working with Different APIs

```javascript
// GitHub User API
async function getGitHubUser(username) {
    try {
        let response = await fetch(`https://api.github.com/users/${username}`);
        
        if (!response.ok) {
            throw new Error("User not found");
        }
        
        let user = await response.json();
        
        console.log("GitHub User Info:");
        console.log(`Name: ${user.name || "Not provided"}`);
        console.log(`Username: ${user.login}`);
        console.log(`Public Repos: ${user.public_repos}`);
        console.log(`Followers: ${user.followers}`);
        console.log(`Bio: ${user.bio || "No bio available"}`);
        
        return user;
    } catch (error) {
        console.error("Error fetching GitHub user:", error.message);
    }
}

// JSONPlaceholder API (for testing)
async function getRandomPost() {
    try {
        let postId = Math.floor(Math.random() * 100) + 1;
        let response = await fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`);
        let post = await response.json();
        
        console.log("Random Post:");
        console.log(`Title: ${post.title}`);
        console.log(`Body: ${post.body}`);
        
        // Get user info for this post
        let userResponse = await fetch(`https://jsonplaceholder.typicode.com/users/${post.userId}`);
        let user = await userResponse.json();
        
        console.log(`Author: ${user.name} (${user.email})`);
        
        return { post, user };
    } catch (error) {
        console.error("Error fetching post:", error.message);
    }
}

// Currency exchange rates API (example)
async function getCurrencyRate(from, to) {
    try {
        // Note: This is a demo URL - replace with actual API key
        let response = await fetch(`https://api.exchangerate-api.com/v4/latest/${from}`);
        let data = await response.json();
        
        let rate = data.rates[to];
        if (rate) {
            console.log(`1 ${from} = ${rate} ${to}`);
            return rate;
        } else {
            throw new Error(`Currency ${to} not found`);
        }
    } catch (error) {
        console.error("Error fetching currency rate:", error.message);
    }
}

// Test the functions
getGitHubUser("octocat");
getRandomPost();
getCurrencyRate("USD", "EUR");
```

---

## Error Handling Best Practices

Proper error handling is crucial for robust applications:

```javascript
// Different types of errors
async function robustAPICall(url) {
    try {
        // Check if URL is provided
        if (!url) {
            throw new Error("URL is required");
        }
        
        console.log(`Fetching data from: ${url}`);
        
        // Set timeout for the request
        let controller = new AbortController();
        let timeoutId = setTimeout(() => controller.abort(), 5000); // 5 second timeout
        
        let response = await fetch(url, {
            signal: controller.signal
        });
        
        clearTimeout(timeoutId);
        
        // Check for HTTP errors
        if (!response.ok) {
            throw new Error(`HTTP ${response.status}: ${response.statusText}`);
        }
        
        // Check content type
        let contentType = response.headers.get("content-type");
        if (!contentType || !contentType.includes("application/json")) {
            throw new Error("Response is not JSON");
        }
        
        let data = await response.json();
        console.log("Data fetched successfully:", data);
        return data;
        
    } catch (error) {
        // Handle different types of errors
        if (error.name === 'AbortError') {
            console.error("Request timed out");
        } else if (error.message.includes('HTTP')) {
            console.error("Server error:", error.message);
        } else if (error.message.includes('JSON')) {
            console.error("Invalid response format:", error.message);
        } else {
            console.error("Unexpected error:", error.message);
        }
        
        // You could also show user-friendly messages here
        throw error; // Re-throw if the caller needs to handle it
    }
}

// Retry mechanism
async function fetchWithRetry(url, maxRetries = 3) {
    for (let attempt = 1; attempt <= maxRetries; attempt++) {
        try {
            console.log(`Attempt ${attempt}/${maxRetries}`);
            let response = await fetch(url);
            
            if (!response.ok) {
                throw new Error(`HTTP ${response.status}`);
            }
            
            let data = await response.json();
            console.log("Success on attempt", attempt);
            return data;
            
        } catch (error) {
            console.log(`Attempt ${attempt} failed:`, error.message);
            
            if (attempt === maxRetries) {
                console.error("All attempts failed");
                throw error;
            }
            
            // Wait before retrying (exponential backoff)
            let delay = Math.pow(2, attempt) * 1000; // 2s, 4s, 8s...
            console.log(`Waiting ${delay}ms before retry...`);
            await new Promise(resolve => setTimeout(resolve, delay));
        }
    }
}
```

---

## Modern JavaScript Features (ES6+)

Let's explore some powerful modern JavaScript features:

### Destructuring

```javascript
// Array destructuring
let colors = ["red", "green", "blue", "yellow"];
let [primary, secondary, tertiary, ...others] = colors;

console.log("Primary:", primary);        // red
console.log("Secondary:", secondary);    // green
console.log("Others:", others);          // [yellow]

// Object destructuring
let user = {
    id: 1,
    name: "John Doe",
    email: "john@example.com",
    address: {
        city: "Cairo",
        country: "Egypt"
    }
};

let { name, email, address: { city } } = user;
console.log(`${name} lives in ${city}`);

// Destructuring in function parameters
function displayUser({ name, email, age = "Unknown" }) {
    console.log(`Name: ${name}`);
    console.log(`Email: ${email}`);
    console.log(`Age: ${age}`);
}

displayUser({
    name: "Sarah",
    email: "sarah@example.com"
});

// API response destructuring
async function getWeatherInfo(city) {
    try {
        let response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}`);
        let { main: { temp, humidity }, weather: [{ description }], name } = await response.json();
        
        console.log(`Weather in ${name}:`);
        console.log(`Temperature: ${temp}°C`);
        console.log(`Humidity: ${humidity}%`);
        console.log(`Description: ${description}`);
        
    } catch (error) {
        console.error("Weather fetch error:", error.message);
    }
}
```

### Spread and Rest Operators

```javascript
// Spread operator (...) - expands arrays/objects
let fruits = ["apple", "banana"];
let vegetables = ["carrot", "lettuce"];
let food = [...fruits, ...vegetables, "rice"];

console.log("All food:", food);

// Copying arrays
let originalArray = [1, 2, 3];
let copiedArray = [...originalArray];
let modifiedArray = [...originalArray, 4, 5];

// Object spread
let basicUser = { name: "John", age: 30 };
let fullUser = { ...basicUser, email: "john@example.com", city: "Cairo" };

console.log("Full user:", fullUser);

// Rest operator - collects multiple elements
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // 15

function logUserInfo(name, age, ...hobbies) {
    console.log(`Name: ${name}, Age: ${age}`);
    console.log("Hobbies:", hobbies.join(", "));
}

logUserInfo("Alice", 25, "reading", "gaming", "coding");
```

### Template Literals and Tagged Templates

```javascript
// Advanced template literals
let user = { name: "Ahmed", score: 95, level: 5 };

let message = `
🎮 Player Stats:
   Name: ${user.name}
   Score: ${user.score.toLocaleString()}
   Level: ${user.level}
   Status: ${user.score > 90 ? "Elite Player! 🏆" : "Keep playing! 💪"}
`;

console.log(message);

// Tagged template literals
function highlight(strings, ...values) {
    return strings.reduce((result, string, i) => {
        let value = values[i] ? `<mark>${values[i]}</mark>` : '';
        return result + string + value;
    }, '');
}

let name = "JavaScript";
let difficulty = "challenging";
let html = highlight`Learning ${name} can be ${difficulty} but rewarding!`;
console.log(html);

// API response formatting
function formatWeather(strings, city, temp, condition) {
    return `
🌤️ Weather Update:
${strings[0]}${city}${strings[1]}${temp}°C${strings[2]}${condition}${strings[3]}
    `.trim();
}

let weatherReport = formatWeather`
Current weather in ${user.city} is ${25} with ${sunny} skies.
Perfect day to go outside! ☀️
`;
```

### Arrow Functions and Advanced Function Features

```javascript
// Arrow function variations
let add = (a, b) => a + b;
let square = x => x * x;
let greet = () => "Hello World!";
let processUser = user => ({
    ...user,
    displayName: `${user.firstName} ${user.lastName}`,
    initials: `${user.firstName[0]}${user.lastName[0]}`
});

// Higher-order functions with arrays
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

let evenNumbers = numbers.filter(num => num % 2 === 0);
let squaredNumbers = numbers.map(num => num ** 2);
let sum = numbers.reduce((total, num) => total + num, 0);

console.log("Even numbers:", evenNumbers);
console.log("Squared numbers:", squaredNumbers);
console.log("Sum:", sum);

// Chaining array methods
let result = numbers
    .filter(num => num > 5)        // [6, 7, 8, 9, 10]
    .map(num => num * 2)           // [12, 14, 16, 18, 20]
    .reduce((sum, num) => sum + num, 0); // 80

console.log("Chained result:", result);

// API data processing
async function processUserData() {
    try {
        let response = await fetch('https://jsonplaceholder.typicode.com/users');
        let users = await response.json();
        
        let processedUsers = users
            .filter(user => user.address.city !== 'undefined')
            .map(user => ({
                id: user.id,
                name: user.name,
                email: user.email,
                city: user.address.city,
                website: user.website
            }))
            .sort((a, b) => a.name.localeCompare(b.name));
        
        console.log("Processed users:", processedUsers);
        return processedUsers;
        
    } catch (error) {
        console.error("Error processing user data:", error.message);
    }
}

processUserData();
```

---

## Mini Project: Weather Dashboard

Let's build a complete weather dashboard combining all our learned concepts:

```javascript
// Weather Dashboard Application
class WeatherDashboard {
    constructor() {
        this.apiKey = "your-api-key-here"; // Get from OpenWeatherMap
        this.baseUrl = "https://api.openweathermap.org/data/2.5";
        this.cities = JSON.parse(localStorage.getItem('weatherCities')) || ['Cairo', 'Alexandria'];
        this.unit = localStorage.getItem('temperatureUnit') || 'metric';
        
        this.init();
    }
    
    async init() {
        console.log("🌤️ Initializing Weather Dashboard...");
        
        // Load saved cities weather
        await this.loadAllCitiesWeather();
        
        // Set up auto-refresh every 10 minutes
        setInterval(() => {
            console.log("🔄 Auto-refreshing weather data...");
            this.loadAllCitiesWeather();
        }, 10 * 60 * 1000);
        
        console.log("✅ Weather Dashboard ready!");
    }
    
    async getCurrentWeather(city) {
        try {
            let url = `${this.baseUrl}/weather?q=${city}&appid=${this.apiKey}&units=${this.unit}`;
            let response = await fetch(url);
            
            if (!response.ok) {
                throw new Error(`City "${city}" not found`);
            }
            
            let data = await response.json();
            
            return {
                city: data.name,
                country: data.sys.country,
                temperature: Math.round(data.main.temp),
                feelsLike: Math.round(data.main.feels_like),
                humidity: data.main.humidity,
                pressure: data.main.pressure,
                description: data.weather[0].description,
                icon: data.weather[0].icon,
                windSpeed: data.wind.speed,
                visibility: data.visibility / 1000, // Convert to km
                timestamp: new Date().toLocaleString()
            };
            
        } catch (error) {
            console.error(`Error fetching weather for ${city}:`, error.message);
            throw error;
        }
    }
    
    async getForecast(city, days = 5) {
        try {
            let url = `${this.baseUrl}/forecast?q=${city}&appid=${this.apiKey}&units=${this.unit}`;
            let response = await fetch(url);
            
            if (!response.ok) {
                throw new Error(`Forecast for "${city}" not available`);
            }
            
            let data = await response.json();
            
            // Process forecast data (API returns data every 3 hours)
            let dailyForecasts = [];
            let currentDate = '';
            
            data.list.forEach(item => {
                let date = new Date(item.dt * 1000).toDateString();
                
                if (date !== currentDate && dailyForecasts.length < days) {
                    dailyForecasts.push({
                        date: date,
                        temperature: Math.round(item.main.temp),
                        description: item.weather[0].description,
                        icon: item.weather[0].icon,
                        humidity: item.main.humidity
                    });
                    currentDate = date;
                }
            });
            
            return dailyForecasts;
            
        } catch (error) {
            console.error(`Error fetching forecast for ${city}:`, error.message);
            throw error;
        }
    }
    
    async addCity(cityName) {
        try {
            // Validate city by fetching its weather
            await this.getCurrentWeather(cityName);
            
            if (!this.cities.includes(cityName)) {
                this.cities.push(cityName);
                this.saveCities();
                console.log(`✅ Added ${cityName} to dashboard`);
                await this.loadAllCitiesWeather();
            } else {
                console.log(`ℹ️ ${cityName} is already in your dashboard`);
            }
            
        } catch (error) {
            console.error(`❌ Cannot add ${cityName}:`, error.message);
            throw error;
        }
    }
    
    removeCity(cityName) {
        let index = this.cities.indexOf(cityName);
        if (index > -1) {
            this.cities.splice(index, 1);
            this.saveCities();
            console.log(`🗑️ Removed ${cityName} from dashboard`);
            this.loadAllCitiesWeather();
        }
    }
    
    async loadAllCitiesWeather() {
        console.log("📡 Loading weather for all cities...");
        
        try {
            let weatherPromises = this.cities.map(city => 
                this.getCurrentWeather(city).catch(error => ({
                    city: city,
                    error: error.message
                }))
            );
            
            let results = await Promise.all(weatherPromises);
            
            console.log("🌤️ Weather Dashboard:");
            console.log("═".repeat(50));
            
            results.forEach(weather => {
                if (weather.error) {
                    console.log(`❌ ${weather.city}: ${weather.error}`);
                } else {
                    this.displayWeather(weather);
                }
            });
            
            console.log("═".repeat(50));
            
        } catch (error) {
            console.error("Error loading weather data:", error.message);
        }
    }
    
    displayWeather(weather) {
        let unitSymbol = this.unit === 'metric' ? '°C' : '°F';
        
        console.log(`
🏙️ ${weather.city}, ${weather.country}
🌡️ ${weather.temperature}${unitSymbol} (feels like ${weather.feelsLike}${unitSymbol})
☁️ ${weather.description}
💧 Humidity: ${weather.humidity}%
🌬️ Wind: ${weather.windSpeed} m/s
👁️ Visibility: ${weather.visibility} km
⏰ Updated: ${weather.timestamp}
        `);
    }
    
    async getDetailedWeatherReport(city) {
        try {
            console.log(`📊 Generating detailed report for ${city}...`);
            
            let [current, forecast] = await Promise.all([
                this.getCurrentWeather(city),
                this.getForecast(city)
            ]);
            
            console.log(`\n📋 Detailed Weather Report for ${city}`);
            console.log("═".repeat(60));
            
            // Current weather
            this.displayWeather(current);
            
            // 5-day forecast
            console.log("📅 5-Day Forecast:");
            forecast.forEach(day => {
                console.log(`${day.date}: ${day.temperature}°C, ${day.description}`);
            });
            
            // Weather insights
            this.generateWeatherInsights(current, forecast);
            
        } catch (error) {
            console.error(`Error generating report for ${city}:`, error.message);
        }
    }
    
    generateWeatherInsights(current, forecast) {
        console.log("\n💡 Weather Insights:");
        
        // Temperature analysis
        let temps = forecast.map(day => day.temperature);
        let avgTemp = temps.reduce((sum, temp) => sum + temp, 0) / temps.length;
        let maxTemp = Math.max(...temps);
        let minTemp = Math.min(...temps);
        
        console.log(`📈 Temperature trend: ${minTemp}°C to ${maxTemp}°C (avg: ${avgTemp.toFixed(1)}°C)`);
        
        // Humidity analysis
        if (current.humidity > 80) {
            console.log("💧 High humidity - might feel sticky");
        } else if (current.humidity < 30) {
            console.log("🏜️ Low humidity - stay hydrated");
        }
        
        // Wind analysis
        if (current.windSpeed > 10) {
            console.log("💨 Windy conditions - hold onto your hat!");
        }
        
        // Clothing recommendations
        if (current.temperature < 15) {
            console.log("🧥 Recommendation: Wear warm clothes");
        } else if (current.temperature > 30) {
            console.log("👕 Recommendation: Light, breathable clothing");
        } else {
            console.log("👔 Recommendation: Comfortable casual wear");
        }
    }
    
    changeUnit(newUnit) {
        if (newUnit === 'metric' || newUnit === 'imperial') {
            this.unit = newUnit;
            localStorage.setItem('temperatureUnit', newUnit);
            console.log(`🌡️ Changed temperature unit to ${newUnit}`);
            this.loadAllCitiesWeather();
        }
    }
    
    saveCities() {
        localStorage.setItem('weatherCities', JSON.stringify(this.cities));
    }
    
    exportData() {
        let data = {
            cities: this.cities,
            unit: this.unit,
            exportDate: new Date().toISOString()
        };
        
        console.log("📤 Weather Dashboard Export:");
        console.log(JSON.stringify(data, null, 2));
        return data;
    }
}

// Usage examples
async function demonstrateWeatherDashboard() {
    console.log("🚀 Starting Weather Dashboard Demo...");
    
    // Create dashboard instance
    let dashboard = new WeatherDashboard();
    
    // Wait for initialization
    await new Promise(resolve => setTimeout(resolve, 2000));
    
    // Add a new city
    try {
        await dashboard.addCity("London");
        await dashboard.addCity("Tokyo");
    } catch (error) {
        console.log("Note: Using demo mode (API key needed for real data)");
    }
    
    // Get detailed report
    await dashboard.getDetailedWeatherReport("Cairo");
    
    // Change units
    dashboard.changeUnit("imperial");
    
    // Export data
    dashboard.exportData();
}

// Run the demo
demonstrateWeatherDashboard();
```

---

## Remember This

> "APIs are the bridges that connect different worlds of data. Master async programming, and you'll be able to build applications that interact with the entire internet!" 🌐

---

## Task (Essential Practice)

Create a **Movie Search App** that includes:

1. **API Integration** with a movie database
2. **Async/await** for handling requests
3. **Error handling** for failed requests
4. **Modern JavaScript** features (destructuring, arrow functions)
5. **Local storage** for favorite movies

```javascript
// Starter code - complete this program
class MovieApp {
    constructor() {
        this.apiKey = "your-omdb-api-key"; // Get from http://www.omdbapi.com/
        this.baseUrl = "https://www.omdbapi.com/";
        this.favorites = JSON.parse(localStorage.getItem('favoriteMovies')) || [];
    }
    
    // TODO: Complete these methods
    async searchMovies(query) {
        // Search for movies using the OMDB API
        // Handle errors appropriately
        // Return array of movie objects
    }
    
    async getMovieDetails(imdbId) {
        // Get detailed information about a specific movie
        // Use destructuring to extract needed properties
        // Return formatted movie object
    }
    
    addToFavorites(movie) {
        // Add movie to favorites array
        // Save to localStorage
        // Avoid duplicates
    }
    
    removeFromFavorites(imdbId) {
        // Remove movie from favorites
        // Update localStorage
    }
    
    displaySearchResults(movies) {
        // Display search results in a user-friendly format
        // Show title, year, poster, and type
    }
    
    displayFavorites() {
        // Show all favorite movies
        // Include option to remove from favorites
    }
    
    getMovieRecommendations() {
        // Based on favorite movies, suggest similar ones
        // Use genre or director information
    }
}

// TODO: Create instance and test the functionality
let movieApp = new MovieApp();

// Example usage:
// await movieApp.searchMovies("Inception");
// await movieApp.getMovieDetails("tt1375666");
// movieApp.displayFavorites();
```

**Requirements:**

- Use async/await for all API calls
- Implement proper error handling with try/catch
- Use destructuring for API response data
- Use arrow functions and modern JavaScript syntax
- Store favorite movies in localStorage
- Handle cases where API returns no results
- Display user-friendly error messages

**Bonus Features:**

- Add movie ratings and reviews functionality
- Implement search filters (year, genre, type)
- Add pagination for search results
- Create a watchlist separate from favorites
