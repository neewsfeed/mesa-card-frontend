<script>
// @ts-nocheck
    const cookies = document.cookie.split('/').reduce((res, c) => {
        const [key, val] = c.trim().split('=').map(decodeURIComponent)
        try {
            return Object.assign(res, { [key]: JSON.parse(val) })
        } catch (e) {
            return Object.assign(res, { [key]: val })
        }
    }, {});

    const accounts = {
        'admin@admin.com': 'admin',
    }

    if (!cookies['loggedIn']) {
        window.location.href = '/';
    }

    const redirIssueCard = () => {
        window.location.href = '/admin-panel/issuecard/';
    }

    const redirChangeValueCard = () => {
        window.location.href = '/admin-panel/value/set'
    }

    const redirGetValue = () => {
        window.location.href = '/admin-panel/value/get';
    }
</script>

<main>
    <script type="module" src="https://unpkg.com/ionicons@5.5.2/dist/ionicons/ionicons.esm.js"></script>
    <script nomodule src="https://unpkg.com/ionicons@5.5.2/dist/ionicons/ionicons.js"></script><link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/5.0.0/normalize.min.css">
    <link rel='stylesheet' href='https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&amp;display=swap'><link rel="stylesheet" href="./style.css">
    {#if cookies['loggedIn'] && accounts[cookies['email']] == cookies['password']}
    <div>
        <h1>Welcome to the Admin Control Panel</h1>
        <p>Logged in as: {cookies['email']}</p>
        <button on:click={redirIssueCard}>Issue a new card</button>
        <button on:click={redirChangeValueCard}>Change the value of a card</button>
        <button on:click={redirGetValue}>Get the value of a card</button>
    </div>
    {/if}
</main>