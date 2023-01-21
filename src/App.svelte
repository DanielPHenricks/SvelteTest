<!-- This is the main page for the Vandy Tab. -->
<script>
  import Clock from "./components/Clock.svelte";
  import ButtonGroup from "./components/ButtonGroup.svelte";
  import Greeting from "./components/Greeting.svelte";
  import DiningHallTable from "./components/DiningHallTable.svelte";
  const numImages = 3;
  let image = Math.ceil(Math.random() * numImages);
  document.body.background = `../images/vandy${image}.jpg`;
</script>

<html lang="en-us">
  <Clock />
  <Greeting />
  <ButtonGroup />
  <DiningHallTable />
</html>
