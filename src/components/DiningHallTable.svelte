<script>
    import dininghalls from "../dininghalls.json";
    const date = new Date();
    const day = date.getDay();
    const hour = date.getHours();
    const isOpen = (hall) => {
        let open = false;
        open = hour >= hall.openHour[day] && hour < hall.closedHour[day];
        return open ? `../images/open.png` : `../images/closed.png`;
    };
</script>

<!-- This component is for the table containing upcoming schedules. -->
<div class="supporting">
    <div class="container">
        <div class="row">
            <div class="col-sm-3">
                <table id="rounded-corner" summary="Dining">
                    <thead>
                        <tr>
                            <th scope="col" class="rounded-company" />
                            <th scope="col" class="rounded-q1">
                                <img
                                    src="../images/food.png"
                                    height="20"
                                    width="20"
                                    alt="Food"
                                /> Food
                            </th>
                            <th scope="col" class="rounded-q4" />
                        </tr>
                    </thead>

                    <tbody id="table">
                        {#each dininghalls as hall}
                            <tr>
                                <td
                                    ><img
                                        id="open1"
                                        src={isOpen(hall)}
                                        alt="img"
                                    /></td
                                >
                                <td>{hall.name}</td>
                                <td />
                            </tr>
                        {/each}
                    </tbody>
                </table>
            </div>
            <div class="col-sm-3" />
            <div class="col-sm-3" />
        </div>
    </div>
</div>

<style type="text/css">
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
    .container {
        max-width: 56em;
        justify-content: center;
    }
    .supporting {
        text-shadow: 0 2px 3px rgba(0, 0, 0, 0.4);
    }
    .supporting .col-xs-2 {
        top: 0px;
        text-align: center;
        color: #fff;
        margin-bottom: 1em;
    }
</style>
