<script context="module">
import Nav from '../components/Navi.svelte';
import Config from '../../app_config'
var config = Config.get_config()
export let cfg = config;
//console.log(cfg)
</script>

<svelte:head>
	<title>About</title>
</svelte:head>

<Nav />
<div class="container mx-auto px-5 py-4 bg-white">
  <h1>About</h1>
  <p>{cfg.MY_SITE_INFO}</p>
  <p>Date: 2021/06/04</p>
  <hr />
  <h3>Author :</h3>
  <p>
    <a class="" href="https://twitter.com/kuc_arc_f">@kuc_arc_f</a>
  </p>  
</div>
