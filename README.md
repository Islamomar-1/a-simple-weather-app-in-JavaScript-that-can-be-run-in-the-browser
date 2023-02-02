### Hi there 👋

<!--
**Islamomar-1/Islamomar-1** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<html>
  <head>
    <title>Weather App</title>
  </head>
  <body>
    <h1>Weather App</h1>
    <form>
      <label for="city">Enter a city:</label>
      <input type="text" id="city" name="city">
      <button type="button" onclick="getWeather()">Get Weather</button>
    </form>
    <div id="weather-output"></div>

    <script>
      function getWeather() {
        const city = document.querySelector("#city").value;
        const weatherOutput = document.querySelector("#weather-output");
        
        fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=YOUR_API_KEY`)
          .then(response => response.json())
          .then(data => {
            const { main, name } = data;
            const { temp, feels_like, temp_min, temp_max } = main;
            
            weatherOutput.innerHTML = `
              <h2>Weather in ${name}</h2>
              <p>Temperature: ${temp} &#8451;</p>
              <p>Feels Like: ${feels_like} &#8451;</p>
              <p>Min. Temperature: ${temp_min} &#8451;</p>
              <p>Max. Temperature: ${temp_max} &#8451;</p>
            `;
          })
          .catch(error => {
            console.error(error);
            weatherOutput.innerHTML = "<p>An error has occurred. Please try again.</p>";
          });
      }
    </script>
  </body>
</html>
