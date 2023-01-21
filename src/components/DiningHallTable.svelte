<script>
    //for each entry in json, create a tr and add the title. check if it is open as well

    //todo: import this
    let dininghalls = [
        {
            name: "The Commons",
            openWeekday: 7,
            closedWeekday: 20,
            openWeekend: 9,
            closedWeekend: 20,
        },
        {
            name: "Rothschild",
            openWeekday: 7,
            closedWeekday: 20,
            openWeekend: 9,
            closedWeekend: 20,
        },
        {
            name: "EBI",
            openWeekday: 7,
            closedWeekday: 20,
            openWeekend: 9,
            closedWeekend: 20,
        },
        {
            name: "Rand",
            openWeekday: 7,
            closedWeekday: 15,
            openWeekend: 0,
            closedWeekend: 0,
        },
    ];

    //end todo

    const date = new Date();
    const isWeekday = date.getDay() > 0 && date.getDay() < 6;
    const hour = date.getHours();
    const isOpen = (hall) => {
        let open = false;
        if (isWeekday) {
            open = hour >= hall.openWeekday && hour < hall.closedWeekday;
        } else {
            open = hour >= hall.openWeekend && hour < hall.closedWeekend;
        }
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
                                /> Food
                            </th>
                            <th scope="col" class="rounded-q4" />
                        </tr>
                    </thead>

                    <tbody>
                        <tr id="link1">
                            <td><img id="open1" src="" /></td>
                            <td>Rand Dining Center</td>
                            <td id="1" />
                        </tr>
                        <tr id="link2">
                            <td><img id="open2" src="" /></td>
                            <td>EBI</td>
                            <td id="2" />
                        </tr>
                        <tr id="link3">
                            <td><img id="open3" src="" /></td>
                            <td>The Commons</td>
                            <td id="3" />
                        </tr>
                        <tr id="link4">
                            <td><img id="open4" src="" /></td>
                            <td>The Pub</td>
                            <td id="4" />
                        </tr>
                    </tbody>
                </table>
            </div>
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
