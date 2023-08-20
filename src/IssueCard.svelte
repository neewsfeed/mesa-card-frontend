<script>
    var suffix, delimiter, delimiter2, currency, amount, cardHolderName, cardIssuer, alias;

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

    // config
    var backendHost = 'http://localhost:3000'

    const submit = () => {
        if (!cookies['loggedIn']) {
            window.location.href = '/';
        } else if (!accounts[cookies['email']] != cookies['password']) {
            window.location.href = '/';
        }

        if (delimiter == '.') {
            delimiter = 'setThisAsDot'
        }
        console.log(`redirecting to ${backendHost}/create-card/${suffix}/${delimiter}/${delimiter2}/${currency}/${amount}/${cardHolderName}/${cardIssuer}/${alias}`)
        window.location.href = `${backendHost}/create-card/${suffix}/${delimiter}/${delimiter2}/${currency}/${amount}/${cardHolderName}/${cardIssuer}/${alias}` 
    }
</script>

<main>
    <script type="module" src="https://unpkg.com/ionicons@5.5.2/dist/ionicons/ionicons.esm.js"></script>
    <script nomodule src="https://unpkg.com/ionicons@5.5.2/dist/ionicons/ionicons.js"></script><link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/5.0.0/normalize.min.css">
    <link rel='stylesheet' href='https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&amp;display=swap'><link rel="stylesheet" href="./style.css">
        <div class='form__group field'>
            <label for="suffix">Suffix</label><br>
            <input bind:value={suffix} class="form__field" type="text" id="suffix" name="suffix" placeholder="Suffix" required><br>
    
            <label for="delimiter">Delimiter</label><br>
            <input bind:value={delimiter} class="form__field" type="text" id="delimiter" name="delimiter" placeholder="Delimiter" required><br>
    
            <label for="delimiter2">Delimiter 2</label><br>
            <input bind:value={delimiter2} class="form__field" type="text" id="delimiter2" name="delimiter2" placeholder="Delimiter 2" required><br>
    
            <label for="currency">Currency</label><br>
            <input bind:value={currency} class="form__field" type="text" id="currency" name="currency" placeholder="Currency" required><br>
    
            <label for="amount">Amount</label><br>
            <input bind:value={amount} class="form__field" type="text" id="amount" name="amount" placeholder="Amount" required><br>
    
            <label for="cardHolderName">Card Holder Name</label><br>
            <input bind:value={cardHolderName} class="form__field" type="text" id="cardHolderName" name="cardHolderName" placeholder="Card Holder Name" required><br>
    
            <label for="cardIssuer">Card Issuer</label><br>
            <input bind:value={cardIssuer} class="form__field" type="text" id="cardIssuer" name="cardIssuer" placeholder="Card Issuer" required><br>
    
            <label for="alias">Alias</label><br>
            <input bind:value={alias} class="form__field" type="text" id="alias" name="alias" placeholder="Alias" required><br>
    
            <br><button on:click={submit}>Submit</button>
    </div>
</main>
<style>
    .form__group {
        position: relative;
        padding: 15px 0 0;
        margin-top: 10px;
        width: 50%;
    }

    .form__field {
        width: 100%;
        border: 0;
        border-bottom: 2px solid #9b9b9b;
        outline: 0;
        font-size: 1.3rem;
        color: #191919;
        padding: 7px 0;
        background: transparent;
    }
    .form__field::placeholder {
        color: transparent;
    }
    .form__field:placeholder-shown ~ .form__label {
        font-size: 1.3rem;
        cursor: text;
        top: 20px;
    }

    .form__label {
        position: absolute;
        top: 0;
        display: block;
        font-size: 1rem;
        color: #9b9b9b;
    }

    .form__field:focus {
        padding-bottom: 6px;
        /* font-weight: 700; */
        border-width: 3px;
        border-image-slice: 1;
    }

    .form__field:required, .form__field:invalid {
        box-shadow: none;
    }
</style>