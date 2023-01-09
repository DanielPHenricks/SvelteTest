<!-- This component is a greeting displayed below the clock.
Todo: style the input and button. -->
<script>

  import { spring } from 'svelte/motion';
  let time = new Date();
  let hours = time.getHours();
  let phrase = "Good ";
  
  switch (hours) {
    case hours >= 6 && hours <= 12:
      phrase += "morning, ";
      break;
    case hours <= 18:
      phrase += "afternoon, ";
      break;
    default:
      phrase += "evening, ";
      break;
  }

  let name = localStorage.getItem("nameOfUser"); //save info for next session
  let show = (name == null);
  let defaultGreeting = "please enter your name.";
  if(name == null){
    phrase += defaultGreeting;
  }
	const isSeen = spring(1);
	$: isSeen.set(show ? 1 : 0);  //like a true or false value, with 0 being falsy
  const updateNameInput = () => {
    isSeen.set(0);
        localStorage.setItem("nameOfUser", document.getElementById("nameInput").value);
        phrase = phrase.substring(0, phrase.indexOf(defaultGreeting));
        phrase += document.getElementById("nameInput").value;
  }
</script>

<div id="container">
  <div id="greeting">
    <p>{phrase}</p>
    <div style="max-height: 4vh">
      <input type="text" id="nameInput" style="opacity: {$isSeen}">
      <button style="opacity: {$isSeen}" on:click={() => {
        updateNameInput();
      }}>Save name</button>
      </div>
  </div>
</div>

<style>
  /* This is the style for the greeting */
  #container {
    background-color: transparent;
    text-align: center;
    position: relative;
    top: 0em;
    text-shadow: 0 2px 3px rgba(0, 0, 0, 0.9);
  }
  #greeting {
    font: 20pt Roboto, Century Gothic;
    color: #fbf9f9;
    text-shadow: 0 0 10px rgba(0, 0, 0, 1);
  }
</style>
