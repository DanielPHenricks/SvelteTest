<script>
  export let name;
  export let openHour;
  export let closedHour;
  export let openMinute;
  export let closedMinute;
  let d = new Date();
  d = new Date();
  let hour = d.getHours();
  let minutes = d.getMinutes();
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
