<script>
  import { APP_STATUS, appStatus } from "../store.ts";
  import { Alert } from 'flowbite-svelte';
  import StepUpload from './StepUpload.svelte';
  import StepLoading from './StepLoading.svelte';
  import StepChat from './StepChat.svelte';
</script>

{#if $appStatus === APP_STATUS.INIT}
  <StepUpload />
{:else if $appStatus === APP_STATUS.LOADING}
  <StepLoading />
{:else if $appStatus === APP_STATUS.ERROR}
<Alert color="red">
  <span class="font-medium">Algo malo a pasado!</span>
  Hay un error en la aplicación
</Alert>
{:else if $appStatus === APP_STATUS.CHAT_MODE}
  <StepChat />
{:else}
<Alert>
  <span class="font-medium">Accion no reconocida</span>
  Este estado de la aplicacion no esta reconocido
</Alert>
{/if}
