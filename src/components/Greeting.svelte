<!-- This component is a greeting displayed below the clock.
Todo: add a personal name. -->
<script>
  let time = new Date();
  let hours = time.getHours();
  let phrase = "Good ";
  switch (hours) {
    case hours >= 6 && hours <= 12:
      phrase += "morning!";
      break;
    case hours <= 18:
      phrase += "afternoon!";
      break;
    default:
      phrase += "evening!";
      break;
  }
</script>

<div id="container">
  <div id="greeting">
    <p>{phrase}</p>
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
    -moz-text-shadow: 0 0 10px rgba(0, 0, 0, 1);
    -webkit-text-shadow: 0 0 10px rgba(0, 0, 0, 1);
    text-shadow: 0 0 10px rgba(0, 0, 0, 1);
  }
</style>
