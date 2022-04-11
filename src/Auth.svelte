<script>
    import {
        supabase
    } from "./supabaseClient";

    let loading = false;
    let email;

    const handleLogin = async () => {
        try {
            loading = true
            const {
                error
            } = await supabase.auth.signIn({
                email
            })
            if (error) throw error
            alert('Check your email for the login link!')
        } catch (error) {
            alert(error.error_description || error.message)
        } finally {
            loading = false
        }
    };
</script>

<form class="container" on:submit|preventDefault={handleLogin}>
    <div class="form-widget">
        <h1 class="header">NotEK Login</h1>
        <p class="description">Sign in via magic link with your email below</p>
        <div>
            <input class="inputField" type="email" placeholder="Your email" bind:value={email} />
        </div>
        <div>
            <input type="submit" class='button block' value={loading ? "Loading" : "Send magic link" }
                disabled={loading} />
        </div>
    </div>
</form>
<style>
    /* responsive form*/
    form {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
    }

    .form-widget {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
    }

    .header {
        font-size: 2rem;
        font-weight: bold;
        margin-bottom: 1rem;
    }

    .description {
        font-size: 1.2rem;
        margin-bottom: 1rem;
    }

    .inputField {
        width: 100%;
        padding: 0.5rem;
        margin-bottom: 1rem;
        border: 1px solid #ccc;
        border-radius: 4px;
    }

    .button {
        width: 100%;
        padding: 0.5rem;
        margin-bottom: 1rem;
        border: 1px solid #ccc;
        border-radius: 4px;
    }

    /* responsive */
    @media (min-width: 768px) {
        form {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }

        .form-widget {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }

        .header {
            font-size: 2rem;
            font-weight: bold;
            margin-bottom: 1rem;
        }

        .description {
            font-size: 1.2rem;
            margin-bottom: 1rem;
        }

        .inputField {
            width: 100%;
            padding: 0.5rem;
            margin-bottom: 1rem;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        .button {
            width: 100%;
            padding: 0.5rem;
            margin-bottom: 1rem;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
    }
</style>