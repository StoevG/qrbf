<template>
  <div id="app" class="container">
    <header>
      <img src="./assets/bfLogo.jpg" class="logo" />
    </header> 
    <div class="content">
      <div class="button-container">
        <button @click="showJoke">Joke</button>
        <button @click="showQuote">Quote</button>
        <button @click="showCoffeeFortune">Coffee Fortune</button>
      </div>
      <div id="output" v-html="output"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      output: '',
      jokes: [
        { setup: "Why don't scientists trust atoms?", punchline: "Because they make up everything!" },
        { setup: "Why did the scarecrow win an award?", punchline: "Because he was outstanding in his field!" },
        { setup: "Why don't some couples go to the gym?", punchline: "Because some relationships don't work out." }
      ],
      quotes: [
        { quote: "A pencil and rubber are of more use to thought than a battalion of assistants. To happiness the same applies as to truth: one does not have it, but is in it.", author: "Theodor Adorno" },
        { quote: "Happiness is not something ready-made. It comes from your own actions.", author: "Dalai Lama" },
        { quote: "The purpose of our lives is to be happy.", author: "Dalai Lama" }
      ],
      coffeeFortunes: [
        "Today, a great idea will come to you after your morning coffee.",
        "You will find joy in a new coffee blend this week.",
        "A warm cup of coffee will bring you comfort today.",
        "An unexpected surprise awaits you during your coffee break.",
        "Your perseverance will be rewarded, especially after a good cup of coffee.",
        // Add more coffee fortunes for each day of the year
        // ...
        // Make sure to have 365 fortunes in total
      ]
    };
  },
  methods: {
    showJoke() {
      const randomJoke = this.jokes[Math.floor(Math.random() * this.jokes.length)];
      this.output = `${randomJoke.setup} - ${randomJoke.punchline}`;
    },
    showQuote() {
      const randomQuote = this.quotes[Math.floor(Math.random() * this.quotes.length)];
      this.output = `<blockquote>"${randomQuote.quote}"</blockquote><footer>- ${randomQuote.author}</footer>`;
    },
    showCoffeeFortune() {
      const randomCoffeeFortune = this.coffeeFortunes[Math.floor(Math.random() * this.coffeeFortunes.length)];
      this.output = `<blockquote>"${randomCoffeeFortune}"</blockquote>`;
    }
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #f0f4f8; /* Light blue-gray background */
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  display: flex;
  flex-direction: column;
  justify-content: center; /* Center content vertically */
  align-items: center; /* Center content horizontally */
  text-align: center;
  background: white;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 20px;
  max-width: 600px;
  width: 100%;
  box-sizing: border-box; /* Include padding and border in element's total width and height */
}

header {
  margin-bottom: 20px;
}

.logo {
  width: 150px; /* Adjust as needed */
  height: auto;
}

.content {
  display: flex;
  flex-direction: column;
  justify-content: center; /* Center content vertically */
  align-items: center; /* Center content horizontally */
  width: 100%;
}

.button-container {
  display: flex;
  flex-wrap: wrap; /* Allows buttons to wrap on smaller screens */
  justify-content: center; /* Center buttons horizontally */
  gap: 10px; /* Space between buttons */
  margin-bottom: 20px;
}

button {
  background-color: #2b6aff; /* Blue background */
  border: none;
  color: white;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
  flex: 1 1 auto; /* Buttons take up equal space and wrap */
  max-width: 200px; /* Limit button width */
}

button:hover {
  background-color: #080731; /* Darker blue on hover */
}

#output {
  margin-top: 20px;
  font-size: 18px;
  overflow: auto; /* Allow scrolling if the content is too large */
  text-align: center;
  width: 100%; /* Ensure output takes full width of the container */
  display: flex;
  justify-content: center; /* Center content horizontally */
  align-items: center; /* Center content vertically */
}

#output img {
  max-width: 100%; /* Ensure the image does not exceed the width of its container */
  height: auto; /* Maintain aspect ratio */
  display: block; /* Remove inline spacing */
  margin: 0 auto; /* Center the image horizontally */
}

#output blockquote {
  font-style: italic;
  margin: 10px auto; /* Center the blockquote horizontally */
  padding: 10px;
  border-left: 4px solid #007bff; /* Blue border on the left */
  background: #f9f9f9; /* Light background for the blockquote */
  max-width: 100%; /* Ensure blockquote does not exceed container width */
}

#output footer {
  font-weight: bold;
  margin-top: 5px;
}

@media (max-width: 600px) {
  .container {
    padding: 10px;
  }

  .logo {
    width: 220px; /* Adjust logo size for smaller screens */
  }

  button {
    font-size: 14px; /* Smaller font size for buttons */
    padding: 8px 16px; /* Smaller padding for buttons */
  }
}
</style>
