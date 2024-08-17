<script lang="ts">
  import { AppBar, LightSwitch, ListBox, ListBoxItem, popup, type PopupSettings } from '@skeletonlabs/skeleton';
  import { writable } from 'svelte/store';
  import { goto } from '$app/navigation';

  // Mock login state (replace with your actual auth logic)
  const isLoggedIn = writable(false);

  // Popup settings for the avatar menu
  const avatarPopup: PopupSettings = {
    event: 'click',
    target: 'avatarMenu',
    placement: 'bottom-end',
    closeOnOutsideClick: true,
    middleware: {
      offset: 5, // Add some offset to position it just below the avatar
    }
  };

  // Function to handle logout
  function handleLogout() {
    isLoggedIn.set(false);
  }
</script>

<AppBar class="sticky top-0 z-10  h-[8vh]">
  <svelte:fragment slot="lead">
    <a href="/" class="btn btn-sm variant-ghost-surface">
      <span class="text-xl font-bold">Logo</span>
    </a>
  </svelte:fragment>
  <svelte:fragment slot="trail">
    <div class="flex items-center space-x-4">
      <LightSwitch />
      <div class="w-24 relative"> <!-- Added relative positioning -->
        {#if $isLoggedIn}
          <button class="btn-icon btn-sm variant-ghost-surface" use:popup={avatarPopup}>
            <!-- Replace with your avatar component or image -->
            <div class="avatar placeholder">
              <div class="bg-neutral-focus text-neutral-content rounded-full w-8">
                <span class="text-xs">UN</span>
              </div>
            </div>
          </button>
          <div class="card w-48 shadow-xl py-2 variant-filled" data-popup="avatarMenu">
            <ListBox rounded="rounded-none">
              <ListBoxItem on:click={() => {goto("/profile")}}>Profile</ListBoxItem>
              <ListBoxItem on:click={() => {}}>Account</ListBoxItem>
              <ListBoxItem on:click={handleLogout}>Log out</ListBoxItem>
            </ListBox>
          </div>
        {:else}
          <button class="btn btn-sm variant-filled" on:click={() => isLoggedIn.set(true)}>
            Sign In
          </button>
        {/if}
      </div>
    </div>
  </svelte:fragment>
</AppBar>

<style>
  /* Add any custom styles here */
</style>
