<script>
    export let name;
    export let isOpen;
    const date = new Date();
    const isWeekday = date.getDay() > 0 && date.getDay() < 6;
    const hour = date.getHours();
    $: link = isOpen ? `../images/open.png` : `../images/closed.png`;
    let data;

    async function fetchData() {
        const response = await fetch("../dininghalls.json");
        data = await response.json();
        data.forEach((e) => {
            let curr = e.name;
            if (name == curr) {
                if (isWeekday) {
                    isOpen = hour >= e.openWeekday && hour < e.closedWeekday;
                } else {
                    isOpen = hour >= e.openWeekend && hour < e.closedWeekend;
                }
            }
        });
    }

    fetchData();
</script>

<td><img id="open1" src={link} alt="img" /></td>
<td>{name}</td>
<td />
