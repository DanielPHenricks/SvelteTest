<script>
  import Time from "./components/Time.svelte";
  let testOne = {
    name: "Rand",
    openHour: 7,
    openMinute: 30,
    closedHour: 22,
    closedMinute: 30,
  };
  let testTwo = {
    name: "EBI",
    openHour: 11,
    openMinute: 0,
    closedHour: 23,
    closedMinute: 59,
  };
</script>

<Time {...testOne} />
<Time {...testTwo} />
