<script>
  import { onMount } from "svelte";
  export let name;
  export let openHour;
  export let closedHour;
  export let openMinute;
  export let closedMinute;
  let time = new Date();
  $: hour = time.getHours();
  $: minutes = time.getMinutes();
  $: seconds = time.getSeconds();

  onMount(() => {
    const interval = setInterval(() => {
      time = new Date();
    }, 1000);

    return () => {
      clearInterval(interval);
    };
  });
  const checkTime = () => {
    return (
      (hour > openHour || (hour == openHour && minutes >= openMinute)) &&
      (hour < closedHour || (hour == closedHour && minutes <= closedMinute))
    );
  };
  const padTime = (hour, min) => {
    let isAM = hour <= 11;
    if (hour == 0) {
      hour = 12;
    }
    return `${hour != 12 ? hour % 12 : hour}:${min < 10 ? "0" + min : min} ${
      isAM ? "AM" : "PM"
    }`;
  };
</script>

<p>
  The {name} dining hall opens at {padTime(openHour, openMinute)}
  and closes at {padTime(closedHour, closedMinute)}. The current time is
  {padTime(hour, minutes)}.
  {name} is {checkTime() ? "open" : "closed"}.
</p>

<style>
</style>
