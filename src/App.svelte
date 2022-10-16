<script lang="ts">
  import Form from "./lib/Form.svelte";
  import { app, db, auth } from "./lib/firebase";
  import { onAuthStateChanged, signOut } from "firebase/auth";
  import { authStore, defaultAuth } from "./lib/stores/auth";
  import Button from "./lib/Button.svelte";

  const logout = () => {
    signOut(auth);
  };

  onAuthStateChanged(auth, (user) => {
    if (user) {
      let newStore = {
        user,
        uid: user.uid,
      };
      const uid = user.uid;

      authStore.set(newStore);
      // ...
    } else {
      authStore.set(defaultAuth);
      //signed out
    }
  });
</script>

<main class="flex flex-col  items-center min-h-screen bg-slate-900">
  <h1 class="text-4xl font-medium text-gray-200 mt-5">Students Room</h1>
  <p class="text-gray-200 text-justify p-5">
    Unical Mathematics and Computer Science Students Room
  </p>
  {#if $authStore.user}
  <div class="text-white">
    <p>Welcome {$authStore.user.displayName} </p>
  </div>
    <Button on:click={logout} text="Sign out" />
  {:else}
    <Form />
  {/if}
</main>

<style>
</style>
