<script>
    import { get_root_for_style } from "svelte/internal";
    import {goto} from "@sapper/app.mjs";

    let email = '', password = ''

    const submit = async() => {
        await fetch('http://localhost:8000/api/login', {
            method: 'POST',
            headers: {'Content-Type': 'application/json'},
            credentials: "include",
            body: JSON.stringify({
                email,
                password
            })
        });

        await goto('/');
    }
</script>

<form on:submit|preventDefault={submit}>
    <h1 class="h3 mb-3 fw-normal">Please sign in</h1>
  
    <input bind:value={email} type="email" class="form-control" placeholder="name@example.com">

    <input bind:value={password} type="password" class="form-control" placeholder="Password">

    <button class="btn btn-primary w-100 py-2" type="submit">Sign in</button>
</form>