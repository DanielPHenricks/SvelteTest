<!-- This component is a greeting displayed below the clock.
Todo: style the input and button. -->
<script>

  import { spring } from 'svelte/motion';
  let time = new Date();
  let hours = time.getHours();
  let name = localStorage.getItem("name"); //save info for next session
  let show = (name == null);
  let defaultGreeting = "Please enter your name.";
  let phrase = "Good ";
  if(name == null){
    phrase = defaultGreeting;
  }
  else {
    if(hours >= 6 && hours <= 12){
      phrase += "morning, ";
    }
    else if(hours <= 18){
      phrase += "afternoon, ";
    }
    else {
      phrase += "evening";
    }
    phrase += name;
  }
	const isSeen = spring(0);
	$: isSeen.set(show ? 1 : 0);  //like a true or false value, with 0 being falsy
  const updateNameInput = () => {
    isSeen.set(0);
    localStorage.setItem("name", document.getElementById("nameInput").value);
    phrase = "Name has been saved.";
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
