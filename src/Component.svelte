<script>
  import { getContext } from "svelte"

  const { styleable } = getContext("sdk")
  const component = getContext("component")
  export let discordId = '';
  let isValid;
  let url;
  $: {
    url = `https://discord.com/widget?id=${discordId}&theme=dark`;
    isValid = /[0-9]+/.test(discordId);
  }
</script>

<div use:styleable={$component.styles}>
  {#if isValid}
    <iframe src={url} width="350" height="500" allowTransparency="true" frameBorder="0"
            sandbox="allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts"></iframe>
  {:else}
    <li>Error - Please put down a valid Server ID</li>
  {/if}
</div>