### Hi there š

<!--
**Islamomar-1/Islamomar-1** is a āØ _special_ āØ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- š­ Iām currently working on ...
- š± Iām currently learning ...
- šÆ Iām looking to collaborate on ...
- š¤ Iām looking for help with ...
- š¬ Ask me about ...
- š« How to reach me: ...
- š Pronouns: ...
- ā” Fun fact: ...
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
