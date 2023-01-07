<script>
  import Clock from "./components/Clock.svelte";
  let numImages = 3;
  let image = Math.ceil(Math.random() * numImages);
  document.body.background = `../images/vandy${image}.jpg`;
</script>

<html lang="en-us">
  <Clock />
</html>
