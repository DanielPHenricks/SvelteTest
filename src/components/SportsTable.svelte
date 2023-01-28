<script>
    import games from "../games.json";
    const time = new Date();
    const date = time.getDate();
    const hour = time.getHours();
</script>

<table id="rounded-corner" summary="Dining">
    <thead>
        <tr>
            <th scope="col" class="rounded-company" />
            <th scope="col" class="rounded-q1">
                <img
                    src="../images/food.png"
                    height="20"
                    width="20"
                    alt="Sports"
                /> Sports
            </th>
            <th scope="col" class="rounded-q4" />
        </tr>
    </thead>

    <tbody id="table">
        <tr>
            <td><b>Date</b></td>
            <td><b>Time</b></td>
            <td><b>Opponent</b></td>
        </tr>
        {#each games as game}
            <tr>
                <td>{game.date}</td>
                <td>{game.time}</td>
                <td
                    >{game.sport}
                    {game.isHomeGame ? "vs" : "at"}
                    {game.opponent}</td
                >
            </tr>
        {/each}
    </tbody>
</table>

<style type="text/css">
    tbody td:first-child {
        width: 60px;
    }
    tbody td:nth-child(2) {
        width: 70px;
    }
    ::-webkit-scrollbar {
        width: 10px;
        height: 3px;
    }
    ::-webkit-scrollbar-button {
        width: 0px;
        height: 0px;
    }
    ::-webkit-scrollbar-thumb {
        background: #ffffff;
        border: 0px none #ffffff;
        border-radius: 0px;
    }
    ::-webkit-scrollbar-thumb:active {
        background: #ffffff;
    }
</style>
