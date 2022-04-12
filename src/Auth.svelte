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

<form on:submit|preventDefault={handleLogin}>
    <div class="form-group">
        <p class="description">Sign in via magic link with your email below</p>
        <div class="form-group">
            <div class="has-icon-right">
                <label for="input-email">Email</label>
                <input class="form-input" id="input-email" type="email" placeholder="Your email" bind:value={email} />
                        {#if loading}
                            <i class="form-icon loading"></i>
                        {/if}
                    </div>
                </div>
            <div>
            <button type="submit" disabled={loading} class="btn btn-primary">
                Send magic link    
            </button>
        </div>
    </div>
</form>
 